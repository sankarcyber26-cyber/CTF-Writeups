# Challenge 3 – Super SSH

## Challenge Information
- **Platform:** picoCTF 2024
- **Challenge Name:** Super SSH
- **Category:** General Skills
- **Difficulty:** Easy
- **Challenge Number:** 3
- **Tool Used:** Kali Linux Terminal
- **Protocol:** SSH

## Challenge Description

Connect to the remote machine using SSH as the user `ctf-player` on port `38810` and retrieve the flag.

## Solution

### Step 1: Connect to the SSH Server

Open Kali Linux Terminal and execute:

```bash
ssh -p 38810 ctf-player@xebec.cylabacademy.net
```

### Step 2: Accept the Fingerprint

When prompted, type:

```text
yes
```

### Step 3: Enter the Password

```text
fd7746b4
```

Note: The password will not be visible while typing.

### Step 4: Find the Flag

After successful login, list the files:

```bash
ls -la
```

Read the flag file using:

```bash
cat <filename>
```

Replace `<filename>` with the actual filename displayed by the `ls` command.

## Flag

```text
academy{YOUR_FLAG_HERE}
```

## What I Learned

1. Learned how SSH works.
2. Practiced connecting to a remote Linux server.
3. Learned SSH username and hostname syntax.
4. Learned how to specify a custom SSH port using `-p`.
5. Practiced accepting SSH fingerprints and password authentication.
6. Learned to inspect remote files using Linux commands.

## Key Takeaway

SSH (Secure Shell) provides secure remote access to another computer over a network.

**Challenge Status:** Solved after retrieving the flag.
