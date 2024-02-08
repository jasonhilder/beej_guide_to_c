# POINTERS - COWER IN FEAR

## 5.1 ( Memory and Variables )

To make memory easy to cope with, each byte of memory is identified by an integer. 
These integers increase sequentially as you move up through memory. 
You can think of it as a bunch of numbered boxes, where each box holds a byte of data.
The number that represents each box is called its address.

Not all data types use just a byte, an int is often four bytes, as is a float, but it really depends on the system. 
You can use the sizeof operator to determine how many bytes of memory a certain type uses.

The bytes that make up the data are always adjacent to one another in memory, however their order is dependant on the
platform (big/small endian)

So, a pointer is a variable that holds an address.

or a Index into memory (if you’re thinking of memory like a big array)
or an Address
or a Location

This means that all these things mean the same thing, i.e. a number that represents a point in memory:

Consider;
You can have a house with certain qualities, yard, metal roof, solar, etc. 
Or you could have the address of that house. 
The address isn’t the same as the house itself. 
One’s a full-blown house, and the other is just a few lines of text. 
But the address of the house is a pointer to that house. 
It’s not the house itself, but it tells you where to find it.

It’s not the data variable itself, but, like with a house address, it tells us where to find it.

To get the address of a pointer we can use the address-of operator (which happens to be an ampersand: “&”).


## 5.2 ( Pointer Types )

We can assign variables to be (store) pointers, with a * before the variable name.

```
int i;
int *p;

```
That is a variable that is a pointer type, and it can point to other ints.
When you do an assignment into a pointer variable, the type of the right hand side of the assignment has to be the same type as the pointer variable.

When you take the address-of a variable, the resultant type is a pointer to that variable type, so assignments like the following are perfect:

```
int i;
int *p;  // p is a pointer, but is uninitialized and points to garbage

p = &i;
	
```

## 5.3 ( Derefencing )

Since a pointer variable can be thought of as referring to another variable by pointing to it so "a pointer is just a reference".

Being roughly a reference we can use the original variable through the pointer by dereferencing the pointer.

We can dereference a pointer with the dereference operator. 
It’s actually called the indirection operator, because you’re accessing values indirectly via the pointer.

It is a * but not to be confused with the pointer declaration, they are the same character but have different meanings in different contexts.

```
#include <stdio.h>

int main(void)
{
    int i;
    int *p;  // this is NOT a dereference--this is a type "int*"

    p = &i;  // p now points to i, p holds address of i

    i = 10;  // i is now 10
    *p = 20; // the thing p points to (namely i!) is now 20!!

    printf("i is %d\n", i);   // prints "20"
    printf("i is %d\n", *p);  // "20"! dereference-p is the same as i!
}
  
```
The * in *p = 20; tells us to use the object of the pointer instead of the pointer itself.

In this way, we have turned *p into an alias of sorts for i.

## 5.4 ( Passing pointers as arguments )

The real power of pointers comes into play when you start passing them to functions.

As before func arguments get *copied* into parameters and we can mutate the local copies.

So if we use a pointer as an argument we can get a copy of the address to a previously setup variable.
Inside the function we can dereference to its original value

```
#include <stdio.h>

void increment(int *p)  // note that it accepts a pointer to an int
{
    *p = *p + 1;        // add one to the thing p points to
}

int main(void)
{
    int i = 10;
    int *j = &i;  // note the address-of; turns it into a pointer to i

    printf("i is %d\n", i);        // prints "10"
    printf("i is also %d\n", *j);  // prints "10"

    increment(j);                  // j is an int*--to i

    printf("i is %d\n", i);        // prints "11"!
} 

```
The above example is often more concisely written in the call just by using address-of right in the argument list:

```
printf("i is %d\n", i);  // prints "10"
increment(&i);
printf("i is %d\n", i);  // prints "11"!

```

## 5.5 ( The NULL Pointer )

Any pointer variable of any pointer type can be set to a special value called NULL. This indicates that this pointer doesn’t point to anything.

Since it doesn’t point to a value, dereferencing it is undefined behavior, and probably will result in a crash

The NULL pointer is a good sentinel value50 and general indicator that a pointer hasn’t yet been initialized.
