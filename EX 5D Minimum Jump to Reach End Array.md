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
