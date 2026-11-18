# 11 – Enhance!

## Challenge Information

| Field | Details |
|---|---|
| Challenge Name | Enhance! |
| Platform | CyLab Academy |
| Original Platform | picoCTF 2022 |
| Category | Forensics |
| Difficulty | Medium |
| File | `drawing.flag.svg` |

## Objective

Download the provided SVG image and inspect its contents to recover the hidden flag.

## Tools Used

- Kali Linux
- `wget`
- `file`
- `grep`
- `sed`
- Terminal

## Step 1 – Download the Challenge File

Created a working directory and downloaded the SVG file.

```bash
mkdir -p ~/enhance
cd ~/enhance

wget "https://challenge-files.cylabacademy.net/library/e64e2668a8f34ef7ddcbdd713ba52720a8804ff3a0914677983d29a4b48c3e6a/drawing.flag.svg"
```

Verified that the file was downloaded:

```bash
ls -lh
```

## Step 2 – Identify the File Type

Used the `file` command to identify the downloaded file.

```bash
file drawing.flag.svg
```

Output:

```text
drawing.flag.svg: SVG Scalable Vector Graphics image
```

The file was identified as an SVG image.

## Step 3 – Search for Hidden Text

Searched the SVG source for relevant keywords and text elements.

```bash
grep -nEi 'pico|academy|flag|text|tspan' drawing.flag.svg
```

The output revealed multiple `<tspan>` elements containing individual parts of the hidden text.

## Step 4 – Inspect the SVG Source

Displayed the relevant section of the SVG file.

```bash
sed -n '70,125p' drawing.flag.svg
```

The hidden text was split across multiple `<tspan>` elements:

```text
a
c
a
d
e
m
y { 3 n h 4 n
c 3 d _ 9 f 3 1 c 0 4 b }
```

By joining the characters in the correct order and removing the extra spaces, the flag was recovered.

## Technical Concepts Learned

- **SVG:** Scalable Vector Graphics is an XML-based image format.
- **XML Inspection:** SVG files can be inspected as text because they contain structured XML elements.
- **`grep`:** Searches files for matching text or patterns.
- **`sed`:** Displays or processes selected lines from a file.
- **`<text>` and `<tspan>`:** SVG elements used to store and organize text.
- **Forensics:** Examining file contents and metadata can reveal information that is not immediately visible when viewing an image.

## Security Lessons

- Never assume an image contains only visual information.
- Text and metadata can be embedded inside image formats such as SVG.
- Inspect suspicious or challenge-provided files using command-line tools.
- Hidden information may be split across multiple elements to make discovery harder.

## Final Flag

```text
academy{3nh4nc3d_9f31c04b}
```

## Conclusion

Successfully recovered the hidden flag by inspecting the SVG source code. Identified the embedded text using `grep`, examined the relevant XML elements using `sed`, and reconstructed the flag from multiple `<tspan>` elements.

**Challenge Status:** Solved (after successful platform submission).
