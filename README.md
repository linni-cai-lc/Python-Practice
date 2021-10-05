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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
