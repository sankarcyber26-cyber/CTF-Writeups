# PicoCTF — Obedient Cat

## Challenge Information

- **Platform:** PicoCTF
- **Challenge Name:** Obedient Cat
- **Category:** General Skills
- **Difficulty:** Easy
- **Tools Used:** Kali Linux, Linux Terminal

## Objective

Retrieve the flag from the provided challenge file using basic Linux command-line utilities.

## Methodology

### Step 1: Download the Challenge File

Downloaded the file provided by the challenge using `wget`.

```bash
wget "<challenge-file-url>"
```

*Note: Replace the placeholder with the actual URL provided by PicoCTF.*

### Step 2: Identify the Downloaded File

Listed the files in the current working directory to identify the downloaded challenge file.

```bash
ls -la
```

### Step 3: Read the File Contents

Used the `cat` command to display the contents of the downloaded file.

```bash
cat <filename>
```

Replaced `<filename>` with the actual name of the downloaded file.

### Step 4: Retrieve the Flag

The file contents revealed the challenge flag. No complex exploitation was required.

## Flag

```text
<INSERT_ACTUAL_FLAG_HERE>
```

## Key Takeaways

- Practiced downloading files using `wget`.
- Used `ls -la` to inspect directory contents.
- Used `cat` to read a file from the Linux terminal.
- Understood how to retrieve a flag from a provided file.

## Conclusion

The Obedient Cat challenge reinforced fundamental Linux command-line skills and demonstrated how to inspect a provided file to retrieve a CTF flag.

---

**Disclaimer:** This write-up documents activity performed within the authorized PicoCTF challenge environment.
