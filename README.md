# Python-Practice

# Week 76 [2/7-2/13]

# [1791](https://leetcode.com/problems/find-center-of-star-graph/)
```python
from collections import Counter
def main(edges):
   book = Counter()
   for i, j in edges:
      book[i] += 1
      book[j] += 1
   return book.most_common(1)[0][0]
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(1)
```python
from collections import Counter
def main(edges):
   book = Counter()
   for i, j in edges:
      book[i] += 1
      book[j] += 1
      if book[i] > 1:
         return i
      if book[j] > 1:
         return j
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(1)

# [1877](https://leetcode.com/problems/minimize-maximum-pair-sum-in-array/)
```python
def main(nums):
   nums.sort()
   maxi = 0
   for idx in range(len(nums)//2):
      maxi = max(maxi, nums[idx] + nums[-(idx+1)])
   return maxi
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(NlogN), space = O(1)

# [2016](https://leetcode.com/problems/maximum-difference-between-increasing-elements/)
```python
def main(nums):
    maxi = 0
    for i in range(len(nums)-1):
        maxi = max(maxi, max(nums[i+1:]) - nums[i])
    return maxi if maxi > 0 else -1
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N^2), space = O(1)
```python
def main(nums):
    diff = -1
    mini = nums[0]
    for i in range(1, len(nums)):
        cur = nums[i]
        if cur > mini:
            diff = max(diff, cur - mini)
        mini = min(mini, cur)
    return diff
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [2022](https://leetcode.com/problems/convert-1d-array-into-2d-array/)
```python
def main(original, m, n):
   size = len(original)
   if size != m * n:
      return []
   res = []
   cur = []
   for i in original:
      cur += [i]
      if len(cur) == n:
         res += [cur]
         cur = []
   return res
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1) excluding the returned result

# [1984](https://leetcode.com/problems/minimum-difference-between-highest-and-lowest-of-k-scores/)
```python
def main(nums, k):
    if k == 1:
        return 0
    size = len(nums)
    nums.sort()
    mini = sys.maxsize
    for i in range(size-k+1):
        mini = min(mini, nums[i+k-1]-nums[i])
    return mini
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(NlogN), space = O(1)

# [1967](https://leetcode.com/problems/number-of-strings-that-appear-as-substrings-in-word/)
```python
def main(patterns, word):
    cnt = 0
    for i in patterns:
        cnt += int(i in word)
    return cnt
```
#### Assumption: P = the number of patterns, W = the length of the word
#### Complexity: runtime = O(P*W), space = O(1)

# [1991](https://leetcode.com/problems/find-the-middle-index-in-array/)
```python
def main(nums):
    size = len(nums)
    left_sum = []
    right_sum = []
    left = 0
    right = 0
    for i in range(size):
        left += nums[i]
        right += nums[size-1-i]
        left_sum += [left]
        right_sum = [right] + right_sum
    for i in range(size):
        if left_sum[i] == right_sum[i]:
            return i
    return -1
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N)

# [1971](https://leetcode.com/problems/find-if-path-exists-in-graph/)
```python
from collections import defaultdict as dd
def main(n, edges, start, end):
    if start == end:
        return True
    book = dd(set)
    for i, j in edges:
        book[i].add(j)
        book[j].add(i)
    
    def dfs(cur, visited):
        neighbors = book[cur]
        for neighbor in neighbors:
            if neighbor == end:
                return True
            if neighbor not in visited:
                visited.add(neighbor)
                if dfs(neighbor, visited):
                    return True
        return False

    for i in book[start]:
        if dfs(i, set()):
            return True
    return False            
```
#### Assumption: N = the number of edges
#### Complexity: runtime = O(N), space = O(N) with recursive callstack

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
