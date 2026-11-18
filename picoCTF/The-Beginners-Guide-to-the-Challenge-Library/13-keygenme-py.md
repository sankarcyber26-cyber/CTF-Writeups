# 13 – Keygenme-py

## Challenge Information

| Field | Details |
|---|---|
| Challenge | Keygenme-py |
| Category | Reverse Engineering |
| Difficulty | Medium |
| Platform | CyLab Academy / picoCTF 2021 |
| Language | Python |

## Objective

Analyze the provided Python source code to understand how the license key is validated and reconstruct the correct key.

## Tools Used

- Kali Linux
- Python 3
- SHA-256 hashing
- Terminal

## Step 1 – Download the Challenge File

Downloaded `keygenme-trial.py` into the working directory.

```bash
mkdir -p ~/keygenme-py
cd ~/keygenme-py
```

## Step 2 – Analyze the Source Code

The source code contained the following important variables:

```python
username_trial = "MILLER"
bUsername_trial = b"MILLER"

key_part_static1_trial = "academy{1n_7h3_kk3y_of_"
key_part_dynamic1_trial = "xxxxxxxx"
key_part_static2_trial = "}"
```

The complete key follows this structure:

```text
academy{1n_7h3_kk3y_of_[8-character dynamic part]}
```

## Step 3 – Understand the SHA-256 Check

The `check_key()` function uses SHA-256 hashing of the username.

It checks eight characters from the resulting hash in this specific order:

```python
[4, 5, 3, 6, 2, 7, 1, 8]
```

Python uses zero-based indexing, meaning the first character has index `0`.

## Step 4 – Generate the SHA-256 Hash

Executed:

```bash
python3 -c "import hashlib; print(hashlib.sha256(b'MILLER').hexdigest())"
```

Output:

```text
734d9ef4ba0977dafd63c59bd4ceb0413f7559edf6347c8405f8feabdecb01d0
```

## Step 5 – Extract the Dynamic Characters

Selected the required characters using the indexes from the source code:

| Index | Character |
|---:|:---:|
| 4 | 9 |
| 5 | e |
| 3 | d |
| 6 | f |
| 2 | 4 |
| 7 | 4 |
| 1 | 3 |
| 8 | b |

Dynamic part:

```text
9edf443b
```

## Step 6 – Reconstruct the License Key

Combined the static prefix, dynamic part, and closing brace.

```text
academy{1n_7h3_kk3y_of_9edf443b}
```

## Technical Concepts Learned

- Python source-code analysis
- Reverse engineering fundamentals
- SHA-256 hashing
- Python byte strings
- Zero-based string indexing
- Reconstructing a key from validation logic

## Security Lessons

- Hardcoded usernames and predictable key-generation logic can weaken license validation.
- Hashing a username does not make a key-generation scheme secure.
- Source-code analysis can reveal how an application validates user input.

## Final Flag / Key

```text
academy{1n_7h3_kk3y_of_9edf443b}
```

## Conclusion

Successfully analyzed the Python validation logic, generated the SHA-256 hash of the trial username, extracted the required characters, and reconstructed the license key.
