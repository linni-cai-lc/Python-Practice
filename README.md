# Python-Practice

# Week 29 [3/15-3-21]

# [1732](https://leetcode.com/problems/find-the-highest-altitude/)
```python
def main(gain):
   cur = 0
   maxi = 0
   for i in gain:
      cur += i
      maxi = max(maxi, cur)
   return maxi
```
#### Assumption: N = the number of elements in gain list
#### Complexity: runtime = O(N), space = O(1)

# [1646](https://leetcode.com/problems/get-maximum-in-generated-array/)
```python
def main(n):
   if n <= 1:
      return n
   res = [0, 1]
   maxi = 1
   for i in range(2, n+1):
      if i % 2 == 0:
            res += [res[i // 2]]
      else:
            res += [res[i // 2] + res[(i + 1) // 2]]
      maxi = max(maxi, res[-1])
   return maxi
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(N), space = O(N)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)