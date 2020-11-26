# Python-Practice

# Week 13 [11/23-11/29]

### Template
# [231](https://leetcode.com/problems/power-of-two/)
```
def main(n):
  if n == 0:
    return False
  while n % 2 == 0:
    n /= 2
  return n == 1
```
#### Assumption: N = the given number
#### Complexity: runtime = O(logN), space = O(1)

# [896](https://leetcode.com/problems/monotonic-array/)
```
def main(A):
  inc = True
  dec = True
  for i in range(len(A) - 1):
    if A[i] < A[i+1]:
      decrease = False
    elif A[i] > A[i+1]:
      increase = False
  return increase or decrease
```
#### Assumption: N = the length of the given list A
#### Complexity: runtime = O(N), space = O(1)

# [628](https://leetcode.com/problems/maximum-product-of-three-numbers/)
```
def main(nums):
   nums.sort()
   return max(nums[-3] * nums[-2] * nums[-1], nums[0] * nums[1] * nums[-1])
```
#### Assumption: N = the length of the given number list
#### Complexity: runtime = O(NlogN) by sorting, space = O(1)

### Template
# []()
```
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)