# PW Crack 5

## Challenge Information

| Field | Details |
|---|---|
| Challenge Name | PW Crack 5 |
| Category | General Skills |
| Difficulty | Medium |
| Platform | CyLab Academy |
| Challenge Number | 10 |
| Status | Completed |

## Objective

Analyze the Python password checker and use the provided dictionary file to identify the correct password by comparing MD5 hashes. Use the recovered password to decrypt the encrypted flag.

## Tools Used

- Kali Linux
- Terminal
- Python 3
- hashlib module
- Dictionary file

## Step 1: Create the Working Directory

```bash
mkdir -p ~/pw-crack-5
cd ~/pw-crack-5
```

## Step 2: Download the Challenge Files

```bash
wget "https://challenge-files.cylabacademy.net/library/a2b32b2b4b000d12f209c65a2c414ede32d08a63774f7e150e3e30a3892a386d/level5.py"

wget "https://challenge-files.cylabacademy.net/library/a2b32b2b4b000d12f209c65a2c414ede32d08a63774f7e150e3e30a3892a386d/level5.flag.txt.enc"

wget "https://challenge-files.cylabacademy.net/library/a2b32b2b4b000d12f209c65a2c414ede32d08a63774f7e150e3e30a3892a386d/level5.hash.bin"

wget "https://challenge-files.cylabacademy.net/library/a2b32b2b4b000d12f209c65a2c414ede32d08a63774f7e150e3e30a3892a386d/dictionary.txt"
```

Verify the files:

```bash
ls -l
```

## Step 3: Analyze the Python Source Code

```bash
cat level5.py
```

The program imports the `hashlib` module, reads the encrypted flag, and loads the stored password hash.

The password hashing function:

```python
def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()
```

The program compares the MD5 hash of the entered password with the stored hash. If they match, it decrypts the flag using the provided repeating-key XOR function.

## Step 4: Understand the Dictionary File

Unlike previous challenges, the possible passwords are stored in a separate file named `dictionary.txt`.

The dictionary contains multiple candidate passwords, with one matching the stored hash.

The important Python operations are:

- `open()` – Opens the dictionary file.
- `for line in file` – Reads the file one line at a time.
- `strip()` – Removes leading and trailing whitespace, including newline characters.
- `hashlib.md5()` – Generates an MD5 hash.
- `break` – Stops the loop after finding a matching password.

## Step 5: Find the Correct Password

Use Python to test every dictionary entry against the stored hash.

```bash
python3 - <<'PY'
import hashlib

correct_hash = open("level5.hash.bin", "rb").read()

with open("dictionary.txt", "r") as file:
    for line in file:
        password = line.strip()
        password_hash = hashlib.md5(password.encode()).digest()

        if password_hash == correct_hash:
            print("[+] Correct password:", password)
            break
    else:
        print("[-] No matching password found")
PY
```

The script reads each dictionary entry, removes whitespace, calculates its MD5 hash, and compares it with the stored hash.

## Step 6: Run the Password Checker

Execute:

```bash
python3 level5.py
```

Enter the recovered password when prompted.

The program verifies the password and decrypts the encrypted flag.

## Step 7: Capture the Flag

The password was accepted, and the encrypted flag was successfully decrypted.

**Final Flag:**

```text
academy{h45h_sl1ng1ng_27d64792}
```

## Technical Concepts Learned

### 1. Dictionary-Based Password Testing

A dictionary attack tests a collection of possible passwords instead of trying every possible character combination.

### 2. Python File Handling

The `open()` function allows Python to read external files such as password dictionaries.

### 3. String strip() Method

The `strip()` method removes leading and trailing whitespace.

Example:

```python
word = "password123\n"
print(word.strip())
```

Output:

```text
password123
```

### 4. MD5 Hash Comparison

The challenge uses MD5 to compare candidate passwords against a stored binary hash.

### 5. XOR Decryption

After password verification, the program uses the password as a repeating XOR key to decrypt the flag.

## Security Lessons

- Dictionary attacks can identify weak or commonly used passwords.
- Passwords should not be stored using MD5.
- Modern applications should use Argon2id, bcrypt, or scrypt with appropriate parameters.
- Password policies should encourage long, unique passwords.
- Sensitive password information should not be exposed in application source code.

## Conclusion

Successfully completed PW Crack 5 by analyzing the Python password checker, reading the external dictionary file, removing whitespace using `strip()`, comparing MD5 hashes, and recovering the password needed to decrypt the flag.

**Challenge Status: Completed**
