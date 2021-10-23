# Python-Practice

# Week 78 [2/21-2/27]

# [1903](https://leetcode.com/problems/largest-odd-number-in-string/)
```python
def main(num):
    for i in range(len(num), -1, -1):
        if int(num[i-1]) % 2 == 1:
            return num[:i]
    return ""
```
#### Assumption: N = the length of the given number string
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
