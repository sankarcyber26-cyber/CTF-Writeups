# Picker IV – CyLab Academy

## 1. Challenge Information

| Field | Details |
|---|---|
| Platform | CyLab Academy |
| Challenge Number | 15 |
| Challenge Name | Picker IV |
| Category | Binary Exploitation |
| Target | `xebec.cylabacademy.net` |
| Port | `47443` |
| Status | In Progress |

## 2. Objective

The objective was to identify the address of the hidden `win()` function and provide that address to the challenge application to redirect program execution.

## 3. Tools Used

- Kali Linux
- `file`
- `nm`
- `grep`
- Netcat (`nc`)

## 4. Exploitation Steps

### Step 1 – Download the Challenge Binary

Downloaded the provided `picker-IV` binary from the CyLab Academy challenge page.

### Step 2 – Identify the Binary Architecture

Executed:

```bash
file picker-IV
```

This command identifies the binary format and architecture.

### Step 3 – Locate the Hidden Function

Used the `nm` command to list symbols and locate the `win()` function.

```bash
nm -n picker-IV | grep " win"
```

Observed output:

```text
00000000004012a1 T win
```

The address of the hidden function was:

```text
0x4012a1
```

### Step 4 – Connect to the Remote Server

Connected using Netcat:

```bash
nc xebec.cylabacademy.net 47443
```

### Step 5 – Provide the Function Address

The challenge requested the address without the `0x` prefix.

Entered:

```text
4012a1
```

## 5. Flag

```text
Pending – Final flag not yet confirmed.
```

## 6. Security Concepts Learned

- Binary analysis
- Symbol enumeration
- Function address identification
- Control-flow manipulation
- Basic command-line binary inspection

## 7. Conclusion

Successfully identified the address of the hidden `win()` function using `nm` and submitted the address to the remote challenge.

The final flag retrieval still requires verification.

**Result: Partially Completed.**
