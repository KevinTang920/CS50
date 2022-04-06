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

# Linear search, binary search
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
    If number begind doors[i]
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
  -```
  dsdf
  ```
