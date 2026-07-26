# Wave a flag - picoCTF

## Category: General Skills
## Difficulty: Easy

## Description
Program has a "help" flag that reveals hidden information.

## Approach

1. Downloaded the binary using wget in the webshell:
   $ wget <challenge_url>

2. Made the file executable:
   $ chmod +x warm

3. Tried running the help flags:
   $ ./warm --help
   (or)
   $ ./warm -h

4. The help output revealed the flag directly.

## Learning
Many CLI tools/binaries expose hidden info or debug data 
through --help or -h flags. Always check help/usage output 
first when analyzing an unknown binary - it's a quick 
low-effort recon step before deeper analysis (strings, 
disassembly, etc.)

## Flag
[Solved ✅ - try it yourself! Run --help on the binary]
