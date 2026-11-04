# Challenge 04 – Insp3ct0r

## Challenge Information
- **Platform:** picoCTF 2019
- **Challenge Name:** Insp3ct0r
- **Category:** Web Exploitation
- **Difficulty:** Easy
- **Challenge Number:** 04
- **Tools Used:** Firefox Browser, Developer Tools, View Page Source

## Challenge Description

Kishor Balan tipped us off that the website code may need inspection.

Website: http://xebec.cylabacademy.net:48789

## Objective

Inspect the HTML, CSS, and JavaScript source files to find three parts of the flag.

## Solution

### Step 1: Inspect HTML Source

1. Open the challenge website.
2. Press `Ctrl + U`.
3. Search for `flag` using `Ctrl + F`.
4. Found the first part:

```text
academy{tru3_d3
```

### Step 2: Inspect CSS Source

1. Open `mycss.css`.
2. Search for `flag`.
3. Found the second part:

```text
t3ct1ve_0r_ju5t
```

### Step 3: Inspect JavaScript Source

1. Open `myjs.js`.
2. Search for `flag`.
3. Found the third part:

```text
_lucky?6679a3ba}
```

## Final Flag

```text
academy{tru3_d3t3ct1ve_0r_ju5t_lucky?6679a3ba}
```

## What I Learned

1. Learned how to inspect HTML source code.
2. Understood how CSS files are linked to HTML.
3. Learned how JavaScript files are included in a website.
4. Practiced finding hidden information in source code comments.
5. Understood the basics of web inspection.

## Key Takeaway

Website source code can contain useful information. Inspecting HTML, CSS, and JavaScript is an important first step in web security testing.

**Challenge Status:** Solved
