# Tab, Tab, Attack - picoCTF

## Category

General Skills

## Difficulty

Easy

## Description

The challenge provides a ZIP file called `Addadshashanammu.zip`.

The hint says that after unzipping, the challenge can be solved using 11 button presses, mostly the Tab key.

## Approach

1. Download the ZIP file:

```text
Addadshashanammu.zip
```

2. Extract the ZIP file using:

```bash
unzip Addadshashanammu.zip
```

3. Use `ls` to view the extracted directory:

```bash
ls
```

4. The extracted files contain a long directory structure.

5. Use `cd` together with **Tab completion** to navigate through the directories without typing the long names manually.

Example:

```bash
cd A<TAB>
```

6. Continue using Tab completion until reaching the final file.

## Flag

```text
picoCTF{l3v3l_up!_t4k3_4_r35t!_fc588427}
```

## Learning

* `unzip`
* `ls`
* `cd`
* Terminal Tab completion
* Navigating long directory structures
* Basic Linux command-line skills
