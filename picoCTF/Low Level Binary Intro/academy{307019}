# CyLab Academy — GDB Baby Step 2

## Challenge Information

- **Platform:** CyLab Security Academy
- **Learning Path:** Low Level Binary Intro
- **Challenge Name:** GDB Baby Step 2
- **Category:** Reverse Engineering
- **Difficulty:** Medium
- **Architecture:** x86_64
- **Tools Used:** Kali Linux, GDB

## Objective

Determine the value stored in the `EAX` register at the end of the `main` function by analyzing the assembly instructions and calculating the loop's result.

## Methodology

### Step 1: Initialize the Variables

The program initializes three local variables:

```asm
movl $0x1e0da, -0x4(%rbp)
movl $0x25f, -0xc(%rbp)
movl $0x0, -0x8(%rbp)
```

Their decimal values are:

- Initial value: `0x1e0da` = `123098`
- Loop limit: `0x25f` = `607`
- Loop counter: `0`

### Step 2: Analyze the Loop

The loop performs the following operations:

```asm
mov -0x8(%rbp), %eax
add %eax, -0x4(%rbp)
addl $0x1, -0x8(%rbp)
```

The current counter is added to the initial value, and the counter is incremented by one.

### Step 3: Determine the Loop Iterations

The loop condition compares the counter with `607` and repeats while the counter is less than the limit.

Therefore, the counter values added are `0` through `606`.

### Step 4: Calculate the Final Value

The sum of the counter values is calculated using the arithmetic series formula:

\[
\frac{606\times607}{2}=183921
\]

Adding this to the initial value:

\[
123098+183921=307019
\]

### Step 5: Identify the Final EAX Value

The final instruction is:

```asm
mov -0x4(%rbp), %eax
```

This loads the calculated result into `EAX`.

## Flag

```text
academy{307019}
```

## Key Takeaways

- Practiced analyzing loops in x86_64 assembly.
- Learned how loop counters affect a variable's value.
- Used an arithmetic series to calculate repeated additions.
- Identified how the final result is returned through `EAX`.

## Conclusion

This challenge demonstrated how to trace loop execution in assembly and calculate the final register value without executing every iteration manually.
