# Python-Practice

# Week 18 [12/28-1/3]
# [922](https://leetcode.com/problems/sort-array-by-parity-ii/)
```python
def main(A):
   odd, even, res = [], [], []
   for val in A:
      if val % 2 == 0:
         even += [val]
      else:
         odd += [val]
   for i in range(len(A) // 2):
      res += [even.pop(), odd.pop()]
   return res
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)