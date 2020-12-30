# Python-Practice

# Week 18 [12/28-1/3]

# [1037](https://leetcode.com/problems/valid-boomerang/)
```python
def main(points):
   return (points[0][1] - points[1][1]) * (points[1][0] - points[2][0]) != \
          (points[0][0] - points[1][0]) * (points[1][1] - points[2][1])
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)
#### Notes: utilize `(y1-y2)/(x1-x2)=(y2-y3)/(x2-x3)`, equal slope validates the same line

# [860](https://leetcode.com/problems/lemonade-change/)
```python
def main(bills):
   p5 = p10 = 0
   for i in bills:
      if i == 5:
         p5 += 1
      elif i == 10:
         if not p5:
            return False
         p5 -= 1
         p10 += 1
      else:
         if p5 and p10:
            p5 -= 1
            p10 -= 1
         elif p5 >= 3:
            p5 -= 3
         else:
            return False
      return True
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [922](https://leetcode.com/problems/sort-array-by-parity-ii/)
```python
def main(A):
   res = [-1] * len(A)
   even, odd = 0, 1
   for val in A:
      if val % 2 == 0:
         res[even] = val
         even += 2
      else:
         res[odd] = val
         odd += 2
   return res
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N)
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