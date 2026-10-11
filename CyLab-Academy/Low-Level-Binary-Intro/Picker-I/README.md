# Picker I — CyLab Academy

## Category
Low Level Binary Intro — Python Security

## Objective
Investigate whether the service can call a function other than its default random-number function.

## Methodology
1. Connected to the challenge instance using Netcat.
2. Tested the provided `getRandomNumber` function.
3. Examined the challenge hint about selecting a useful function.
4. Tested the `win` function.
5. Decoded the hexadecimal output into readable text.

## Tools
- Kali Linux
- Netcat (`nc`)
- Python 3

## Key Learning
- Python functions can be selected or called by a program.
- Unsafe function selection can expose unintended functionality.
- Hexadecimal bytes can be decoded into text.

## Result
Challenge completed.

## Security Lesson
Programs should validate user input and restrict function selection to explicitly permitted operations.
