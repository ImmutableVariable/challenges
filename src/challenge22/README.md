# Run Length Encoding

Run-length encoding (RLE) is a basic form of lossless data compression.
It works by replacing repeated sequences of data with a single data value and the number of times it repeats.
Your function only has to handle alphabetic characters; however, you should have two functions that can convert to and from the RLE form.

## Examples

```
Encoding:
AAAABBBCCDAA => 4A3B2C1D2A
A => 1A
AA => 2A

Decoding: 
4A3B2C1D2A => AAAABBBCCDAA
1A => A
2A => AA
```