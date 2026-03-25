# Pointers
<show-structure depth="2"/>

```C
int x = 10;
int *p = &x;
printf("%d", *p); // 10
```

## 🔥 Dynamic allocation

```C
#include <stdlib.h>

int *p = (int *) malloc(sizeof(int));

*p = 42;
```

- allocates memory on heap
- returns void* (generic pointer)
- you cast it (optional in C, but people still do it)

**⚠️ VERY IMPORTANT:**

```C
if (p == NULL) {
    // allocation failed
}
```

## 🧼 `free`

```C
free(p);
```

```C
free(p);
free(p); // 💀 undefined behavior
```

## 🧨 `malloc` does NOT initialize memory

```C
int *p = malloc(sizeof(int));
printf("%d", *p); // garbage value
```

```C
int *p = (int *) malloc(5 * sizeof(int));
```

- Allocates memory
- Does NOT initialize it
- Memory contains garbage values

> Takes only **one** argument
{style="note"}

### 🧊 `calloc`

```C
int *p = (int *) calloc(5, sizeof(int));
```

- Allocates memory for 5 integers
- **Initializes everything to 0**

> Takes **two** arguments
{style="note"}

## 🔄 `realloc` (resizing memory)

```C
p = realloc(p, 10 * sizeof(int));
```

- resizes previously allocated memory
- may move memory to a new location

So always:

```C
int *temp = realloc(p, new_size);
if (temp != NULL) {
    p = temp;
}
```

Because if `realloc` fails, your original pointer is still valid…

## 📦 Arrays using pointers

```C
int *arr = malloc(5 * sizeof(int));

arr[0] = 10;
arr[1] = 20;
// OR
*(arr + 1) = 20;
```

## 🧠 Pointer arithmetic

```C
int *p = arr;
p++; // moves to next int (not +1 byte)
```

C automatically adjusts by `sizeof(type)`.

## 🏗️ Struct allocation

```C
struct Person {
    int age;
};

struct Person *p = malloc(sizeof(struct Person));
p->age = 25;
```

## 🧵 Strings (char pointers)

```C
char *str = malloc(6 * sizeof(char));
strcpy(str, "Hello");
```

**Important:** allocate space for `\0`

```C
"Hello" = 5 chars + 1 null = 6
```

## 🧨 Dangling pointers

```C
int *p = malloc(sizeof(int));
free(p);

printf("%d", *p); // 💀 Pointer still exists… memory doesn’t.
```

Fix:

```C
free(p);
p = NULL;
```

Now at least it fails safely.

## ⚡ Stack vs Heap

Stack

```C
int x = 10;
```

- automatic
- fast
- destroyed when function ends

```C
int *p = malloc(sizeof(int));
```

- manual
- slower
- YOU must free it

## 🧪 Common mistakes

```C
// ❌ Forgetting `sizeof`
int *p = malloc(5); // wrong

// ✅ Correct
int *p = malloc(5 * sizeof(int));
```

```C
// ❌ Using uninitialized pointer
int *p;
*p = 10; // 💀
```

```C
// ❌ Memory leak
p = malloc(...);
p = malloc(...); // lost reference to old memory
```
