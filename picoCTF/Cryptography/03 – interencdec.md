# 03 – interencdec

**Platform:** CyLab Academy  
**Original Challenge:** picoCTF 2024  
**Category:** Cryptography  
**Difficulty:** Easy  
**Author:** NGIRIMANA Schadrack

## Challenge Description

Can you get the real meaning from this file?

**Hint:** Engaging in various decoding processes is of utmost importance.

## Step 1 – Download the File

```bash
mkdir -p ~/interencdec
cd ~/interencdec
wget "https://challenge-files.cylabacademy.net/library/0d5754d51dc425dbb46c76eef33bb2b596a1a3bc6f4163ddd2a215f7e0d45198/enc_flag"
```

## Step 2 – Identify the Encoded Data

```bash
cat enc_flag
```

Output:

```text
YidhR3BvYTJ4MFpudHFhR3g2YUhsZmF6TnFlVGwzWVROclh6Z3hiR3M1YlRBeWZRPT0nCg==
```

## Step 3 – First Base64 Decoding

```bash
base64 -d enc_flag
```

Output:

```text
b'aGpoa2x0ZntqaGx6aHlfazNqeTl3YTNrXzgxbGs5bTAyfQ=='
```

## Step 4 – Second Base64 Decoding

```bash
echo 'aGpoa2x0ZntqaGx6aHlfazNqeTl3YTNrXzgxbGs5bTAyfQ==' | base64 -d
```

Output:

```text
hjhkltf{jhlzhy_k3jy9wa3k_81lk9m02}
```

## Step 5 – Caesar Cipher Decoding

The decoded text contains another encoding layer: Caesar Cipher.

The letters are shifted 7 positions backward.

```bash
python3 -c "s='hjhkltf{jhlzhy_k3jy9wa3k_81lk9m02}'; print(''.join(chr((ord(c)-97-7)%26+97) if c.islower() else c for c in s))"
```

## Concepts Learned

- Base64 decoding
- Identifying multiple encoding layers
- Caesar Cipher
- Using Linux terminal commands
- Python for decoding text

## Final Flag

```text
academy{caesar_d3cr9pt3d_81ed9f02}
```

**Submission status:** Pending confirmation from the challenge platform.
