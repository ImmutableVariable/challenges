# Brainfuck Interpreter

Brainfuck is a esoteric programming language created by Urban Müller which consists of 8 basic commands.

## Commands/Characters

| **Character**         | **Meaning**                                              |
|------------------|--------------------------------------------------------------|
| **>** | Increment Data Pointer                |
| **<** | Decrement Data Pointer                |
| **+** | Increment the byte at the pointer by 1                |
| **-** | Decrement the byte at the pointer by 1                |
| **.** | Output byte at the pointer                |
| **,** | Accept byte at the pointer as input                |
| **[** | If datapointer byte is zero, jump it forward the command after matching ]                |
| **]** | If datapointer byte is nonzero, jump it back to the command after matching [                |


## Notes 

- It is recommended to convert outputted bytes to ASCII, but is not required.
- You should handle cell wrapping, i.e handling cells that have values of below 0 or above 255

## Resources

- [Wikipedia](https://en.wikipedia.org/wiki/Brainfuck)