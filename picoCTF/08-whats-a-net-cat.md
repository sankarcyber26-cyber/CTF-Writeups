# What's a net cat? - picoCTF

## Category

General Skills

## Difficulty

Easy

## Description

The challenge provides a program that can be accessed using netcat:

```bash
nc wily-courier.picoctf.net 65385
```

The program does not speak English, so we need to decode the data it sends.

## Approach

1. Connect to the server using netcat:

```bash
nc wily-courier.picoctf.net 65385
```

2. The server returns decimal numbers such as:

```text
112
105
99
111
67
84
70
123
...
125
```

3. These numbers are ASCII decimal values.

For example:

```text
112 → p
105 → i
99  → c
111 → o
67  → C
84  → T
70  → F
```

4. Convert all the ASCII decimal values into characters.

5. The decoded text gives the flag.

## Flag

```text
picoCTF{g00d_k1tty!_n1c3_k1tty!_195fe}
```

## Learning

* Netcat (`nc`)
* ASCII encoding
* Decimal ASCII to text conversion
* Connecting to a remote service
* Basic CTF enumeration and interaction
