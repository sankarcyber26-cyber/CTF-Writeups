# Python Wrangling - picoCTF

## Category

General Skills

## Difficulty

Medium

## Description

The challenge provides Python scripts and a password file. The goal is to use the Python script with the provided password to decrypt the flag.

## Approach

1. Download the required files:

```text
ende.py
pw.txt
flag.txt.en
```

2. Check the files:

```bash
ls
```

3. Use the Python script in decrypt mode:

```bash
python3 ende.py -d flag.txt.en
```

4. The script asks for the password.

5. Read the password from the password file:

```bash
cat pw.txt
```

6. Enter the password when the script asks for it.

7. The encrypted flag is decrypted and displayed.

## Flag

```text
picoCTF{4p0110_1n_7h3_h0us3_67c6cc96}
```

## Learning

* Running Python scripts from the terminal
* Using command-line arguments
* Reading files with `cat`
* Using a password to decrypt an encrypted file
* Basic Python command-line usage

## Key Commands

```bash
ls
cat pw.txt
python3 ende.py -d flag.txt.en
```

**Status:** Solved ✅
