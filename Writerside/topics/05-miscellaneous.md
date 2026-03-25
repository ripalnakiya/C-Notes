# Miscellaneous

## Buffer overflow with strings

```C
char str[5] = "Hello"; // 💀 overflow
```

## Static keyword

```C
static int x = 0;
```

**Inside function:** value persists across calls

**Inside file:** limits scope to that file

Same keyword. Different meanings.

## const is not as strict as C++

- C’s const is:
  - compile-time restriction
  - not guaranteed runtime protection

```C
const int x = 10;

int *p = (int *)&x;
*p = 20;

printf("%d", x);

// Maybe prints 20
// Maybe prints 10
```
