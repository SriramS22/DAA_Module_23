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
