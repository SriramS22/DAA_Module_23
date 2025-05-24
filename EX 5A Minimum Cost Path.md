# EX 5A Minimum Cost Path
## DATE:
## AIM:
To write a Python program using A Naive recursive implementation of Minimum Cost Path Problem.

## Algorithm
1.Start by reading the number of rows R and columns C from the user.
2. Define a recursive function minCost(cost, m, n) that computes the minimum cost to reach cell (m, n) from (0, 0).
3. Check base conditions:
    If m < 0 or n < 0, return a very large number (infinity-like) to avoid invalid paths.
    If m == 0 and n == 0, return the cost at (0, 0) as it's the starting point.

4.Recursively calculate the minimum of the three possible directions (diagonal, up, left) and add the current cell’s cost.   
5. Print the minimum cost to reach cell (R-1, C-1) using the recursive function.  

## Program:
```
/*
A program to implement to find the Minimum Cost Path Problem using a  Naive recursive Approach.
Developed by: Gokularamanan K
RegisterNumber: 212222230040
*/
```
```python
R = int(input())
C = int(input())
import sys
def minCost(cost, m, n):
    if (n < 0 or m < 0):
        return sys.maxsize
    elif (m == 0 and n == 0):
        return cost[m][n]
    else:
        return cost[m][n] + min( minCost(cost, m-1, n-1),
                                minCost(cost, m-1, n),
                                minCost(cost, m, n-1) )
def min(x, y, z):
    if (x < y):
        return x if (x < z) else z
    else:
        return y if (y < z) else z
cost= [ [1, 2, 3],
        [4, 8, 2],
        [1, 5, 3] ]
print(minCost(cost, R-1, C-1))
```

## Output:
![image](https://github.com/user-attachments/assets/24fd4b59-f85b-472e-b1fe-65a95fbd1504)



## Result:
Thus the above program was executed successfully for finding the minimum cost.
