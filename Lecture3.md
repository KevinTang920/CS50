# Lectue3
## Big Ο
- Running time
- Big O notation
- Some common running times:
  - O(n²)
  - O(n log n)
  - O(n)
  - O(log n)
  - O(1)

- Big Ω，big Omega notation,which describes the lower bound of number of steps for our algorithm
  - Ω(n²)
  - Ω(n log n)
  - Ω(n)
  - Ω(log n)
  - Ω(1)

- Θ, big Theta, which we use to describe running times of algorithms if the upper bound and lower bound is the same.
  - Θ(n²)
  - Θ(n log n)
  - Θ(n)
  - Θ(log n)
  - Θ(1)

## Linear search, binary search
- Linear search: one by one, from left to right.
- pseudocode
```
For each door from left to right
    If number is behind dorr
        Return true
Retrurn false
```
   - `Retrun false` is outside the for loop, since we only want to do that after we've looked behind all doors.

- Rewrite pseudocode to be a little closer to C:
```
For i from 0 to n-1
    If number behind doors[i]
        Return true
Return false
```
- For linear search, big *O* is *O*(n), big Omega is Ω(1).
- Binary search: know the numbers are sorted, star in the middle, know go left or right.
```
If no doors
    Return false
If number behind middle door
    Return true
Else if number < middle door
    Search left half
Else if number > middle door 
    Search right half
```
- more like C
```
If no doors
    Return false
If number behind doors[middle]
    Return true
Else if number < doors[middle]
    Search door[0] through doors[middle -1]
Else if number > doors[middle]
    Search doors[middle + 1] through doors[n -1]
```
- For binary search: Big *O* is *O*(log n), big Omega is Ω(1).

## Searching with code

- ```number.c```
```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int numbers[] = {4, 6, 8, 2, 7, 5, 0}
    for (int i = 0; i < 7; i++)
    {
        if (numbers[i] == 0)
        {
            printf("Found\n")
            return 0;
        }
    }
    printf("Not found\n")
    return 1;
}
```
  - ```return 0``` indicate success, ```return 1``` indicate an error code.
- ```name.c```
```
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    string names[] = {"Bill", "Charlie", "Fred", "George", "Ginny", "Tim", "Alex")
    for (int i = 0; i < 7; i++)
    {
        if (names[i] == "Ron")
        {
            printf("Found\n")
            return 0;
        }
    }
    printf("Not found\n");
    return 1;
}
```
  - When we try to compile our program, we get an error.
  - Can not compare strings directly in C.
  - ```strcmp```,string compare: returns a negative value if the first string comes before the second string, ```0```if the strings are the same, and a positive value if the first string comes after the second string.
  - Chage conditional to ```if (strcmp(names[i], "Ron") == 0)```
  - ```if (strcmp(names[i], "Ron"))```,any non-zero value, positive or negative, would be cosidered ```true```, which would be the *opposite* of what we want.
    - We could actually write ```if(!strcmp(names[i], "Ron"))``` to invert the value, but it would be arguably worse design.

## Structs
- We might want to implemnt a phone book, with names and phone numbers in phonebook0.c
```
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    string names[] = {"Carter", "David"};
    string numbers[] = {"16174951000", "19494682740"};
    for (int i = 0; i < 2; i++)
    {
        if (strcmp(names[i], "David") == 0)
        {
            printf("Found %s\n", numbers[i]);
            return 0;
        }
    }
    printf("Not found\n");
    return 1;

}
```
- It turns out in C that we can define our own data type, or **data structure**.
- In C, we can create a struct with the following syntax:
```
typedef struct
{
    string name;
    string number;
}
peerson;
```
  - ```typedef struct``` tells the compiler that we're defining our own data structure. And ```person``` at the end of the curly braces will be the name of this data structure.

- We'll use this in phonebook1.c
```
#include <cs50.h>
#include <stdio.h>
#include <string.h>

typedef struct
{
    string name;
    string number;
}
person;

int main(void)
{
    person people[2];
    people[0].name = "Carter";
    people[0].number = "1513243341";

    people[1].name = "David";
    people[1].number = "1151515151";

    for (int i = 0; i < 2; i++)
    {
        if (strcmp(people[i].name, "David") ==0)
        {
            printf("Found %s\n", people[i].number);
            return 0;
        }
    }
    printf("Not found\n");
    return 1;
}
```
- In coumputer science, **encapsulation** is the idea that related data is grouped together, and here we've encapsulated two pieces of information, ```name``` and ```number``` into the same data structure.
