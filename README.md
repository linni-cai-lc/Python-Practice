# Python-Practice

# Week 58 [10/4-10/10]

# [50](https://leetcode.com/problems/powx-n/)
```python
def myPow(x, n):
   res = 1
   cur = x
   i = abs(n)
   while int(i) > 0:
      if i % 2 == 1:
            res *= cur
            if i // 2 == 0:
               break
      cur *= cur
      i //= 2
   if n < 0:
      return 1 / res
   return res
```
#### Assumption: X = the given number size, Q = the given power size
#### Complexity: runtime = O(logQ), space = O(1)

# [718](https://leetcode.com/problems/maximum-length-of-repeated-subarray/)
```python
def main(nums1, nums2):
   dp = [0] * (len(nums2) + 1)
   maxi = 0
   for i in range(1, len(nums1)+1):
      pre = 0
      for j in range(1, len(nums2)+1):
         cur = dp[j]
         if nums1[i-1] == nums2[j-1]:
            dp[j] = 1 + pre
            maxi = max(maxi, dp[j])
         else:
            dp[j] = 0
         pre = cur                    
   return maxi
```
#### Assumption: N1 = the number of elements in nums1, N2 = the number of elements in nums2
#### Complexity: runtime = O(N1*N2), space = O(N2)

# [162](https://leetcode.com/problems/find-peak-element/)
```python
def main(nums):
   if len(nums) == 1:
      return 0
   nums = [-sys.maxsize] + nums + [-sys.maxsize]
   l, r = 1, len(nums)-2
   while l <= r:
      m = (l + r) // 2
      if nums[m-1] < nums[m] and nums[m+1] < nums[m]:
         return m-1
      elif nums[m] < nums[m+1]:
         l = m+1
      else:
         r = m-1
   return -1
```
#### Note: Utilize binary search to reduce time cost
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(logN), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
