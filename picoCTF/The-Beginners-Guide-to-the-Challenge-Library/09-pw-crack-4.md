# PW Crack 4

## Challenge Information

| Field | Details |
|---|---|
| Challenge Name | PW Crack 4 |
| Category | General Skills |
| Difficulty | Medium |
| Platform | CyLab Academy |
| Challenge Number | 09 |
| Status | Completed |

## Objective

Analyze the provided Python password checker, identify the correct password from 100 possible candidates using MD5 hash comparison, and decrypt the encrypted flag.

## Tools Used

- Kali Linux
- Terminal
- Python 3
- hashlib module
- Regular expressions (`re`)

## Step 1: Create the Working Directory

```bash
mkdir -p ~/pw-crack-4
cd ~/pw-crack-4
```

## Step 2: Download the Challenge Files

```bash
wget "https://challenge-files.cylabacademy.net/library/846131a53233d7d11fb53d10ebe53b2addb4693a7f39e2f464fed1d85226b899/level4.py"

wget "https://challenge-files.cylabacademy.net/library/846131a53233d7d11fb53d10ebe53b2addb4693a7f39e2f464fed1d85226b899/level4.flag.txt.enc"

wget "https://challenge-files.cylabacademy.net/library/846131a53233d7d11fb53d10ebe53b2addb4693a7f39e2f464fed1d85226b899/level4.hash.bin"
```

Verify the downloaded files:

```bash
ls -l
```

## Step 3: Analyze the Python Source Code

Display the source code:

```bash
cat level4.py
```

The program imports the `hashlib` module and defines a function to generate an MD5 hash from a password.

```python
def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()
```

The password verification logic compares the generated hash with the stored binary hash.

```python
user_pw_hash = hash_pw(user_pw)

if user_pw_hash == correct_pw_hash:
    print("Welcome back... your flag, user:")
    decryption = str_xor(flag_enc.decode(), user_pw)
    print(decryption)
```

The source code also contains a list of 100 possible passwords in `pos_pw_list`.

## Step 4: Extract and Test the 100 Passwords

Instead of checking each password manually, a Python script was used to extract the candidate list and test every password against the stored MD5 hash.

```bash
python3 - <<'PY'
import hashlib
import re

correct_hash = open("level4.hash.bin", "rb").read()

with open("level4.py", "r") as file:
    source = file.read()

match = re.search(r'pos_pw_list\s*=\s*(\[.*?\])', source, re.S)
passwords = eval(match.group(1))

for password in passwords:
    password_hash = hashlib.md5(password.encode()).digest()

    if password_hash == correct_hash:
        print("[+] Correct password:", password)
        break
else:
    print("[-] No matching password found")
PY
```

Output:

```text
[+] Correct password: bb8e
```

**Recovered Password:** `bb8e`

## Step 5: Run the Password Checker

Execute the original Python program:

```bash
python3 level4.py
```

Enter the recovered password:

```text
bb8e
```

The program verifies the MD5 hash and decrypts the encrypted flag using the provided repeating-key XOR function.

## Step 6: Capture the Flag

The password was accepted, and the encrypted flag was successfully decrypted.

**Final Flag:**

```text
academy{fl45h_5pr1ng1ng_c1e14a37}
```

## Technical Concepts Learned

### 1. MD5 Hashing

MD5 generates a 128-bit digest from input data. The challenge uses the digest to verify the password.

### 2. Python For Loops

A `for` loop can iterate through a collection of candidate passwords and test each one automatically.

### 3. Regular Expressions

The Python `re` module was used to locate and extract the `pos_pw_list` definition from the source code.

### 4. Automated Password Testing

Automating candidate testing is faster and more reliable than manually checking 100 passwords.

### 5. XOR Decryption

After successful password verification, the supplied repeating-key XOR function decrypts the flag using the recovered password.

## Security Lessons

- Hardcoded password lists can expose credentials to source-code inspection.
- Short passwords are vulnerable to dictionary and brute-force attacks.
- MD5 is unsuitable for modern password storage because it is fast and vulnerable to attacks.
- Use Argon2id, bcrypt, or scrypt for password hashing.
- Never expose sensitive credentials or password-verification logic in client-accessible code.

## Conclusion

Successfully completed PW Crack 4 by analyzing the Python source code, extracting 100 candidate passwords, automating MD5 hash comparisons with a Python loop, recovering the password `bb8e`, and decrypting the flag.

**Challenge Status: Completed**
