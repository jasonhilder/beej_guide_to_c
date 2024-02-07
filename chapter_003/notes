# VARIABLES & STATEMENTS

## 3.1

It’s said that “variables hold values”. But another way to think about it is that a variable is a human-readable name that refers to some data in memory.

You can think of memory as a big array of bytes. Data is stored in this “array”. 
If a number is larger than a single byte, it is stored in multiple bytes.
Because memory is like an array, each byte of memory can be referred to by its index. This index into memory is also called an address, or a location, or a pointer.

So a variable is a name for some data that’s stored in memory at some address.

## 3.1.2

C’s kinda picky about variable types, so a refresher is good.

The most basic:
Type						Example			C Type
Integer						3490			int
Floating point				3.14159			float35
Character (single)			'c'				char
String						"Hello, world!"	char *36

C makes an effort to convert automatically between most numeric types when you ask it to. 
But other than that, all conversions are manual, notably between string and numeric.

Uninitialized variables have indeterminate value37. 
They have to be initialized or else you must assume they contain some nonsense number.

## 3.1.3

Historically, C didn’t have a Boolean type, and some might argue it still doesn’t.

In C, 0 means “false”, and non-zero means “true”.

So 1 is true. And -37 is true. And 0 is false.

If you #include <stdbool.h>, you also get access to some symbolic names that might make things look more familiar.

#include <stdio.h>
#include <stdbool.h>

int main(void) {
    bool x = true;

    if (x) {
        printf("x is true!\n");
    }
}

## 3.2.3

Pre-and-Post Increment-and-Decrement

++i;        // Add one to i (pre-increment)
--i;        // Subtract one from i (pre-decrement)

With pre-increment and pre-decrement, the value of the variable is incremented or decremented before the expression is evaluated. 
Then the expression is evaluated with the new value.

With post-increment and post-decrement, the value of the expression is first computed with the value as-is, and then the value is incremented 
or decremented after the value of the expression has been determined.

You can actually embed them in expressions, like this:

i = 10;
j = 5 + i++;  // Compute 5 + i, _then_ increment i

printf("%d, %d\n", i, j);  // Prints 11, 15

Let’s compare this to the pre-increment operator:

i = 10;
j = 5 + ++i;  // Increment i, _then_ compute 5 + i

printf("%d, %d\n", i, j);  // Prints 11, 16

## 3.2.7

The sizeof operator tells you the size (in bytes) that a particular variable or data type uses in memory.

Since this computes the number of bytes needed to store a type, you might think it would return an int. 
Or… since the size can’t be negative, maybe an unsigned?

But it turns out C has a special type to represent the return value from sizeof. 
It’s size_t, pronounced “size tee”. 
All we know is that it’s an unsigned integer type that can hold the size in bytes of anything you can give to sizeof.

It’s important to note that sizeof is a compile-time operation. 
The result of the expression is determined entirely at compile-time, not at runtime.
