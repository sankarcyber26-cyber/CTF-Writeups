# Cryptography Can Be Easy – CyLab Academy

## 1. Challenge Information

| Field | Details |
|---|---|
| Platform | CyLab Academy |
| Learning Path | The Beginner's Guide to the Challenge Library |
| Challenge Number | 01 |
| Challenge Name | Cryptography Can Be Easy |
| Category | Cryptography |
| Cipher | ROT13 |
| Status | Completed |

## 2. Objective

The objective of this challenge was to decode an encoded message using the ROT13 substitution cipher and retrieve the hidden flag.

## 3. Tools Used

- CyberChef
- Web Browser
- ROT13 Operation

## 4. Challenge Analysis

The challenge provided a file named `values.txt`.

The hint indicated that the challenge could be solved using ROT13.

### What is ROT13?

ROT13 stands for Rotate by 13 Places.

It is a simple substitution cipher that shifts each English alphabet letter by 13 positions.

For example:

- A becomes N
- B becomes O
- C becomes P
- N becomes A
- O becomes B

ROT13 is reversible. Applying ROT13 twice returns the original text.

## 5. Exploitation / Solving Steps

### Step 1 – Access CyberChef

Opened CyberChef in the browser:

https://gchq.github.io/CyberChef/

### Step 2 – Select ROT13

Searched for `ROT13` in the Operations search box.

Added the ROT13 operation to the Recipe section.

### Step 3 – Provide the Encoded Text

Copied the contents of `values.txt` and pasted them into the Input section.

### Step 4 – Decode the Message

CyberChef automatically applied ROT13 and displayed the decoded result in the Output section.

### Step 5 – Retrieve the Flag

Copied the decoded flag from the Output section.

## 6. Flag

```text
academy{next_time_I'll_try_2_rounds_of_rot13_5c5f5b36}
```

## 7. Security Concepts Learned

- Introduction to cryptography
- ROT13 substitution cipher
- Character substitution
- Encoding and decoding
- Using CyberChef for cryptographic analysis

## 8. Security Notes

ROT13 is not secure encryption.

It does not use a secret key and provides no meaningful protection for sensitive information.

It should only be treated as a simple obfuscation technique.

## 9. Conclusion

Successfully decoded the challenge file using the ROT13 operation in CyberChef and retrieved the hidden flag.

**Result: Successfully Completed.**
