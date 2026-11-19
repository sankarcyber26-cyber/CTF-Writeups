# 02 – Caesar Cipher

## Challenge Information

| Field | Details |
|---|---|
| Challenge | Caesar |
| Category | Cryptography |
| Difficulty | Medium |
| Platform | CyLab Academy |
| Original Challenge | picoCTF 2019 |

## Objective

Decrypt the given encrypted message using the Caesar cipher technique and recover the flag.

## Tools Used

- Kali Linux
- Terminal
- Caesar Cipher decryption
- Brute-force technique

## Step 1 – Download the Challenge File

Created a working directory and downloaded the encrypted file.

```bash
mkdir -p ~/caesar
cd ~/caesar
wget "https://challenge-files.cylabacademy.net/library/eb4325fac37933de66857090e6c78c226267394ccaf5c079ff593e3e33b4b95a/data.enc"
```

## Step 2 – Read the Encrypted Message

Used the `cat` command to view the encrypted message.

```bash
cat data.enc
```

Encrypted message:

```text
academy{jyvzzpunaolybipjvubsxjvqwk}
```

## Step 3 – Understand Caesar Cipher

Caesar Cipher is a substitution cipher in which each alphabet character is shifted by a fixed number of positions.

The challenge was solved using a backward shift of 7 positions.

## Step 4 – Decrypt the Message

Encrypted text:

```text
jyvzzpunaolybipjvubs
