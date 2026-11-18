# 12 – Vault Door Training

## Challenge Information

| Field | Details |
|---|---|
| Challenge Name | Vault Door Training |
| Platform | CyLab Academy |
| Original Platform | picoCTF 2019 |
| Category | Reverse Engineering |
| Difficulty | Easy |
| Language | Java |
| Source File | `VaultDoorTraining.java` |

## Objective

Inspect the provided Java source code to identify the hardcoded password and recover the vault flag.

## Tools Used

- Kali Linux
- `wget`
- `cat`
- Java source code inspection

## Step 1 – Download the Source Code

Created a working directory and downloaded the Java source file.

```bash
mkdir -p ~/vault-door-training
cd ~/vault-door-training

wget "https://challenge-files.cylabacademy.net/library/080a285021cd4d6edaff96f54c7eba477b4f450b778c0c129297bf51bbd3d3c8/VaultDoorTraining.java"
```

Verified the downloaded file:

```bash
ls -lh
```

## Step 2 – Inspect the Java Source Code

Displayed the source code:

```bash
cat VaultDoorTraining.java
```

The program contains a `main()` method and a `checkPassword()` method.

## Step 3 – Understand the Password Validation

The important code was:

```java
public boolean checkPassword(String password) {
    return password.equals("w4rm1ng_Up_w1tH_jAv4_1633b42d7f1");
}
```

This method compares the supplied password with a hardcoded string.

- `equals()` compares two strings.
- If both strings match, the method returns `true`.
- Otherwise, it returns `false`.

## Step 4 – Understand the Input Processing

The following line removes the flag prefix and closing brace:

```java
String input = userInput.substring("academy{".length(),userInput.length()-1);
```

For example, an input in the format:

```text
academy{password}
```

is converted into:

```text
password
```

The extracted value is then passed to `checkPassword()`.

## Step 5 – Recover the Flag

The hardcoded password was:

```text
w4rm1ng_Up_w1tH_jAv4_1633b42d7f1
```

The challenge flag format is `academy{...}`.

## Technical Concepts Learned

- **Source Code Analysis:** Reading application source code to understand its internal logic.
- **Hardcoded Credentials:** Passwords stored directly inside source code can be exposed if the code is accessed.
- **Java String Comparison:** The `equals()` method checks whether two strings contain the same characters.
- **Substring:** The `substring()` method extracts part of a string using character positions.
- **Reverse Engineering:** Understanding program behavior by examining its source code.

## Security Lessons

- Never store passwords or secrets directly in source code.
- Source code exposure can reveal hardcoded credentials.
- Sensitive credentials should be stored securely using appropriate secret-management mechanisms.
- Authentication systems should use secure password hashing rather than plain-text password comparisons.

## Final Flag

```text
academy{w4rm1ng_Up_w1tH_jAv4_1633b42d7f1}
```

## Conclusion

Successfully identified the hardcoded password by inspecting the Java source code. Understood how the application extracts the password from the input and validates it using the `equals()` method.

**Challenge Status:** Solved after successful platform submission.
