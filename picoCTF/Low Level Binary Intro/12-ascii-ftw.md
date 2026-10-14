# ASCII FTW

## Challenge Information
- **Platform:** CyLab Security Academy
- **Category:** Reverse Engineering
- **Difficulty:** Easy
- **Tools:** Kali Linux, GDB

## Objective
Analyze the binary's assembly instructions and decode hexadecimal values into ASCII characters to recover the flag.

## Step 1: Download the Challenge File

Download the binary and save it in the Kali Linux Downloads directory.

```bash
cd ~/Downloads
wget "https://challenge-files.cylabacademy.net/library/60ac124e46a3c8894d62ac83ba929cdebd78f28658dc91611d4aae76ad1cb41a/asciiftw" -O asciiftw
```

## Step 2: Open the Binary in GDB

```bash
gdb ./asciiftw
```

Disassemble the `main` function:

```gdb
disassemble main
```

## Step 3: Analyze the Assembly

The program stores individual hexadecimal values as bytes in memory using `movb` instructions.

Examples:

| Hexadecimal | ASCII character |
|---|---|
| `0x61` | `a` |
| `0x63` | `c` |
| `0x64` | `d` |
| `0x7b` | `{` |
| `0x41` | `A` |
| `0x5f` | `_` |
| `0x7d` | `}` |

Decoding the byte values reveals the flag text.

## Step 4: Recover the Flag

The decoded flag is:

```text
academy{ASCII_IS_EASY_AC3E0C8C}
```

## Key Learning
- `disassemble main` displays the assembly instructions for a function.
- `movb` stores a single byte in memory.
- Hexadecimal values can represent ASCII characters.
- Reverse engineering helps reveal strings constructed at runtime or stored as individual bytes.

## Conclusion
This challenge introduced basic assembly analysis and hexadecimal-to-ASCII conversion using GDB on Kali Linux.
