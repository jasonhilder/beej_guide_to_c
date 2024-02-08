## Arrays

C only barely has arrays! Arrays are just syntactic sugar in C—they’re actually all pointers and stuff deep down.

```
#include <stdio.h>

int main(void)
{
    int i;
    float f[4];  // Declare an array of 4 floats

    f[0] = 3.14159;  // Indexing starts at 0, of course.
    f[1] = 1.41421;
    f[2] = 1.61803;
    f[3] = 2.71828;

    // Print them all out:

    for (i = 0; i < 4; i++) {
        printf("%f\n", f[i]);
    }
}
  
```

## 6.2 ( Getting the Length of an Array )

Kinda can't. There is a trick only possible when in the same scope of the array declaration.

You can take the sizeof the array and divide it by the size of the type it has (the size of each element).

if we have an array of int x[12] we can do the following:

```
int x[12];  // 12 ints

printf("%zu\n", sizeof x);     // 48 total bytes
printf("%zu\n", sizeof(int));  // 4 bytes per int

printf("%zu\n", sizeof x / sizeof(int));  // 48/4 = 12 ints! 

```

But you cannot use it in a function that the array has been passed to. In C it only passes a pointer to the first element.

## 6.4 ( Out of Bounds )

C doesn’t stop you from accessing arrays out of bounds. It might not even warn you.

We can keep printing in a for loop and it will print random (undefined behavior) numbers.

Short version: don’t do anything that causes undefined behavior. Ever.

## 6.6.1