# Picker III – CyLab Academy

## 1. Challenge Information

| Field | Details |
|---|---|
| Platform | CyLab Academy |
| Challenge Number | 14 |
| Challenge Name | Picker III |
| Category | Binary Exploitation |
| Difficulty | Beginner |
| Target | `xebec.cylabacademy.net` |
| Status | Completed |

## 2. Objective

The objective of this challenge was to manipulate the program's `func_table` variable and execute the hidden `win()` function to retrieve the challenge flag.

## 3. Tools Used

- Kali Linux
- CyLab Academy challenge environment
- Python syntax
- Hexadecimal decoding

## 4. Challenge Analysis

The application contained a function table named `func_table`.

The challenge allowed interaction with program variables through the `write_variable` functionality.

The security weakness was that the user could modify a variable that influenced which function the application executed.

## 5. Exploitation Steps

### Step 1 – Access the Challenge

Opened the Picker III challenge in the CyLab Academy environment.

### Step 2 – Identify the Target Variable

The important variable used in the challenge was:

```python
func_table
```

This variable influenced the application's function-selection mechanism.

### Step 3 – Modify the Function Table

Used the `write_variable` functionality to replace the existing function table value.

Payload:

```python
'win                             ' + ' '*96
```

**Payload Explanation:**

- `'win'` places the target function name at the beginning.
- The spaces provide padding.
- `' '*96` adds additional padding to the replacement string.
- The modified value changes the function-selection behavior.

### Step 4 – Execute the Hidden Function

After modifying `func_table`, selected option:

```text
1
```

The application then used the modified function table to invoke the hidden `win()` function.

### Step 5 – Retrieve the Flag

The challenge returned the flag in hexadecimal representation.

Decoded the hexadecimal output to obtain the original flag.

## 6. Flag

```text
academy{7h15_15_wh47_w3_g37_w17h_u53r5_1n_ch4rg3_948e866e}
```

## 7. Vulnerability and Security Concepts

- User-controlled variable modification
- Function table manipulation
- Dynamic function selection
- Input validation weaknesses
- Application control-flow manipulation

## 8. Security Recommendations

1. Prevent untrusted users from modifying sensitive program variables.
2. Validate user input before using it in program execution.
3. Restrict access to sensitive functions.
4. Avoid unsafe dynamic function-selection mechanisms.
5. Apply proper access control to sensitive operations.

## 9. Conclusion

Successfully modified the `func_table` variable using the `write_variable` functionality and selected option `1` to execute the hidden `win()` function.

The challenge demonstrated how improper control over application variables can affect program execution and expose sensitive functionality.

**Final Result: Successfully Completed.**
