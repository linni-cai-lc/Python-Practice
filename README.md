# Python-Practice

# Week 45 [7/5-7/11]

# [120](https://leetcode.com/problems/triangle/)
```python
def main(triangle):
   @lru_cache(None)
   def dfs(idx, level):
      if level >= len(triangle) or idx >= len(triangle[level]):
         return 0
      return triangle[level][idx] + min(dfs(idx, level+1), dfs(idx+1, level+1))
   return dfs(0, 0)
```
#### Note: TOP DOWN with recursion
#### Assumption: N = the number of elements in the triangle list
#### Complexity: runtime = O(N^2), space = O(N^2) due to recursive call stack

```python
def main(triangle):
   for row in range(1, len(triangle)):
      for col in range(row + 1):
         cur = sys.maxsize
         if col > 0:
            cur = triangle[row - 1][col - 1]
         if col < row:
            cur = min(cur, triangle[row - 1][col])
         triangle[row][col] += cur
   return min(triangle[-1])
```
#### Note: BOTTOM UP with iteration, add previous min cost to the current location, which means the minimum cost from the top to the current location
#### Assumption: N = the number of elements in the triangle list
#### Complexity: runtime = O(N^2), space = O(1)

# [674](https://leetcode.com/problems/longest-continuous-increasing-subsequence/)
```python
def main(nums):
   cnt = 1
   maxi = 1
   for i in range(1, len(nums)):
      if nums[i] > nums[i-1]:
         cnt += 1
         maxi = max(maxi, cnt)
      else:
         cnt = 1
   return maxi
```
#### Note: no dp needed, since it is strictly increasing, easy for number increasing control
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(N)

# [1869](https://leetcode.com/problems/longer-contiguous-segments-of-ones-than-zeros/)
```python
def checkZeroOnes(s):
   maxi_ones = 0
   maxi_zeros = 0
   cnt_ones = 0
   cnt_zeros = 0
   pre = -1
   for i in s:
      if pre == -1:
         pre = i
         if i == '1':
            cnt_ones = 1
         else:
            cnt_zeros = 1
      else:
         if i == pre:
            if i == '1':
               cnt_ones += 1
            else:
               cnt_zeros += 1
         else:
            if i == '1':
               maxi_zeros = max(maxi_zeros, cnt_zeros)
               cnt_zeros = 0
               cnt_ones  = 1
            else:
               maxi_ones = max(maxi_ones, cnt_ones)
               cnt_ones = 0
               cnt_zeros = 1
      pre = i
   return max(maxi_ones, cnt_ones) > max(maxi_zeros, cnt_zeros)                
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [1873](https://leetcode.com/problems/calculate-special-bonus/)
```sql
SELECT employee_id,
    CASE WHEN employee_id % 2 = 1 AND name NOT LIKE "M%" THEN salary
    ELSE 0
    END AS bonus
FROM Employees;
```

# [1859](https://leetcode.com/problems/sorting-the-sentence/)
```python
def sortSentence(s):
   cur = ""
   book = []
   for i in s:
      if i.isdigit():
            book += [(cur, int(i))]
      elif i == " ":
            cur = ""
      else:
            cur += i
   book.sort(key=lambda x:x[1])
   return " ".join([i[0] for i in book])
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(NlogN), space = O(N)

# [1854](https://leetcode.com/problems/maximum-population-year/)
```python
from collections import Counter
def maximumPopulation(logs):
   logs.sort()
   book = Counter()
   maxi = sys.maxsize
   maxi_cnt = 0
   for born, dead in logs:
      for i in range(born, dead):
         book[i] += 1
         if book[i] > maxi_cnt or (book[i] == maxi_cnt and i < maxi):
            maxi_cnt = book[i]
            maxi = i
   return book.most_common()[0][0]
```
#### Assumption: N = the number of logs, R = the range of period
#### Complexity: runtime = O(NlogN+NR), space = O(NR)

# [1853](https://leetcode.com/problems/convert-date-format/)
```sql
SELECT DATE_FORMAT(day, "%W, %M %e, %Y") AS day
FROM Days;
```
#### Note: use DATE_FORMAT with appropriate format.

# [1844](https://leetcode.com/problems/replace-all-digits-with-characters/)
```python'
def replaceDigits(s):
   res = []
   letter = None
   for i in s:
      if not letter:
         letter = i
      else:
         res += [letter, chr(ord(letter) + int(i))]
         letter = None
   if letter:
      res += [letter]
   return "".join(res)
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)

# [139](https://leetcode.com/problems/word-break/)
```python
def main(s, wordDict):
   words = set(wordDict)
   dp = [False] * (len(s) + 1)
   dp[0] = True
   for i in range(1, len(s) + 1):
      for j in range(i):
         if dp[j] and s[j:i] in words:
            dp[i] = True
            break
   return dp[len(s)]
```
#### Assumption: N = the length of the string
#### Complexity: runtime = O(N^3), space = O(N)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
