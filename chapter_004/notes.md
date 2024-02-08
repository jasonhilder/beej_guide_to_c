# FUNCTIONS

## 4.1 ( passing by value )

Lots of things in C are easier to understand if you know that the parameter is a copy of the argument, not the argument itself.

```
#include <stdio.h>

void increment(int a)
{
    a++;
}

int main(void)
{
    int i = 10;

    increment(i);

    printf("i == %d\n", i);  
}
```

int a is COPIED, not the original, it does get incremented inside the function but on completion all local variables are discarded.

The print then runs i which has remained 10.

To get around this we pass by reference, but in any case even in the passing by reference without exception,
everything passed to a function	is copied into its corresponding parameter.

## 4.2 ( Function prototypes )

Typically we need to define a function before using it otherwise the compile wont be aware of it at that point of compilation.

You can notify the compiler in advance that you’ll be using a function of a certain type that has a certain parameter list. 
That way the function can be defined anywhere (even in a different file), as long as the function prototype has been declared before you call that function.

```
#include <stdio.h>

int foo(void);  // This is the prototype!

int main(void)
{
    int i;
    
    // We can call foo() here before it's definition because the
    // prototype has already been declared, above!

    i = foo();
    
    printf("%d\n", i);  // 3490
}

int foo(void)  // This is the definition, just like the prototype!
{
    return 3490;
}
```

If you don’t declare your function before you use it, you’re performing something called an implicit declaration.

Notice we are calling printf without defining or declaring a prototype, this is because its included in the header file.

## 4.3 Empty Parameter List

Always use void to indicate that a function takes no parameters. There’s never a reason to skip this in modern code.

```
void foo();
void foo(void);  // Not the same!
    
```

Leaving void out of the prototype indicates to the compiler that there is no additional information about the parameters to the function. 
It effectively turns off all that type checking.

With a prototype definitely use void when you have an empty parameter list.

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