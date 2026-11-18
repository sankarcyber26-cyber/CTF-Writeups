# Password Checker – Level 1

## 1. Challenge Information

| Field | Details |
|---|---|
| Platform | CyLab Academy |
| Learning Path | The Beginner's Guide to the Challenge Library |
| Challenge Number | 06 |
| Challenge Name | Password Checker – Level 1 |
| Category | General Skills |
| Technique | Python Source Code Analysis and XOR Decryption |
| Difficulty | Easy |
| Status | Completed |

## 2. Objective

The objective was to analyze a Python password checker, identify the correct password, and use it to decrypt an encrypted flag.

## 3. Tools Used

- Kali Linux
- Python 3
- `wget`
- `cat`
- Terminal

## 4. Challenge Files

Two files were provided:

- `level1.py` – Python password checker.
- `level1.flag.txt.enc` – Encrypted flag.

## 5. Exploitation / Solving Steps

### Step 1 – Create a Working Directory

Created a separate directory for the challenge.

```bash
mkdir -p ~/password-checker-level1
cd ~/password-checker-level1
```

### Step 2 – Download the Challenge Files

Downloaded the Python script:

```bash
wget "https://challenge-files.cylabacademy.net/library/85308c2e48584c90de2af360f3324194bde62acf79d53364ea85fd34ce0eaa1f/level1.py"
```

Downloaded the encrypted flag:

```bash
wget "https://challenge-files.cylabacademy.net/library/85308c2e48584c90de2af360f3324194bde62acf79d53364ea85fd34ce0eaa1f/level1.flag.txt.enc"
```

### Step 3 – Analyze the Python Source Code

Used the `cat` command to inspect the source code.

```bash
cat level1.py
```

Identified the password verification condition:

```python
if(user_pw == "691d"):
```

This condition revealed that the correct password was `691d`.

### Step 4 – Understand the Password Check

The program accepts user input and compares it with a hardcoded password.

```python
user_pw = input("Please enter correct password for flag: ")

if(user_pw == "691d"):
    print("Welcome back... your flag, user:")
```

If the entered password matches, the program proceeds to decrypt the encrypted flag.

### Step 5 – Understand XOR Decryption

The script uses a function called `str_xor()`.

```python
def str_xor(secret, key):
    new_key = key
    i = 0

    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)

    return "".join([
        chr(ord(secret_c) ^ ord(new_key_c))
        for (secret_c, new_key_c) in zip(secret, new_key)
    ])
```

**Explanation:**

- The password is used as the XOR key.
- The key is repeated until it matches the encrypted data length.
- Each character is XORed with the corresponding key character.
- The resulting characters form the decrypted flag.

The challenge hint indicated that reverse engineering this function was unnecessary.

### Step 6 – Execute the Password Checker

Executed the Python script:

```bash
python3 level1.py
```

Entered the discovered password:

```text
691d
```

The program accepted the password and decrypted the encrypted flag.

## 6. Final Password

```text
691d
```

## 7. Flag

```text
academy{545h_r1ng1ng_329bb7f6}
```

## 8. Security Concepts Learned

1. Python source code analysis.
2. Hardcoded password identification.
3. Password verification logic.
4. XOR encryption and decryption.
5. Repeating-key XOR.
6. Encrypted file analysis.

## 9. Security Recommendations

- Never store passwords directly in source code.
- Avoid hardcoded secrets and credentials.
- Use secure password hashing algorithms such as Argon2id or bcrypt.
- Protect encryption keys separately from encrypted data.
- Avoid exposing sensitive application logic to unauthorized users.

## 10. Conclusion

Successfully analyzed the Python password checker and identified the hardcoded password `691d`.

Used the password to pass the verification check and decrypt the encrypted flag.

This challenge demonstrated how source code inspection can reveal hardcoded credentials and how XOR-based encryption can be used to protect data.

**Final Result: Successfully Completed.**
