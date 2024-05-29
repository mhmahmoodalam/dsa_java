# Selection Sort Algorithm

## Explanation

Selection sort also, at the end of each iteration, pushes the \
next highest number to the end. However, this time, it was done \
with fewer swaps. You just pick the highest number in each \
iteration and swapped it with the last, unsorted number. So, \
each iteration in the worst case needs only one swap. This is \
unlike Bubble sort where you have to compare and swap every two \
numbers every time they are out of order.

```flow
Start
|
|__ Input the array of elements
|
|__ Set n = length of array
|
|__ Repeat n - 1 times (outer loop)
|   |
|   |__ Set minIndex = i (assume the current index is the minimum)
|   |
|   |__ Repeat from i + 1 to n - 1 (inner loop)
|   |   |
|   |   |__ If element at current index is less than element at minIndex
|   |   |   |
|   |   |   |__ Update minIndex to current index
|   |   |
|   |__ Swap the element at minIndex with the element at index i
|
|__ Output the sorted array
|
End


```

## Notes

- same as bubble sort
- does fewer swaps hence more efficient

## Analysis

- Selection sort also has a time complexity of O(N2).
- It performs fewer swaps than Bubble sort.
- So, ideally, it should run a bit more efficiently than Bubble sort.
