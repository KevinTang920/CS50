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
## Sorting
### Selection sort
- Select the smallest nmber and swap.
- For this algorithm, we started with looking at all _n_ elements, then only _n-1_, then _n-2_, and so on:
  n + (n-1) + (n-2)+...+1
  n(n+1)/2
 （n²+n)/2
  n²/2+n/2
  _O_(n²)
- In the best case, where th list is already sorted, our selection sort algorithm will still look at all the numbers and repeat the loop, so it has a lower bound for running time of Ω(n²).

## Bubble sort
- Look at **pairs** of numbers and swap them if they are out of order.
- To determine the running time for bubble sort, we have _n-1_ comparisons in the loop, and _n-1_ loops:
  (n-1) * (n-1)
  n² - 2n + 1
  _O_(n²)
- The lower bound for running time of bubble sort would be Ω(n).

## Recursion
- **Recurison** is the ability for a function to call itself. 
- pyramid
```
#
##
###
```
- Code
```
#include <cs50.h>
#include <stdio.h>

void draw(int n);
int main(void)
{
    int height = get_int("Height: ");
    
    draw(height);
}

void draw(int n)
{
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < i + 1; j++)
        {
            printf("#");
        }
        printf("\n");
    }
}
```
- But notice that a pyramid of height 4 is actually a pyramid of height 3 with an extra row of 4 blocks added on. And a pyramid of height 3 is a pyramid of height 2 with an extra row of 3 blocks. A pyramid of height 2 is a pyramid of height 1 with an extra row of 2 blocks. And finally, a pyramid of height 1 is a pyramid of height 0(no blocks) with a row of 1 block added.
- Since a pyramid is a recursive structure, we can write a recursive function to draw a pyramid, a function that calls itself to draw a smller pyramid before adding another row:
```
#include <cs50.h>
#include <stdio.h>

void draw(int n);

int main(void)
{
    int height = get_int("Height: ");
    
    draw(height);
}

void draw(int n)
{
    if (n <= 0)
    {
        return;
    }
    draw(n -1);
    
    for (int i = 0; i < n; i++)
    {
        printf("#");
    }
    printf("\n");
}
```
- We can rewrite our draw function to use itself.
- if ```n``` is ```0``` (or negative somehow) we'll stop without printing anything. And we need to make sure we stop for some base case, so our function doesn't call itself over and over forever.
- Otherwise, we'll call ```draw``` again, to print a pyramid of size ```n-1``` first.
- Then, we'll print the row of blocks we need for our pyramid, of size ```n```.

## Merge sort
- Sort each half, and then merge thme together.
- The upper bound for running time for merge sort is  _O_(nlogn).
- The lower bound of merge sort is still Ω(nlogn), since we have to do all the work even if the list is sorted. So merge sort also has θ(nlogn).
