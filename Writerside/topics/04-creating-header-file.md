# Creating Header file

- A header file contains:
  - function declarations
  - macros
  - typedefs
  - struct definitions

**NOT actual implementations.**

## Create `.h` file

📄 `math_utils.h`

```C
#ifndef MATH_UTILS_H    // It is a Include guard
#define MATH_UTILS_H

int add(int a, int b);
int subtract(int a, int b);

#endif
```

## Create implementation file

📄 `math_utils.c`

```C
#include "math_utils.h"

int add(int a, int b) {
    return a + b;
}

int subtract(int a, int b) {
    return a - b;
}
```

This is where the real work happens.

**Why include the header in `.c` too?**
Because it ensures function signatures match.

## Use it in main

📄 `main.c`

```C
#include <stdio.h>
#include "math_utils.h"

int main() {
    printf("%d\n", add(5, 3));
    printf("%d\n", subtract(5, 3));
    return 0;
}
```

- Notice:
  - `""` for your own headers
  - `<>` for system headers

## Compile everything together

```shell
gcc main.c math_utils.c -o app
```

## Theory

Header files are copied into your code by preprocessor.

So:

```C
#include "math_utils.h"
```

**≈ literally pastes content there**

- That’s why:
  - guards are needed
  - no function definitions in headers

## 🧠 Final mental model

- Think of it like:
  - `.h` → contract / promise
  - `.c` → actual work
