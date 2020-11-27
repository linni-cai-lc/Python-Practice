# Python-Practice

# Week 13 [11/23-11/29]

# [859](https://leetcode.com/problems/buddy-strings/)
```
def main(A, B):
  if len(A) != len(B):
    return False
  pre = None
  nex = None
  same = set()
  hasSame = False
  for i in range(len(A)):
    if A[i] != B[i]:
      if not pre:
        pre = [A[i], B[i]]
      elif not nex:
        nex = [A[i], B[i]]
      else:
        return False
    if A[i] in same:
      hasSame = True
    same.add(A[i])
    return (not pre and not nex and hasSame) or \
           (pre and nex and pre[0] == nex[1] and pre[1] == nex[0])
```
#### Assumption: N = the length of A/B
#### Complexity: runtime = O(N), space = O(N)

# [27](https://leetcode.com/problems/remove-element/)
```
def main(nums, val):
  left = 0
  right = len(nums) - 1
  while left <= right:
    if nums[left] == val:
      nums[left] = nums[right]
      right -= 1
    else:
      left += 1
  return left
```
#### Assumption: N = the length of the given list nums
#### Complexity: runtime = O(N), space = O(1)

# [342](https://leetcode.com/problems/power-of-four/)
```
def main(n):
  if n == 0:
    return False
  while n % 4 == 0:
    n /= 4
  return n == 1
```
#### Assumption: N = the given number n
#### Complexity: runtime = O(logN), space = O(1)

# [1436](https://leetcode.com/problems/destination-city/)
```
def main(paths):
  start = set()
  end = set()
  for i, j in paths:
    start.add(i)
    end.add(j)
  return end.difference(start).pop()
```
#### Assumption: N = the number of paths
#### Complexity: runtime = O(N), space = O(N)

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