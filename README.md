# Python-Practice

# Week 19 [1/4-1/10]

# [1160](https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/)
```python
from collections import Counter
def main(words, chars):
   book = Counter(chars)
   res = 0
   for i in words:
      cur = Counter(i)
      match = True
      for letter in cur:
         if cur[letter] > book[letter]:
            match = False
      if match:
         res += len(i)
   return res
```
#### Assumption: W = the number of words, L = the max length of word in words, C = the length of chars
#### Complexity: runtime = O(WL+C), space = O(WL+C), constructing a counter of a word is O(L) for each word of length L

# [492](https://leetcode.com/problems/construct-the-rectangle/)
```python
from math import ceil
def main(area):
   for L in range(cel(area ** 0.5), area):
      if area % L == 0:
         return [L, area // L]
   return [area, 1]
```
#### Assumption: N = the number size
#### Complexity: runtime = O(sqrt(N)), space = O(1)

# [1141](https://leetcode.com/problems/user-activity-for-the-past-30-days-i/)
```sql
SELECT activity_date AS day, count(DISTINCT user_id) as active_users
FROM Activity
WHERE activity_date <= "2019-07-27" AND activity_date > "2019-06-27"
GROUP_BY activity_date
```

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