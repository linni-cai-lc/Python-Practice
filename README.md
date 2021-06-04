# Python-Practice

# Week 54 [9/6-9/12]

# [1827](https://leetcode.com/problems/minimum-operations-to-make-the-array-increasing/)
```python
def minOperations(nums):
   cnt = 0
   pre = 0
   for i in nums:
      if i <= pre:
         cnt += (pre+1-i)
         pre += 1
      else:
         pre = i
   return cnt
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
