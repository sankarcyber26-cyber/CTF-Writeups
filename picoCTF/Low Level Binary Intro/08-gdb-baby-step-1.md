# CyLab Academy — GDB Baby Step 1

## Challenge Information

- **Platform:** CyLab Security Academy
- **Learning Path:** Low Level Binary Intro
- **Challenge Name:** GDB Baby Step 1
- **Category:** Reverse Engineering
- **Difficulty:** Medium
- **Architecture:** x86_64
- **Tools Used:** Kali Linux, GDB, Python 3

## Objective

Determine the value stored in the `EAX` register at the end of the `main` function by disassembling the binary using GDB. Convert the hexadecimal value to decimal and submit the flag in the required format.

## Methodology

### Step 1: Download the Challenge Binary

Downloaded the challenge binary provided by CyLab Academy.

```bash
wget "https://challenge-files.cylabacademy.net/library/03b038548e2a34973bde05a78fadc1f09467a1d03ffbfb9e4b48bd44e87c0e70/debugger0_a"
```

### Step 2: Open the Binary in GDB

Started GDB with the downloaded binary.

```bash
gdb ./debugger0_a
```

### Step 3: Disassemble the Main Function

Used the `disassemble main` command to inspect the assembly instructions executed by the `main` function.

```gdb
disassemble main
```

The relevant instruction was:

```asm
mov $0x86342, %eax
```

### Step 4: Analyze the Instruction

The `mov` instruction copies the immediate hexadecimal value `0x86342` into the `EAX` register.

The following instructions restore the base pointer and return from the function without modifying `EAX`.

Therefore, the final value returned in `EAX` is `0x86342`.

### Step 5: Convert Hexadecimal to Decimal

Converted the hexadecimal value to decimal using Python 3.

```bash
python3 -c 'print(int("0x86342", 16))'
```

Output:

```text
549698
```

### Step 6: Construct the Flag

Placed the decimal value inside the flag format required by the challenge.

## Flag

```text
academy{549698}
```

## Key Takeaways

- Learned how to open a binary in GDB.
- Practiced disassembling a function using `disassemble main`.
- Identified an immediate value assigned to the `EAX` register.
- Converted a hexadecimal value to decimal using Python.
- Understood how register values can be used to solve introductory reverse-engineering challenges.

## Conclusion

The GDB Baby Step 1 challenge provided practical experience with GDB disassembly, x86_64 register analysis, and hexadecimal-to-decimal conversion.

