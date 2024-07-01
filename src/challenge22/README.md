# Run Length Encoding

Run-length encoding (RLE) is a basic form of lossless data compression.
It works by replacing repeated sequences of data with a single data value and the number of times it repeats.
Your function only has to handle alphabetic characters; however, you should have two functions that can convert to and from the RLE form.

See below: 
```
// `AAAABBBCCDAA` => `4A3B2C1D2A`
// `4A3B2C1D2A` => `AAAABBBCCDAA`
// `A` => `1A`
// `1A` => `A`
// `AA` => `2A`
// `2A` => `AA`
```