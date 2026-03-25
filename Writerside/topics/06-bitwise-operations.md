# Bitwise Operations

🧠 What are Bitwise Operators?

They operate on individual bits (0/1) of integers.

Example:
```C
5  = 00000101
3  = 00000011
```

## AND `&`

Each bit is 1 only if both bits are 1.

```C
5 & 3 = 1

  0101
& 0011
= 0001
```

**Use:** Masking (keep certain bits, remove others)

## OR `|`

Bit is 1 if at least one is 1.

```C
5 | 3 = 7

  0101
| 0011
= 0111
```

**Use:** Setting bits

## XOR `^`

Bit is 1 if bits are different.

```C
5 ^ 3 = 6

  0101
^ 0011
= 0110
```

**Use:** Toggle bits, Tricks like swapping numbers

## NOT `~`

Flips all bits.

```C
~5 = -6   // (in 2’s complement)
```

**Why negative?** Because C uses 2’s complement representation.

## Left Shift `<<`

Shifts bits left (adds zeros on right)

```C
5 << 1 = 10

0101 → 1010
```
Equivalent:

```C
x << n = x * (2^n)
```

## Right Shift `>>`

Shifts bits right

```C
5 >> 1 = 2

0101 → 0010
```

Equivalent:

```C
x >> n = x / (2^n)
```

## 🎭 Bit Masking

Bit masking = using bits to store multiple boolean flags inside one integer

```C
// Instead of:
bool isAdmin;
bool isVerified;
bool isPremium;

// You store:
int user = 0;
```

### 🔹 Set a bit

```C
user = user | (1 << 2);  // set 3rd bit
```

### 🔹 Clear a bit

```C
user = user & ~(1 << 2);
```

### 🔹 Toggle a bit

```C
user = user ^ (1 << 2);
```

### 🔹 Check a bit

```C
if (user & (1 << 2)) {
    // bit is ON
}
```

### Example:

```C
int flags = 0;

flags |= (1 << 0); // enable feature A
flags |= (1 << 2); // enable feature C

// Check feature C
if (flags & (1 << 2)) {
    printf("Feature C enabled");
}
```

## 🧩 Common Bit Tricks

### 1. Check even/odd

```C
if (x & 1) → odd
else → even
```

### 2. Check power of 2

```C
if (x > 0 && (x & (x - 1)) == 0)
```

**Why?** Power of 2 has only one bit set

### 3. Count set bits (Brian Kernighan’s Algorithm)

```C
int count = 0;
while (x) {
    x = x & (x - 1);
    count++;
}
```

### 4. Swap without temp

```C
a = a ^ b;
b = a ^ b;
a = a ^ b;
```

### 5. Get lowest set bit

```C
x & (-x)
```

## 🚀 LeetCode

### 1. Find element that appears once

```C
int singleNumber(int* nums, int n) {
    int res = 0;
    for (int i = 0; i < n; i++) {
        res = res ^ nums[i];
    }
    return res;
}
```

- Why it works:
  - a ^ a = 0
  - 0 ^ b = b

Everything cancels out except the unique number.

### 2. Generates all subsets using Bitmasking

```C
for (int mask = 0; mask < (1 << n); mask++) {
    for (int i = 0; i < n; i++) {
        if (mask & (1 << i)) {
            printf("%d ", nums[i]);
        }
    }
}
```

### 3. Missing Number

```C
int missingNumber(int* nums, int n) {
    int xor = n;
    for (int i = 0; i < n; i++) {
        xor ^= i ^ nums[i];
    }
    return xor;
}
```
