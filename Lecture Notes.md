# CS50
# Lecture1

## IDEs, compilers, interfaces

- IDEs, integrated development environments
- CLI, command-line interface
- code hello.c, to create a new file called hello.c
- compile program: make hello
- run program: `./hello`
- file name with an asterisk,\*,to indicate that it's executable, or that we can run it.

## main, header files, commands

- commands:
  - cd, for changing our current directory(folder). We can go up tow levels at once with `cd ../..` 
  - cp, for copying files and directories
  - ls, for listing files in a directory
  - mkdir, for making a directory
  - mv, for moving(renaming) files and directories
  - rm, for removing(deleting) files
  - rmdir, for removing(deleting) directories
- clean the terminal window:
  - `clean` 
  - contrl + L

## Calculations
- In the terminal window, we can also start typing commands like make `ca`, and then press the tab key for the terminal to automatically complete our command. The up and down arrows also allow us to see previous commands and run them without typing them again.
- comments `//`

## Constant

- `const int MINE = 2`;  \# The const keyword tells our compiler to ensure that the value of this variable isn't changed, and by convention the name of the variable should be in all upper case.


## or `||`  and `&&`
- In C, a char is surrounded y single quotes, ', instead of double quotes for strings.

## Loops, functions
- We define our function with `void meow(void)`. The first `void` means that there isn't a return value for our function. The `void` within the parentheses also indicates that the function doesn't take any arguments, or inputs.

## Imprecision, overflow
- Specify the number of decimal places displayed: %.5f

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
- We can add a command-line argument, or an input to a program on the command-line as extra words after the program's name. We can run `clang -0 hello hello.c`, where `clang` is the name of the program, and `-o hello` and `hello.c` are additional arguments. We're telling `clang` to use `hello` as the output filename, and use `hello.c` as the source code. Now, we can see `hello` being created as output.

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
- RAM, random-access memory, tat stores zeroes and ones

## Arrays
- int scores[3],declare an array of three integers

## Strings

- In C, strings end with a special character, `'\0'`, or a byte with all eight bits set to 0, so our programs have a way of knowing where the string ends. This character is called the null character, or NUL.
- Libraries and functions: manual pages(https://manual.cs50.io/)

## Command-line arguments

- It turns out that our `main` function also returns an interger value called an **exit status**. By default, our `main` function returns `0` to indicate nothing went wrong, but we can write a program to return a different value:
`
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
`
`
$ make arg
$ ./arg
missing command-line argument
$ ./arg David
hello, David
`
- If there is no return value after `missing command-line argument`

`
$ make arg
$ ./arg
missing command-line argument
hello, (null)
`
  - Once we run `return 1`, our program will **exit early** with an exit status of 1.(here can be any number, return 0 or 1 or 2...)
  - We'll write return 0 explicitly at the end of our program here, even though we don't technically need to since C will automatically return `0` for us.


