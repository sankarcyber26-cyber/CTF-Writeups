# PicoCTF — Bit-O-Asm-1

## Challenge Information

- **Platform:** PicoCTF
- **Challenge Name:** Bit-O-Asm-1
- **Category:** Reverse Engineering
- **Difficulty:** Easy
- **Tools Used:** Assembly code analysis

## Objective

Analyze the provided assembly instruction to determine the value stored in the `EAX` register and retrieve the flag.

## Methodology

### Step 1: Analyze the Assembly Instruction

The challenge provides an assembly instruction similar to the following:

```asm
mov eax, 0x30
```

### Step 2: Understand the Instruction

The `mov` instruction copies a value into a register.

- `mov` — Copies a value to the destination.
- `eax` — A 32-bit general-purpose CPU register.
- `0x30` — A hexadecimal value.

### Step 3: Convert Hexadecimal to Decimal

The hexadecimal value `0x30` converts to decimal as follows:

\[
(3 \times 16) + 0 = 48
\]

Therefore, the value stored in the `EAX` register is `48`.

### Step 4: Construct the Flag

The calculated decimal value is placed into the flag format specified by the challenge.

## Flag

```text
academy{48}
```

## Key Takeaways

- Learned how to interpret the `mov` assembly instruction.
- Understood the purpose of the `EAX` register.
- Practiced hexadecimal-to-decimal conversion.
- Gained introductory experience analyzing assembly code.

## Conclusion

The Bit-O-Asm-1 challenge introduced fundamental assembly language concepts and demonstrated how register values can be analyzed to retrieve a CTF flag.

---

**Disclaimer:** This write-up documents activity performed within the authorized PicoCTF challenge environment.
