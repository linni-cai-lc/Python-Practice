# Python-Practice

# Week 35 [4/26-5/2]

# [1299](https://leetcode.com/problems/replace-elements-with-greatest-element-on-right-side/)
```python
def main(arr):
   res = [-1]
   maxi = 0
   for i in range(len(arr)-2, -1, -1):
      maxi = max(maxi, arr[i+1])
      res += [maxi]
   return res[::-1]
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1) excluding the result

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)