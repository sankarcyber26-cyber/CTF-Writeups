# PicoCTF — Warmed Up

## Challenge Information

- **Platform:** PicoCTF
- **Challenge Name:** Warmed Up
- **Category:** General Skills
- **Difficulty:** Easy
- **Tools Used:** Number-system conversion

## Objective

Convert a hexadecimal number into its decimal equivalent to obtain the challenge flag.

## Methodology

### Step 1: Analyze the Challenge

The challenge provides a hexadecimal value and requires converting it into decimal format.

### Step 2: Convert Hexadecimal to Decimal

Hexadecimal is a base-16 number system that uses digits `0–9` and letters `A–F`.

The provided hexadecimal value can be converted using Python:

```python
int("0xVALUE", 16)
```

Replace `0xVALUE` with the actual hexadecimal value provided in the challenge.

Alternatively, the `0x` prefix can be removed:

```python
int("VALUE", 16)
```

### Step 3: Verify the Result

The output is the decimal equivalent of the given hexadecimal number. Use that result to construct the flag in the format specified by the challenge.

## Flag

```text
<INSERT_ACTUAL_FLAG_HERE>
```

## Key Takeaways

- Understood the hexadecimal number system.
- Practiced converting hexadecimal values into decimal using Python.
- Learned how number-system conversions are used in basic CTF challenges.

## Conclusion

The Warmed Up challenge strengthened my understanding of hexadecimal-to-decimal conversion and basic Python number conversion.

---

**Disclaimer:** This write-up documents activity performed within the authorized PicoCTF challenge environment.
