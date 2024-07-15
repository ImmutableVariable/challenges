# Answer

## JavaScript

```javascript
const fs = require('fs');
const zlib = require('zlib');

// Based on the PNG file format specification: https://www.w3.org/TR/PNG/
class PNG {
    buffer = null;
    width = 0;
    height = 0;
    bitDepth = 0;
    colorType = 0;
    compressionMethod = 0;
    filterMethod = 0;
    interlaceMethod = 0;

    chunks = [];
    data = [];

    constructor(imageBuffer) {
        if (!imageBuffer || imageBuffer.length < 8) {
            throw new Error('Invalid PNG file');
        }

        this.buffer = imageBuffer;
        this.parse();
    }

    parseIHDR() {
        const ihdr = this.chunks.find(chunk => chunk.type === 'IHDR');
        if (!ihdr) {
            throw new Error('IHDR chunk not found, This is not a valid PNG file');
        }

        this.width = ihdr.data.readUInt32BE(0);
        this.height = ihdr.data.readUInt32BE(4);
        this.bitDepth = ihdr.data.readUInt8(8);
        this.colorType = ihdr.data.readUInt8(9);
        this.compressionMethod = ihdr.data.readUInt8(10);
        this.filterMethod = ihdr.data.readUInt8(11);
        this.interlaceMethod = ihdr.data.readUInt8(12);
    }

    parseHeader() {
        const header = this.buffer.slice(0, 8);

        if (header.toString('hex') !== '89504e470d0a1a0a') {
            throw new Error('Invalid PNG signature');
        }
    }

    chunker() {
        let i = 8; // Skip the header
        while (i < this.buffer.length) {
            const length = this.buffer.readUInt32BE(i);
            const type = this.buffer.slice(i + 4, i + 8).toString('ascii');
            const data = this.buffer.slice(i + 8, i + 8 + length);
            const crc = this.buffer.readUInt32BE(i + 8 + length);
            this.chunks.push({ length, type, data, crc });
            i += 12 + length;
        }
    }

    // Start to parse the image data chuck!
    parseIDAT() {
        // As image data can be split into multiple IDAT chunks
        // we need to concatenate them all
        const idatChunks = this.chunks.filter(chunk => chunk.type === 'IDAT');
        const idatData = Buffer.concat(idatChunks.map(chunk => chunk.data));

        if (!idatData) {
            throw new Error('IDAT chunk not found, This is not a valid PNG file');
        }

        if (this.colorType !== 6) {
            throw new Error('Only RGBA color type is supported currently.');
        }

        const decompressedData = zlib.inflateSync(idatData);

        const data = [];
        let i = 0;
        for (let y = 0; y < this.height; y++) {
            const filterType = decompressedData.readUInt8(i);
            i++;
            for (let x = 0; x < this.width; x++) {
                let red = decompressedData.readUInt8(i);
                let green = decompressedData.readUInt8(i + 1);
                let blue = decompressedData.readUInt8(i + 2);
                let alpha = decompressedData.readUInt8(i + 3);

                if (x !== 0 || y !== 0) {
                    let left = x !== 0 ? data[data.length - 1] : { red: 0, green: 0, blue: 0, alpha: 0 };
                    let above = y !== 0 ? data[data.length - this.width] : { red: 0, green: 0, blue: 0, alpha: 0 };
                    let aboveLeft = x !== 0 && y !== 0 ? data[data.length - this.width - 1] : { red: 0, green: 0, blue: 0, alpha: 0 };

                    if (filterType === 4) {
                        console.log(filterType);
                    }
                    switch (filterType) {
                        case 0: // None
                            break;
                        case 1: // Sub
                            red += left.red;
                            green += left.green;
                            blue += left.blue;
                            alpha += left.alpha;
                            break;
                        case 2: // Up
                            red += above.red;
                            green += above.green;
                            blue += above.blue;
                            alpha += above.alpha;
                            break;
                        case 3: // Average
                            red += Math.floor((left.red + above.red) / 2);
                            green += Math.floor((left.green + above.green) / 2);
                            blue += Math.floor((left.blue + above.blue) / 2);
                            alpha += Math.floor((left.alpha + above.alpha) / 2);
                            break;
                        case 4: // Paeth
                            red += this.paethPredictor(left.red, above.red, aboveLeft.red);
                            green += this.paethPredictor(left.green, above.green, aboveLeft.green);
                            blue += this.paethPredictor(left.blue, above.blue, aboveLeft.blue);
                            alpha += this.paethPredictor(left.alpha, above.alpha, aboveLeft.alpha);
                            break;
                    }
                }

                data.push({ red: red & 0xFF, green: green & 0xFF, blue: blue & 0xFF, alpha: alpha & 0xFF });
                i += 4;
            }
        }

        this.data = data;
    }

    paethPredictor(a, b, c) {
        const p = a + b - c;
        const pa = Math.abs(p - a);
        const pb = Math.abs(p - b);
        const pc = Math.abs(p - c);

        if (pa <= pb && pa <= pc) return a;
        else if (pb <= pc) return b;
        else return c;
    }

    parse() {
        this.parseHeader();
        this.chunker();
        this.parseIHDR();
        console.log(this.width, this.height, this.bitDepth, this.colorType, this.compressionMethod, this.filterMethod, this.interlaceMethod);

        if (this.interlaceMethod !== 0) {
            throw new Error('Interlaced images are not yet supported');
        }

        this.parseIDAT();

        return this.data;
    }

    // given a width and height, resize the image using nearest neighbor interpolation
    resize(width, height) {
        let resizedData = [];
        let xRatio = this.width / width;
        let yRatio = this.height / height;

        for (let y = 0; y < height; y++) {
            for (let x = 0; x < width; x++) {
                let pixel = this.data[Math.floor(y * yRatio) * this.width + Math.floor(x * xRatio)];
                resizedData.push(pixel);
            }
        }

        this.width = width;
        this.height = height;
        this.data = resizedData;
    }
}

function createSizedPNGType(imagePath, maxWidth = 30, maxHeight = 20) {
    const imageBuffer = fs.readFileSync(imagePath);
    const png = new PNG(imageBuffer);

    if (png.height > maxHeight) {
        const ratio = maxHeight / png.height;
        png.resize(Math.floor(png.width * ratio), maxHeight);
    }

    if (png.width > maxWidth) {
        const ratio = maxWidth / png.width;
        png.resize(maxWidth, Math.floor(png.height * ratio));
    }

    return png;
}

function printPNGImagePathAsAscii(imagePath) {
    const png = createSizedPNGType(imagePath);
    const { data, width, height } = png;
    const chars = ['.', '+', '*', '#', '@'];
    
    let ascii = '';
    for (let y = 0; y < height; y++) {
        for (let x = 0; x < width; x++) {
            const pixel = data[y * width + x];

            // represent it as a range from 0 to chars.length
            // i got this formula from https://stackoverflow.com/questions/596216/formula-to-determine-brightness-of-rgb-color
            const luminance = ((0.299 * pixel.red + 0.587 * pixel.green + 0.114 * pixel.blue) / 255) * chars.length; 
    

            if (pixel.alpha === 0) {
                ascii += ' ';
            } else {
                ascii += chars[Math.floor(luminance)];
            }
        }
        ascii += '\n';
    }
    console.log(ascii);
}

#printPNGImagePathAsAscii('image.png');
```