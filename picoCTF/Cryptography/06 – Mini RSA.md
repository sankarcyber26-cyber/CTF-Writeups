# 06 – Mini RSA

**Platform:** CyLab Academy  
**Original Challenge:** picoCTF 2021  
**Author:** Sara  
**Category:** Cryptography  
**Difficulty:** Medium

## Challenge Description

What happens if RSA uses a small public exponent?

The challenge uses `e = 3` and provides an encrypted message with padding. The hint explains that the plaintext is included somewhere inside the decrypted message, not necessarily at the beginning.

## Step 1 – Download the File

```bash
mkdir -p ~/mini-rsa
cd ~/mini-rsa
wget "https://challenge-files.cylabacademy.net/library/e5f3ed71ca30832720bfbed988000b07159531af4efd8bde534455cb31281df7/values"
```

## Step 2 – Read the RSA Values

```bash
cat values
```

Important values:

- `N` – RSA modulus
- `e = 3` – Public exponent
- `c` – Ciphertext

## Step 3 – Understand the Vulnerability

RSA encryption:

\[
c = M^e \bmod N
\]

Since `e = 3`, we have:

\[
c = M^3 \bmod N
\]

If the plaintext is small enough that:

\[
M^3 < N
\]

then:

\[
c = M^3
\]

We can recover the plaintext by calculating the exact integer cube root of `c`.

## Step 4 – Decrypt Using Python

Create a Python script:

```bash
nano solve.py
```

Paste:

```python
c = 5709720175026317841944505166332182779419760031115432215563425901875620052791608163398750297304277886495537367793006288112991932717211066611899319963701838062828209254458935983141207100322897221021063116398621664612418813778554568264340430225832578419510188716272485416847020031786240493474216219976022230869888952027678216917573096647103329007747318226924546155390806085120914969452892742334587155888067115809741247942520249413550823776542714197976954393983964547415885494497967317041948018762619837565110934913856322148114605081220228082382496419481186347789827332766319099768385339675485674098729928722491454024819209643705436617193628436345338680537047177323301194162660757103489761598885882853346119600569195748535459069143523542108427003139728980057083066664641150644821647353430627540846457261643465679095174704766947857556896761656169629741900371937539062751103533758611539748595561989792317060484717828643461989154370495487728398479845553917495920818130003766392290200672893336450122809476169268494312

def integer_cube_root(n):
    low, high = 0, 1

    while high ** 3 <= n:
        high *= 2

    while low + 1 < high:
        mid = (low + high) // 2

        if mid ** 3 <= n:
            low = mid
        else:
            high = mid

    return low

m = integer_cube_root(c)

if m ** 3 == c:
    print("Exact cube root found!")
else:
    print("Not an exact cube root")

plaintext = m.to_bytes((m.bit_length() + 7) // 8, "big")
print(plaintext.decode())
```

Run:

```bash
python3 solve.py
```

## Step 5 – Understand the Output

The decrypted plaintext contains leading spaces followed by the flag.

The important observation is that the cube root is exact:

\[
M^3 = c
\]

No floating-point approximation is required.

## Concepts Learned

- RSA encryption
- Small public exponent vulnerability
- Integer cube root
- Modular arithmetic
- Python arbitrary-precision integers
- Plaintext padding

## Final Flag

```text
academy{e_sh0u1d_b3_lArg3r_35f26e1a}
```

**Submission status:** Awaiting confirmation from CyLab Academy.
