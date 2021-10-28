# Python-Practice

# Week 79 [2/28-3/6]

# [1598](https://leetcode.com/problems/crawler-log-folder/)
```python
def main(logs):
    PARENT = '../'
    CURRENT = './'
    cur = 0
    for i in logs:
        if i == PARENT:
            cur = max(0, cur-1)
        elif i == CURRENT:
            pass
        else:
            cur += 1
    return cur
```
#### Assumption: N = the number of elements in the log list
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
