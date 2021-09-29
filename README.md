# Python-Practice

# Week 74 [1/24-1/30]

# [1979](https://leetcode.com/problems/find-greatest-common-divisor-of-array/)
```python
def main(nums):
   mini, maxi = min(nums), max(nums)
   while mini:
      maxi, mini = mini, maxi % mini
   return maxi
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(1)

# [593](https://leetcode.com/problems/valid-square/)
```python
from collections import Counter
def main(p1, p2, p3, p4):
   def get_side_len(point1, point2):
      return sqrt(abs(point1[0]-point2[0])**2 + abs(point1[1]-point2[1])**2)
   
   s12 = get_side_len(p1, p2)
   s13 = get_side_len(p1, p3)
   s14 = get_side_len(p1, p4)
   s23 = get_side_len(p2, p3)
   s24 = get_side_len(p2, p4)
   s34 = get_side_len(p3, p4)
   
   book = Counter()
   book[s12] += 1
   book[s13] += 1
   book[s14] += 1
   book[s23] += 1
   book[s24] += 1
   book[s34] += 1
   if book.most_common()[-1][0] == 0:
      return False
   if book.most_common()[0][1] != 4:
      return False
   right_angle_side = book.most_common()[0][0]
   slope_side = book.most_common()[1][0]
   return abs(right_angle_side ** 2 * 2 - slope_side ** 2) < 0.001       
```
#### Note: since the input parameters are four points, the logic is constantly calculated
#### Complexity: runtime = O(1), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
