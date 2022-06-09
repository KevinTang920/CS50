# Lecture 2
## Compiling
- make is actually just a program that calls `clang`, a compiler named for the "C language".
- can compile source code, hello.c, directly by running the command `clang hello.c` in the terminal:
```
$ clang hello.c
$
```
- Nothing seems to happen, which means there were no errors. And if we run list, with `ls`, we see an `a.out` file in our directory. The filename is just the default for clang's output, and we can run it:
```
$ ./a.out
hello, world
```
- We can add a command-line argument, or an input to a program on the command-line as extra words after the program's name. We can run `clang -o hello hello.c`, where `clang` is the name of the program, and `-o hello` and `hello.c` are additional arguments. We're telling `clang` to use `hello` as the output filename, and use `hello.c` as the source code. Now, we can see `hello` being created as output.

## Debugging
- step over. run the next line.
- step into. Let us go into the function called on that line

## Memory

- 1 byte = 8 bits
  - bool, 1 byte
  - char, 1 byte
  - double, 8 bytes
  - float, 4 bytes
  - int, 4 bytes
  - long, 8 bytes
  - string, ? bytes
- RAM, random-access memory, that stores zeroes and ones

## Arrays
- int scores[3],declare an array of three integers

## Strings

- In C, strings end with a special character, `'\0'`, or a byte with all eight bits set to 0, so our programs have a way of knowing where the string ends. This character is called the null character, or NUL.
- Libraries and functions: manual pages(https://manual.cs50.io/)

## Command-line arguments

- It turns out that our `main` function also returns an interger value called an **exit status**. By default, our `main` function returns `0` to indicate nothing went wrong, but we can write a program to return a different value:


```
#include <cs50.h>
#include <stdio.h>

int main(int argc, string argv[])
{
    if (argc != 2)
    {
        printf("missing command-line argument\n");
        return 1;
    }
    printf("hello, %s\n", argv[1]);
    return 0;
}
```


```
$ make arg
$ ./arg
missing command-line argument
$ ./arg David
hello, David
```

- If there is no return value after `missing command-line argument`



```
$ make arg
$ ./arg
missing command-line argument
hello, (null)
```


  - Once we run `return 1`, our program will **exit early** with an exit status of 1.(here can be any number, return 0 or 1 or 2...)
  - We'll write return 0 explicitly at the end of our program here, even though we don't technically need to since C will automatically return `0` for us.

