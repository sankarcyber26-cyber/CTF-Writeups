# 04 – New Caesar

**Platform:** CyLab Academy  
**Original Challenge:** picoCTF 2021  
**Author:** madStackspico  
**Category:** Cryptography  
**Difficulty:** Medium

## Challenge Description

We found a brand new type of encryption. Can you break the secret code?

**Ciphertext:**

```text
cbdabldadbplblcnpfpnpapapecpcn
```

## Step 1 – Download the Challenge File

```bash
mkdir -p ~/new_caesar
cd ~/new_caesar
wget "https://challenge-files.cylabacademy.net/library/4cf4ea26cde66bb3ef842ce6888992b798f8832b7644ca1b526a4cc86db4e42f/new_caesar.py"
```

## Step 2 – Understand the Encryption

The Python source code uses two encryption operations:

1. Custom Base16 encoding.
2. Caesar-style shifting with a single-character key.

The custom alphabet is:

```python
ALPHABET = string.ascii_lowercase[:16]
```

This means the alphabet contains only:

```text
abcdefghijklmnop
```

Each plaintext character is converted into 8-bit binary and split into two 4-bit groups.

Each 4-bit group is represented using one character from the custom alphabet.

After that, a single-character key shifts every encoded character.

## Step 3 – Decryption Method

To decrypt:

1. Reverse the Caesar-style shift.
2. Convert each pair of custom alphabet characters back into 8-bit binary.
3. Convert the binary values into plaintext characters.
4. Test all 16 possible keys.

## Step 4 – Python Decryption Script

Create the script:

```bash
nano solve.py
```

Use:

```python
import string

ALPHABET = string.ascii_lowercase[:16]
CIPHERTEXT = "cbdabldadbplblcnpfpnpapapecpcn"

def unshift(text, key):
    result = ""
    for c in text:
        result += ALPHABET[
            (ALPHABET.index(c) - ALPHABET.index(key)) % 16
        ]
    return result

def b16_decode(text):
    result = ""
    for i in range(0, len(text), 2):
        binary = (
            format(ALPHABET.index(text[i]), "04b") +
            format(ALPHABET.index(text[i + 1]), "04b")
        )
        result += chr(int(binary, 2))
    return result

for key in ALPHABET:
    decoded = b16_decode(unshift(CIPHERTEXT, key))
    print(f"Key: {key} | Output: {decoded}")
```

Run:

```bash
python3 solve.py
```

## Concepts Learned

- Custom Base16 encoding
- Binary-to-text conversion
- Caesar cipher with a custom alphabet
- Brute-force key testing
- Python decryption scripting

## Final Flag

```text
academy{et_tu?_a91448ca}
```

**Submission status:** Awaiting confirmation from CyLab Academy.
