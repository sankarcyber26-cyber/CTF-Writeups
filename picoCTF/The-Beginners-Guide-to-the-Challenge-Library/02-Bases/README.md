# Challenge 2 – Bases

## Challenge Information
- **Platform:** picoCTF 2019
- **Challenge Name:** Bases
- **Category:** General Skills
- **Difficulty:** Easy
- **Challenge Number:** 2
- **Tool Used:** CyberChef

## Challenge Description

What does this `bDNhcm5fdGgzX3IwcDM1` mean? I think it has something to do with bases.

## Objective

Decode the given encoded string and find the flag.

## Solution

### Step 1: Identify the Encoding

The given string:

`bDNhcm5fdGgzX3IwcDM1`

looks like Base64 encoding.

### Step 2: Decode Using CyberChef

1. Open https://gchq.github.io/CyberChef/
2. Paste the encoded string into the Input section.
3. Search for the operation `From Base64`.
4. Drag it into the Recipe section.
5. Check the Output section.

### Step 3: Decoded Output

`l3arn_th3_r0p35`

### Step 4: Linux Terminal Method

The same result can be obtained using Kali Linux:

```bash
echo "bDNhcm5fdGgzX3IwcDM1" | base64 -d
```

Output:

```text
l3arn_th3_r0p35
```

## Flag

```text
academy{l3arn_th3_r0p35}
```

## What I Learned

1. Learned about Base64 encoding and decoding.
2. Understood how to identify Base64 strings.
3. Practiced decoding using CyberChef.
4. Learned the Linux `base64 -d` command.
5. Understood that Base64 is encoding, not encryption.

## Key Takeaway

Base64 converts data into a text-friendly format. It is not encryption because anyone can decode it without a secret key.

**Challenge Status:** Solved ✅
