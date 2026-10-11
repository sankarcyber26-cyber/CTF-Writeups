# PicoCTF — Binary Decimal Conversion

## Challenge Information

- **Platform:** PicoCTF
- **Challenge Name:** Binary Decimal Conversion
- **Category:** General Skills
- **Difficulty:** Easy
- **Tools Used:** Kali Linux Terminal, Python 3

## Objective

Convert a binary number into its decimal equivalent and use the result to solve the challenge.

## Methodology

### Step 1: Identify the Binary Value

Examined the binary number provided by the challenge.

```text
<INSERT_BINARY_VALUE_HERE>
```

Binary is a base-2 number system that uses only two digits: `0` and `1`.

### Step 2: Convert Binary to Decimal

Used Python to convert the binary value into decimal.

```python
binary_value = "INSERT_BINARY_VALUE"
decimal_value = int(binary_value, 2)

print(decimal_value)
```

The second argument, `2`, tells Python that the input number is in base 2.

### Step 3: Verify the Result

Executed the code and recorded the decimal equivalent of the binary number.

```text
Decimal result: <INSERT_DECIMAL_VALUE_HERE>
```

### Step 4: Retrieve the Flag

Used the result and the flag format specified by the challenge to identify the final flag.

## Flag

```text
<INSERT_ACTUAL_FLAG_HERE>
```

## Key Takeaways

- Understood the binary number system.
- Practiced converting binary values into decimal using Python.
- Learned how to use Python's `int()` function with a base argument.
- Improved basic number-system conversion skills.

## Conclusion

The Binary Decimal Conversion challenge reinforced binary-to-decimal conversion and provided practical experience using Python for basic numerical operations.

---

**Disclaimer:** This write-up documents activity performed within the authorized CTF challenge environment.
