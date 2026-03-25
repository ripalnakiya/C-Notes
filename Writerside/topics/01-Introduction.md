# Introduction
<show-structure depth="2"/>

## Compiling a C file

```shell
gcc -o source source.c
./source
```

- Breakdown:
    - **`gcc`**: The GNU C compiler.
    - **`source.cpp`**: Your C file.
    - **`-o program`**: Output flag. “Name the final executable `source` instead of the default `a.out`”

- So this command:
    - ➡️ Compiles `source.c`
    - ➡️ Produces an executable file named `source`

If you skip `-o source`:

```shell
gcc source.c
./a.out
```

## Comparison with C++

### 1. Don't have OOP features

- C has:
  - No classes
  - No inheritance
  - No polymorphism

- You want OOP? Congrats, you fake it using:
- `struct`
- function pointers

### 2. `printf` instead of `std::cout`

```C
printf("%d", x);

printf("%d", 3.14); // compiles fine, prints garbage
```

### 3. No references. Only pointers.

### 4. Memory management

No `new/delete`.

Just:

```C
malloc()
free()
```

And if you forget `free()`: **memory leak**

### 5. No function overloading

```C++
// C++
int add(int, int);
float add(float, float);
```

```C
// C
int add_int(int, int);
float add_float(float, float);
```

> Function pointers can be used as "DIY Polymorphism"
> 
> [Refer C++ Docs](https://ripalnakiya.github.io/Cpp-Notes/07-functions.html#pointer-to-a-function)
{style="note"}

### 6. Header files are… primitive

No namespaces. No fancy modules.

### 7. Strings are just char arrays

```C
char str[10] = "hello";
```

### 8. No exceptions

No `try/catch`. Handle potential crashes manually.

```C
if (ptr == NULL) {
    // handle error
}
```
