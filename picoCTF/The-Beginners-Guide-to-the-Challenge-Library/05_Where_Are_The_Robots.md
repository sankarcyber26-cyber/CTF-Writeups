# Challenge 05 – Where Are The Robots?

## Challenge Information
- **Platform:** picoCTF 2019
- **Challenge Name:** Where Are The Robots?
- **Category:** Web Exploitation
- **Difficulty:** Easy
- **Challenge Number:** 05
- **Tool Used:** Kali Linux – Firefox Browser

## Challenge Description

Can you find the robots?

## Objective

Find the hidden webpage by inspecting the website's `robots.txt` file and retrieve the flag.

## Solution

### Step 1: Open the Challenge Website

Open the challenge website in Firefox:

```text
http://chatelaine.cylabacademy.net:26741
```

### Step 2: Find robots.txt

Open the following URL:

```text
http://chatelaine.cylabacademy.net:26741/robots.txt
```

### Step 3: Inspect robots.txt

The file displayed:

```text
User-agent: *
Disallow: /91ac7.html
```

The `Disallow` directive revealed a hidden webpage path.

### Step 4: Open the Hidden Page

Visit:

```text
http://chatelaine.cylabacademy.net:26741/91ac7.html
```

The hidden page revealed the flag.

## Final Flag

```text
academy{ca1cu1at1ng_Mach1n3s_91ac7}
```

## What I Learned

1. Learned about the `robots.txt` file.
2. Understood the purpose of the `User-agent` directive.
3. Learned how the `Disallow` directive works.
4. Practiced discovering hidden website paths.
5. Understood that robots.txt is not a security mechanism.

## Key Takeaway

The robots.txt file provides instructions to web crawlers. It may also reveal paths that should not be indexed, so it is useful to inspect during web reconnaissance.

**Challenge Status:** Solved ✅
