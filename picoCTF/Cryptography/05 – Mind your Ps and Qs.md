# 05 – Mind your Ps and Qs

**Platform:** CyLab Academy  
**Original Challenge:** picoCTF 2021  
**Author:** Sara  
**Category:** Cryptography  
**Difficulty:** Medium

## Challenge Description

In RSA, a small public exponent `e` can be problematic, but what about `N`?

The challenge provides RSA values and asks us to decrypt the ciphertext.

## Step 1 – Download the File

```bash
mkdir -p ~/mind-your-ps-and-qs
cd ~/mind-your-ps-and-qs
wget "https://challenge-files.cylabacademy.net/library/4a3b1aca528881eece43ed483e527d3700c5e388eb5ab2291015dbd67a809f31/values"
```

## Step 2 – Read the RSA Values

```bash
cat values
```

Provided values:

```text
c: 717608817902276639011922897702552744324264244069272484013719744328086856277690292

n: 1368992139315019955067447961537607041364451719382349005056752379702694554965203011

e: 65537
```

- `c` – Ciphertext
- `n` – RSA modulus
- `e` – Public exponent

## Step 3 – Factorize N

RSA uses:

\[
N = p \times q
\]

The modulus is small enough to factorize into two prime numbers.

```text
p = 2074606527507983503944226222695401999839

q = 659880377875535146491994798968813949893149
```

## Step 4 – Calculate the Private Key

Calculate Euler's totient:

\[
\phi(N) = (p-1)(q-1)
\]

Calculate the private exponent:

\[
d = e^{-1} \bmod \phi(N)
\]

## Step 5 – Decrypt the Ciphertext

RSA decryption:

\[
m = c^d \bmod N
\]

Run the Python command:

```bash
python3 -c "p=2074606527507983503944226222695401999839; q=659880377875535146491994798968813949893149; e=65537; n=1368992139315019955067447961537607041364451719382349005056752379702694554965203011; c=717608817902276639011922897702552744324264244069272484013719744328086856277690292; phi=(p-1)*(q-1); d=pow(e,-1,phi); m=pow(c,d,n); h=hex(m)[2:]; h='0'+h if len(h)%2 else h; print(bytes.fromhex(h)[::-1].decode())"
```

## Concepts Learned

- RSA encryption and decryption
- Public and private keys
- RSA modulus and prime factorization
- Euler's totient function
- Modular multiplicative inverse
- Python modular exponentiation using `pow()`
- Little-endian byte order

## Final Flag

```text
academy{sma11_N_n0_g0od_a3ac7152}
```

**Submission status:** Awaiting confirmation from CyLab Academy.
