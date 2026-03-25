# Output Formatting
<show-structure depth="2"/>

Syntax:

```C
printf("format string", arguments...);

printf("Age: %d", 25);
```

## Common Format Specifiers

| Specifier | Meaning           |
|-----------|-------------------|
| `%d`      | int               |
| `%f`      | float/double      |
| `%c`      | char              |
| `%s`      | string (char*)    |
| `%p`      | pointer (address) |
| `%x`      | hex (lowercase)   |
| `%X`      | hex (uppercase)   |
| `%o`      | octal             |

```C
printf("%d %f %c %s", 10, 3.14, 'A', "hello");

int x = 10;
printf("%p", &x);
```
