# Python-Practice

# Week 37 [5/10-5/16]

# [566](https://leetcode.com/problems/reshape-the-matrix/)
```python
def main(nums, r, c):
    if not nums or not nums[0] or r * c != len(nums) * len(nums[0]):
        return nums
    new_m = [[0] * c for _ in range(r)]
    cur_r = 0
    cur_c = 0
    for i in range(len(nums)):
        for j in range(len(nums[0])):
            new_m[cur_r][cur_c] = nums[i][j]
            cur_c += 1
            if cur_c == c:
                cur_c = 0
                cur_r += 1
    return new_m
```
#### Assumption: M = the number of rows in the given nums matrix, N = the number of columns in the given nums matrix, R = the number size of r, C = the number size of c
#### Complexity: runtime = O(MN), space = O(1) excluding result matrix

# [1337](https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/)
```python
from collections import Counter
def main(mat, k):
    book = Counter()
    for i in range(len(mat)):
        book[i] = -sum(mat[i])
    return [x[0] for x in book.most_common()[:k]]
```
#### Assumption: M, N = the matrix dimension M x N, K = the result size
#### Complexity: runtime = O(MN), space = O(M)

# [1184](https://leetcode.com/problems/distance-between-bus-stops/)
```python
def main(distance, start, destination):
    mini = min(start, destination)
    maxi = max(start, destination)
    forward = sum(distance[mini:maxi])
    backward = sum(distance[:mini])+sum(distance[maxi:])
    return min(forward, backward)
```
#### Assumption: N = the number of elements in the distance list
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