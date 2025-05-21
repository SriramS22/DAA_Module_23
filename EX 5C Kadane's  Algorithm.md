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
Developed by: Gokul J 
Register Number: 212222230038  
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
