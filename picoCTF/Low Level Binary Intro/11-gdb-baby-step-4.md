# GDB Baby Step 4

## Challenge Information
- **Platform:** CyLab Security Academy
- **Learning Path:** Low Level Binary Intro
- **Category:** Reverse Engineering
- **Difficulty:** Medium
- **Architecture:** x86_64

## Objective
Identify the constant used by `func1` to multiply the value in the `EAX` register. Convert the hexadecimal constant to decimal and construct the flag.

## Tools Used
- Kali Linux
- GDB (GNU Debugger)

## Solution

### Step 1: Disassemble the function

Run GDB:

```bash
gdb /home/kali/debugger0_d
```

Inspect the function:

```gdb
disassemble func1
```

Relevant instruction:

```asm
imul $0x3269,%eax,%eax
```

### Step 2: Identify the constant

The instruction uses `0x3269` as the multiplication constant.

Convert hexadecimal to decimal:

```bash
printf "%d\n" $((0x3269))
```

Output:

```text
12905
```

### Step 3: Construct the flag

The challenge asks for the constant in decimal, not the final value in the `EAX` register.

## Flag

```text
academy{12905}
```

## Key Learning
- `disassemble` displays a function's assembly instructions.
- `imul` performs signed integer multiplication.
- Hexadecimal constants can be converted to decimal using Bash arithmetic.
- Read the challenge objective carefully: the requested constant may differ from the function's return value.
