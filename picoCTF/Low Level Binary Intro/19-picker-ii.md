# Picker II – CyLab Academy

## Challenge Information

| Field | Details |
|---|---|
| Platform | CyLab Academy |
| Challenge Number | 19 |
| Challenge Name | Picker II |
| Category | Binary Exploitation |
| Target | `xebec.cylabacademy.net` |
| Port | `37659` |
| Status | Completed |

## Objective

The objective of this challenge was to bypass the application's input filtering mechanism and execute the hidden `win()` function to retrieve the flag.

## Tools Used

- Kali Linux
- Netcat (`nc`)
- Python
- Hexadecimal decoding

## Exploitation Process

### Step 1: Connect to the Challenge Server

Connected to the remote challenge server using Netcat.

```bash
nc xebec.cylabacademy.net 37659
```

### Step 2: Analyze the Input Filter

The application restricted certain input patterns to prevent users from accessing protected functionality.

The goal was to bypass this restriction without directly entering the restricted function name.

### Step 3: Bypass the Filter

Used dynamic function lookup to construct the function name.

Payload:

```python
globals()['w'+'in']()
```

**Payload Explanation:**

- `globals()` accesses the global namespace.
- `'w'+'in'` dynamically constructs the string `win`.
- `globals()['w'+'in']` retrieves the function named `win`.
- `()` executes the retrieved function.

This technique bypassed the input filter and invoked the hidden function.

### Step 4: Retrieve the Flag

The challenge returned the flag in hexadecimal representation.

The hexadecimal output was decoded into readable text.

## Flag

```text
academy{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_bd7d479d}
```

## Security Concepts Learned

1. Input filtering and its limitations.
2. Dynamic function lookup in Python.
3. Global namespace access using `globals()`.
4. Filter bypass techniques.
5. Risks of exposing sensitive functions to user-controlled input.

## Security Recommendations

- Avoid relying only on blacklist-based input filtering.
- Use strict allowlists for accepted user inputs.
- Never expose sensitive functions through unrestricted dynamic lookup.
- Apply proper validation and access control.

## Conclusion

Successfully bypassed the application's input filtering mechanism using dynamic function lookup and executed the hidden `win()` function.

The challenge demonstrated how weak input filtering can expose sensitive application functionality.

**Result: Successfully completed.**
