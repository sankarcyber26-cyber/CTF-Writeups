# PW Crack 3

## Challenge Information

| Field | Details |
|---|---|
| Challenge Name | PW Crack 3 |
| Category | General Skills |
| Difficulty | Medium |
| Platform | CyLab Academy |
| Challenge Number | 08 |
| Status | Completed |

## Objective

Analyze the provided Python password checker, identify the correct password from seven possibilities using MD5 hash comparison, and decrypt the encrypted flag.

## Tools Used

- Kali Linux
- Terminal
- Python 3
- hashlib Python module
- MD5 hashing

## Step 1: Create the Working Directory

```bash
mkdir -p ~/pw-crack-3
cd ~/pw-crack-3
```

## Step 2: Download the Challenge Files

Download all three required files:

```bash
wget "https://challenge-files.cylabacademy.net/library/ae8548417223f50bd8a748c28e60fc688e1426cc7be7b09142456c1427def2c3/level3.py"

wget "https://challenge-files.cylabacademy.net/library/ae8548417223f50bd8a748c28e60fc688e1426cc7be7b09142456c1427def2c3/level3.flag.txt.enc"

wget "https://challenge-files.cylabacademy.net/library/ae8548417223f50bd8a748c28e60fc688e1426cc7be7b09142456c1427def2c3/level3.hash.bin"
```

Verify the downloaded files:

```bash
ls -l
```

## Step 3: Analyze the Python Source Code

Display the source code:

```bash
cat level3.py
```

The program imports the `hashlib` module and reads the encrypted flag and stored password hash.

The password verification function:

```python
def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()
```

This function converts the password into bytes and generates its MD5 hash.

The verification logic:

```python
user_pw_hash = hash_pw(user_pw)

if user_pw_hash == correct_pw_hash:
    print("Welcome back... your flag, user:")
    decryption = str_xor(flag_enc.decode(), user_pw)
    print(decryption)
```

The program compares the generated MD5 hash with the stored hash. If they match, it decrypts the flag using the provided XOR function.

## Step 4: Identify the Seven Possible Passwords

At the bottom of the source code, the challenge provides seven possible passwords:

```python
pos_pw_list = ["f09e", "4dcf", "87ab", "dba8", "752e", "3961", "f159"]
```

Only one password produces the same MD5 hash as the stored hash.

## Step 5: Compare the MD5 Hashes

Created a Python script to calculate the MD5 hash of each candidate password and compare it with `level3.hash.bin`.

```bash
python3 - <<'PY'
import hashlib

correct_hash = open("level3.hash.bin", "rb").read()

passwords = ["f09e", "4dcf", "87ab", "dba8", "752e", "3961", "f159"]

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
[+] Correct password: dba8
```

**Recovered Password:** `dba8`

## Step 6: Run the Password Checker

Execute the Python program:

```bash
python3 level3.py
```

Enter the recovered password:

```text
dba8
```

The program verifies the MD5 hash and decrypts the encrypted flag using the provided XOR function.

## Step 7: Capture the Flag

The program successfully decrypted the flag.

**Final Flag:**

```text
academy{m45h_fl1ng1ng_f684152a}
```

## Technical Concepts Learned

### 1. MD5 Hashing

MD5 is a cryptographic hash function that generates a 128-bit (16-byte) digest.

Python example:

```python
import hashlib

password = "dba8"
result = hashlib.md5(password.encode()).hexdigest()

print(result)
```

### 2. Hash Comparison

Instead of storing or comparing the original password directly, the program compares the generated password hash with a stored binary hash.

### 3. Dictionary-Based Password Testing

The challenge provides a limited list of seven candidate passwords. Each candidate can be hashed and compared against the stored hash to identify the correct password.

### 4. XOR Decryption

After successful password verification, the program uses the password as the key for the provided repeating-key XOR function to decrypt the flag.

### 5. Python Byte Handling

The challenge uses `encode()`, `bytearray()`, and `digest()` to convert password strings into bytes and generate binary hash output.

## Security Lessons

- Passwords should not be stored in plaintext.
- MD5 is considered cryptographically broken and should not be used for password storage.
- Modern applications should use password-hashing algorithms such as Argon2id, bcrypt, or scrypt with appropriate parameters.
- Short passwords are vulnerable to dictionary attacks and brute-force attempts.
- A hash is not encryption: hashing is designed to be one-way, while encryption is designed to be reversible with the appropriate key.

## Conclusion

Successfully completed PW Crack 3 by analyzing the Python source code, identifying seven possible passwords, comparing their MD5 hashes against the stored binary hash, recovering the password `dba8`, and decrypting the flag.

**Challenge Status: Completed**
