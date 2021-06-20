# Python-Practice

# Week 58 [10/4-10/10]

# [50](https://leetcode.com/problems/powx-n/)
```python
def myPow(x, n):
   res = 1
   cur = x
   i = abs(n)
   while int(i) > 0:
      if i % 2 == 1:
            res *= cur
            if i // 2 == 0:
               break
      cur *= cur
      i //= 2
   if n < 0:
      return 1 / res
   return res
```
#### Assumption: X = the given number size, Q = the given power size
#### Complexity: runtime = O(logQ), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
