# Divide And Conquer

## Explanation

If the problem is divided into sub-problems, then the number of steps required to solve it reduces significantly.

```flow
Start
|
|__ Check if the problem is small enough to solve directly
|   |
|   |__ If yes,
|   |   |
|   |   |__ Solve the problem directly
|   |   |
|   |   |__ Return the solution
|   |
|   |__ If no,
|   |   |
|   |   |__ Divide the problem into smaller subproblems
|   |   |
|   |   |__ Recursively solve each subproblem
|   |   |
|   |   |__ Combine the solutions of the subproblems to solve the original problem
|   |   |
|   |   |__ Return the combined solution
|
End

```

Brute-Force Searching

Brute-force searching is also known as exhaustive searching, and it simply means to check all possible configurations for a given problem. It is easy to implement and would most definitely find the solution, although it consumes a lot of time.

Example:

If we have to find a name in a phone book, we started in the middle, thus dividing the search space into two halves. The phonebook  coincidently had names starting with L in the middle. If you were looking for a name  that starts with T, then you would have discarded everything to the left of L and moved to the right of L. This would have saved the number of steps required to search in the left half, which is insignificant to you. So, in each step, you reduce the search space by half. Therefore, if the search space had 128 elements initially, then you reduced the number to 64 in the first pass, 32 in the next, 16 in the next, 8 in the next, 4 after that, 2 after that, and, finally, the last element. The table given below depicts this more concisely.

| Steps | search size |
| ------------ | ----- |
| Initial Size |	128 |
| After Step 1 |	64 |
| After Step 2 |	32 |
| After Step 3 |	16 |
| After Step 4 |	8 |
| After Step 5 |	4 |
| After Step 6 |	2 |
| After Step 7 |	1 |
 