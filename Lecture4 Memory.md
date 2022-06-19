# Lecture4
## Hexadecimal
- hexadecimal, base-16, 16digits:
```0 1 2 3 4 5 6 7 8 9 A B C D E F```
## Addresses, pointers
- A **pointer** is a variable that stores an address in memory, where some other variable might be stored.
- The ```&``` operator can be used to get the address of some variable, as with ```&n```. And the ```*``` operator declares a variable as a pointer, as with ```*p```, indicating that we have a variable called ```p``` that _points_ to an ```int```. So, to store the address of a variable ```n``` into a pointer ```p```, we would write:
``` 
int *p = &n;
```
```
#include <stdio.h>

int main(void)
{
    int n = 50;
    int *p = &n;
    printf("%p\n", p);
}
```
```
Week4/ $ make pointer
Week4/ $ ./pointer
0x7ffcfd6bf0ec
```
- ```%p``` is the format code to print an address with ```printf```. And we only need to use the name of the variable, ```p```, after we've declared it.
- With C, we can also go to specific addresses in memory, which might cause segmentation faults, where we've tried to read or write to memory we don't have permission to. 
- The ```*``` operator is also the **dereference operator**, which goes to an address to get the value stored there. For example, we can say:
```
#include <stdio.h>

int main(void)
{
    int n = 50;
    int *p = &n;
    printf("%p\n", p);
    printf("%i\n", *p);
}
```
```
Week4/ $ make pointer
Week4/ $ ./pointer
0x7ffd161eb47c
50
```
