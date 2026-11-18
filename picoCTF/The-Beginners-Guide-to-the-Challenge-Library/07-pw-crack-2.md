# PW Crack 2

## Challenge Information

| Field | Details |
|---|---|
| Challenge Name | PW Crack 2 |
| Category | General Skills |
| Difficulty | Easy |
| Platform | CyLab Academy |
| Challenge Number | 07 |
| Status | Completed |

## Objective

Analyze the provided Python password checker, identify the correct password, and use it to decrypt the encrypted flag.

## Tools Used

- Kali Linux
- Terminal
- Python 3
- `cat` command

## Step 1: Create the Working Directory

```bash
mkdir -p ~/pw-crack-2
cd ~/pw-crack-2
```

## Step 2: Download the Challenge Files

Download the Python password checker and encrypted flag file.

```bash
wget "https://challenge-files.cylabacademy.net/library/d6d0540f2ff74e5b7e0fafa03b47cee3e9feb314bd1a7a03478d44fa84a2227c/level2.py"

wget "https://challenge-files.cylabacademy.net/library/d6d0540f2ff74e5b7e0fafa03b47cee3e9feb314bd1a7a03478d44fa84a2227c/level2.flag.txt.enc"
```

## Step 3: Analyze the Python Source Code

Display the source code:

```bash
cat level2.py
```

The password verification condition was:

```python
if( user_pw == chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65) ):
```

The password was represented using Python's `chr()` function and hexadecimal values.

## Step 4: Decode the Password

The `chr()` function converts an integer Unicode code point into its corresponding character.

| Python expression | Character |
|---|---|
| `chr(0x33)` | `3` |
| `chr(0x39)` | `9` |
| `chr(0x63)` | `c` |
| `chr(0x65)` | `e` |

Combining the characters:

```text
39ce
```

**Recovered password:** `39ce`

## Step 5: Run the Password Checker

Execute the Python program:

```bash
python3 level2.py
```

Enter the recovered password when prompted:

```text
39ce
```

The program verifies the password and uses the existing `str_xor()` function to decrypt the encrypted flag.

## Step 6: Capture the Flag

The program successfully decrypted the flag.

**Final Flag:**

```text
academy{tr45h_51ng1ng_82234aa4}
```

## Technical Concepts Learned

### 1. Python `chr()` Function

The `chr()` function converts a numeric Unicode code point into a character.

Example:

```python
print(chr(0x33))
```

Output:

```text
3
```

### 2. Hexadecimal Representation

Hexadecimal is a base-16 number system that uses digits `0–9` and letters `A–F`.

The challenge used hexadecimal values to hide the password characters.

### 3. XOR Decryption

The challenge used a repeating-key XOR function to decrypt the encrypted flag.

The password was used as the XOR key.

### 4. Source Code Analysis

Inspecting the password verification logic helped recover the password without brute-forcing it.

## Security Lessons

- Hardcoded passwords can be recovered by inspecting application source code.
- Encoding a password with hexadecimal values does not provide real security.
- Sensitive credentials should never be stored directly in client-accessible source code.
- XOR encryption alone is not a substitute for secure cryptographic design.

## Conclusion

Successfully completed PW Crack 2 by analyzing the Python source code, decoding the hexadecimal character values using `chr()`, recovering the password `39ce`, and decrypting the flag using the provided XOR function.

**Challenge Status: Completed**
