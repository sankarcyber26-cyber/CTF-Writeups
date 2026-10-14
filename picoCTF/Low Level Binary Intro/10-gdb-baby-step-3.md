# CyLab Academy — GDB Baby Step 3

## Challenge Information

- **Platform:** CyLab Security Academy
- **Learning Path:** Low Level Binary Intro
- **Challenge Name:** GDB Baby Step 3
- **Category:** Reverse Engineering
- **Difficulty:** Medium
- **Architecture:** x86_64
- **Tools Used:** Kali Linux, GDB

## Objective

Examine the bytes of a constant stored in memory using GDB and construct the flag from the four bytes in memory order.

## Methodology

### Step 1: Disassemble the Main Function

Used GDB to inspect the assembly instructions.

```gdb
disassemble main
```

The relevant instructions were:

```asm
movl $0x2262c96b, -0x4(%rbp)
mov -0x4(%rbp), %eax
```

### Step 2: Analyze the Instructions

The first instruction stores the hexadecimal value `0x2262c96b` in a four-byte memory location.

The second instruction loads that value into the `EAX` register.

### Step 3: Understand Little-Endian Byte Order

The hexadecimal value can be divided into four bytes:

```text
22 62 c9 6b
```

The x86_64 architecture uses little-endian byte order. Therefore, the bytes are stored in memory from the least significant byte to the most significant byte:

```text
6b c9 62 22
```

### Step 4: Examine the Memory Using GDB

Set a breakpoint after the memory store instruction and before the value is loaded into `EAX`.

```gdb
break *main+22
run
x/4xb $rbp-4
```

The `x/4xb` command examines four individual bytes in hexadecimal format.

Expected byte sequence:

```text
0x6b 0xc9 0x62 0x22
```

### Step 5: Construct the Flag

Combined the four bytes in memory order according to the challenge's required flag format.

## Flag

```text
academy{0x6bc96222}
```

## Key Takeaways

- Practiced disassembling a binary with GDB.
- Learned how to inspect individual bytes in memory.
- Understood little-endian byte order on x86_64 systems.
- Learned the difference between a multi-byte integer representation and its byte order in memory.

## Conclusion

The GDB Baby Step 3 challenge demonstrated how to inspect memory byte by byte and apply little-endian byte ordering to solve a reverse-engineering problem.
