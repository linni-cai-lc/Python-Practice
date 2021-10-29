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

# [1945](https://leetcode.com/problems/sum-of-digits-of-string-after-convert/)
```python
def main(s, k):
    cur = ''
    for i in s:
        cur += str(ord(i) - ord('a') + 1)
    while k > 0:
        k -= 1
        new_cur = 0
        for i in cur:
            new_cur += int(i)
        cur = str(new_cur)
    return int(cur)      
```
#### Assumption: N = the length of the given string, K = the number of conversions
#### Complexity: runtime = O(logN * K), space = O(logN * K)


### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
