# Python-Practice

# Week 24 [2/8-2/14]

# [705](https://leetcode.com/problems/design-hashset/)
```python
class MyHashSet:
   def __init__(self):
      self.book = []
   
   def add(self, key):
      if key not in self.book:
         self.book += [key]
   
   def remove(self, key):
      if key in self.book:
         self.book.remove(key)

   def contains(self, key):
      return key in self.book
```
#### Assumption: N = the number of elements in the given list
#### Complexity: add runtime = O(1), remove runtime = O(N), contains runtime = O(1), space = O(N)

# [643](https://leetcode.com/problems/maximum-average-subarray-i/)
```python
def main(nums, k):
   cur = sum(nums[:k])
   maxi = cur
   for i in range(1, len(nums)-k+1):
      cur += nums[i+k-1] - nums[i-1]
      maxi = max(max_ave, cur)
   return maxi / k
```
#### Assumption: N = the number of elements in the nums list, K = the size of subarray
#### Complexity: runtime = O(N), space = O(1)

# [1672](https://leetcode.com/problems/richest-customer-wealth/)
```python
def main(accounts):
   maxi = 0
   for i in accounts:
      maxi = max(maxi, sum(i))
   return maxi
```
#### Assumption: M = the number of customers, N = the number of accounts for each customer
#### Complexity: runtime = O(MN), space = O(1z)

# [989](https://leetcode.com/problems/add-to-array-form-of-integer/)
```python
def main(A, K):
   return list(str(int("".join(map(str, A))) + K))
```
#### Assumption: A = the number of elements in list A, K = the size of number to add in as K
#### Complexity: runtime = O(max(A, K)), space = O(1), return result space = O(max(A, K))

# [610](https://leetcode.com/problems/triangle-judgement/)
```sql
SELECT *, CASE WHEN x+y>z AND x+z>y AND y+z>x THEN "Yes" ELSE "No" END AS triangle
FROM triangle
```

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)