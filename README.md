# DAA_Module_23

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


# EX 5B Coin Change Problem
## DATE:
## AIM:
To compute the fewest number of coins that we need to make up the amount given.


## Algorithm
1. Start by reading the number of coin denominations (n), the list of denominations (s), and the target amount (amt).
2. Initialize a dynamic programming (DP) array dp of size amt + 1, with all values set to infinity (inf) except dp[0], which is set to 0 (0 coins needed to make       amount 0). 
3. Iterate through each coin in the list of denominations. 
4. Update the DP array: For each coin, update all entries from coin to amt using the relation dp[i] = min(dp[i], dp[i - coin] + 1), meaning use the coin if it         leads to a smaller count.
5. Return the final result: If dp[amt] is still infinity, return -1 (amount cannot be formed); otherwise, return dp[amt].  

## Program:

```
/*
Create a python function to compute the fewest number of coins that we need to make up the amount given.
Developed by: Gokularamanan K
RegisterNumber: 212222230040
*/
```

```python
class Solution(object):
   def coinChange(self, coins, amount):
       dp = [float('inf')] * (amount + 1)
       dp[0]=0
       for coin in coins:
           for i in range(coin, amount + 1):
               dp[i] = min(dp[i], dp[i - coin] + 1)
       return dp[amount] if dp[amount]!=float('inf') else -1
      
ob1 = Solution()
n=int(input())
s=[]
amt=int(input())
for i in range(n):
    s.append(int(input()))


print(ob1.coinChange(s,amt))
```

## Output:
![image](https://github.com/user-attachments/assets/7e027691-67e1-432d-9661-7502c1cb7c3c)



## Result:
Thus the program was executed successfully for finding the minimum number of coins required to make amount.


# EX 5C Kadane's Algorithm
## DATE:
## AIM:
To write a python program to find the maximum contiguous subarray.


## Algorithm
1. Start by reading the number of elements n and the list of integers a[].
2. Initialize two variables:
    max_till_now to store the overall maximum subarray sum (start with the first element).
    max_ending to store the current subarray sum (start with 0).
3. Traverse the array from index 0 to n-1 using a loop.
4. Update max_ending by adding the current element. If max_ending becomes negative, reset it to 0. If max_ending exceeds max_till_now, update max_till_now. 
5. Return or print max_till_now as the maximum contiguous subarray sum.  

## Program:
```
/*
To implement the program to find the maximum contiguous subarray.
Developed by: Gokularamanan K
RegisterNumber: 212222230040
*/
```

```python
def maxSubArraySum(a,size):
    
    max_till_now = a[0]
    max_ending = 0
    
    for i in range(0, size):
        max_ending = max_ending + a[i]
        if max_ending < 0:
            max_ending = 0
        
        
        elif (max_till_now < max_ending):
            max_till_now = max_ending
            
    return max_till_now
n=int(input())  
a =[] 
for i in range(n):
    a.append(int(input()))
  
print("Maximum contiguous sum is", maxSubArraySum(a,n))
```

## Output:

![image](https://github.com/user-attachments/assets/73e03c8c-775b-421f-8940-16b789c6c378)



## Result:
Thus the program was executed successfully for finding the maximum contiguous sum of subarray..


# EX 5D Minimum Jump to Reach End Array
## DATE:
## AIM:
To write a python program for finding the minimum number of jumps needed to reach end of the array using Dynamic Programming.


## Algorithm
1. Start by reading the size of the array n and input the elements of the array arr[].
2. Initialize a jumps[] array of size n where jumps[i] will hold the minimum number of jumps required to reach index i. Set jumps[0] = 0 as no jumps are needed to     reach the start.
3. Loop through the array from index 1 to n-1 to fill jumps[i] by checking all previous indices j (from 0 to i-1).
4. Check if index i is reachable from index j using the condition i <= j + arr[j] and update jumps[i] = min(jumps[i], jumps[j] + 1) if jumps[j] is not infinity. 
5. Return or print jumps[n-1] which contains the minimum number of jumps to reach the last index.   

## Program:
```
/*
To implement the program to finding the minimum number of jumps needed to reach end of the array.
Developed by: Gokularamanan K
RegisterNumber: 212222230040
*/
```

```python
def minJumps(arr, l, h):
    if (h == l):
        return 0
    if (arr[l] == 0):
        return float('inf')
    min = float('inf')
    for i in range(l + 1, h + 1):
        if (i < l + arr[l] + 1):
            jumps = minJumps(arr, i, h)
            if (jumps != float('inf') and
                       jumps + 1 < min):
                min = jumps + 1
 
    return min
arr = []
n = int(input()) #len(arr)
for i in range(n):
    arr.append(int(input()))
print('Minimum number of jumps to reach','end is', minJumps(arr, 0, n-1))
```

## Output:

![image](https://github.com/user-attachments/assets/ea738506-e7d9-40c4-806a-2fdc7ae90ed8)


## Result:
Thus the program was executed successfully for finding the minimum number of jumps to reach end.
