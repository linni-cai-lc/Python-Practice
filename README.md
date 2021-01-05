# Python-Practice

# Week 19 [1/4-1/10]

# [1365](https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/)
```python
def main(nums):
   sort_nums = sorted(nums)
   book = {}
   res = []
   for idx, val in enumerate(sort_nums):
      if val not in book:
         book[val] = idx
   for i in nums:
      res.append(book[i])
   return res
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(NlogN), space = O(N)

# [1389](https://leetcode.com/problems/create-target-array-in-the-given-order/)
```python
def main(nums, index):
   res = []
   for idx, val in enumerate(index):
      res.insert(val, nums[idx])
   return res
```
#### Assumption: N = the number of elements in nums = M = the number of elements in index
#### Complexity: runtime = O(N^2) list insertion takes O(N), space = O(N) return the result list

# [596](https://leetcode.com/problems/classes-more-than-5-students/)
```sql
SELECT class
FROM courses
GROUP BY class
HAVING COUNT(DISTINCT student) >= 5
```

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)