# Python-Practice

# Week 75 [1/31-2/6]

# [1146](https://leetcode.com/problems/snapshot-array/)
```python
class SnapshotArray:
    def __init__(self, length):
        self.snap_book = [[[-1, 0]] for _ in range(length)]
        self.snap_id = 0

    def set(self, index, val):
        self.snap_book[index] += [[self.snap_id, val]]

    def snap(self):
        self.snap_id += 1
        return self.snap_id - 1

    def get(self, index, snap_id):
        i = bisect.bisect(self.snap_book[index], [snap_id + 1]) - 1
        return self.snap_book[index][i][1]
```
#### Assumption: N = the number of snapshots
#### Complexity:
- general: space = O(N)
- set: runtime = O(1)
- snap: runtime = O(1)
- get: runtime = O(logN)

# [1826](https://leetcode.com/problems/faulty-sensor/)
```python
def main(sensor1, sensor2) -> int:
    size = len(sensor1)
    cnt1 = False
    cnt2 = False
    val = 1
    for i in range(size):
        if sensor1[:i]+sensor1[i+1:] == sensor2[:-1]:
            cnt1 = True
            val = 2
        if sensor2[:i]+sensor2[i+1:] == sensor1[:-1]:
            cnt2 = True
    if cnt1 and cnt2:
        return -1
    return val
```
#### Assumption: N = the number of elements in each list
#### Complexity: runtime = O(N^2), space = O(1)

# [2000](https://leetcode.com/problems/reverse-prefix-of-word/)
```python
def main(word, ch):
    cur = ''
    idx = 0
    for i in word:
        cur += i
        if i == ch:
            return cur[::-1] + word[idx+1:]
        idx += 1
    return word
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)
```python
def main(word, ch):
    for i in range(len(word)):
        if word[i] == ch:
            return word[:i+1][::-1] + word[i+1:]
    return word
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [2027](https://leetcode.com/problems/minimum-moves-to-convert-string/)
```python
def main(s):
    cnt = 0
    idx = 0
    size = len(s)
    while idx < size:
        if s[idx] == 'X':
            cnt += 1
            idx += 3
        else:
            idx += 1
    return cnt
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [2032](https://leetcode.com/problems/two-out-of-three/)
```python
def main(nums1, nums2, nums3):
    set1 = set(nums1)
    set2 = set(nums2)
    set3 = set(nums3)
    diff12 = set1.intersection(set2)
    diff13 = set1.intersection(set3)
    diff23 = set2.intersection(set3)
    return diff12.union(diff13).union(diff23)
```
#### Assumption:
- N1 = the length of nums1
- N2 = the length of nums2
- N3 = the length of nums3
#### Complexity: runtime = O(N1+N2+N3), space = O(N1+N2+N3)
```python
from collections import Counter
def main(nums1, nums2, nums3):
    book = Counter()
    set1 = set(nums1)
    set2 = set(nums2)
    set3 = set(nums3)
    for i in set1:
        book[i] += 1
    for i in set2:
        book[i] += 1
    for i in set3:
        book[i] += 1
    res = []
    for i in book:
        if book[i] > 1:
            res += [i]
    return res
```
#### Assumption:
- N1 = the length of nums1
- N2 = the length of nums2
- N3 = the length of nums3
#### Complexity: runtime = O(N1+N2+N3), space = O(N1+N2+N3)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
