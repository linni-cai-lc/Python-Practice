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

# [1704](https://leetcode.com/problems/determine-if-string-halves-are-alike/)
```python
def main(s):
   return len(re.sub("a|e|i|o|u", "", s[:len(s)//2].lower())) == len(re.sub("a|e|i|o|u", "", s[len(s)//2:].lower()))
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)

# [1475](https://leetcode.com/problems/final-prices-with-a-special-discount-in-a-shop/)
```python
def main(prices):
   stack = []
   for idx, val in enumerate(prices):
      while stack and prices[stack[-1]] >= val:
         prices[stack.pop()] -= val
      stack += [idx]
   return prices
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(N)
#### Note: utilize stack to store index for unused elements in the list, if the current value in the list is smaller than or equal to the top of the stack, make the discount update on the stack popped index in the price list.

# [346](https://leetcode.com/problems/moving-average-from-data-stream/)
```python
class MovingAverage:
    def __init__(self, size: int):
        self.lst = []
        self.size = size

    def next(self, val: int):
        if len(self.lst) == self.size:
            self.lst.pop(0)
        self.lst += [val]
        return sum(self.lst) / len(self.lst) 
```
#### Assumption: N = the object property list size
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