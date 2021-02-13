# Python-Practice

# Week 30 [3/22-3-28]

# [276](https://leetcode.com/problems/paint-fence/)
```python
def main(n, k):
   if n == 0:
      return 0
   c1, c2 = 0, k
   for i in range(2, n+1):
      c1, c2 = c2, (c1 + c2) * (k - 1)
   return c1 + c2
```
#### Note: this is a dp problem.
- Let's assume:
  - F[i][0] = the number of ways to paint the first i fences, i and i-1 have different colors
  - F[i][1] = the number of ways to paint the first i fences, i and i-1 have the same color
- F[i][0]:
  - i = 1: k
  - i > 1: (F[i-1][0] + F[i-1][1])*(k-1) = #(pre and cur have different colors) + #(pre and cur have the same color) * #(colors left)
- F[i][1]:
  - i = 1: k
  - i > 1: F[i-1][0]
#### Assumption: N = the number of fences, K = the number of colors
#### Complexity: runtime = O(N), space = O(1)

# [746](https://leetcode.com/problems/min-cost-climbing-stairs/)
```python
def main(cost):
   c1, c2 = 0, 0
   for i in cost[::-1]:
      c1, c2 = i + min(c1, c2), c1
   return min(c1, c2)
```
#### Note: this is a dp problem. 
- Let's assume F(i) = the min cost of the i th element.
- The dp formula: F[i] = C[i] + min(F[i-1], F[i-2]), since it is easier to calculate from the back to the front. When we have cost reversed version, convert to following.
- The new formula: F[i] = C[i] + min(F[i+1], F[i+2]). c1 is to accumulate cost with current cost, c2 is to give up current cost (skip).
#### Assumption: N = the number of elements in the cost list
#### Complexity: runtime = O(N), space = O(1)

# [303](https://leetcode.com/problems/range-sum-query-immutable/)
```python
from collections import defaultdict as dd

class NumArray:


    def __init__(self, nums: List[int]):
        self.book = dd(int)
        for i in range(len(nums)):
            self.book[i+1] = self.book[i] + nums[i]
        

    def sumRange(self, i: int, j: int) -> int:
        return self.book[j+1]-self.book[i]
```
#### Utilize default dict to provide set search, to improve runtime to O(1)
#### Assumption: N = the number elements in the array
#### Complexity: runtime = O(1), space = O(N)

# [232](https://leetcode.com/problems/implement-queue-using-stacks/)
```python
class MyQueue:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.lst = []
        

    def push(self, x: int) -> None:
        """
        Push element x to the back of queue.
        """
        self.lst += [x]
        

    def pop(self) -> int:
        """
        Removes the element from in front of queue and returns that element.
        """
        return self.lst.pop(0)
        

    def peek(self) -> int:
        """
        Get the front element.
        """
        return self.lst[0]
        

    def empty(self) -> bool:
        """
        Returns whether the queue is empty.
        """
        return len(self.lst) == 0
```

# [266](https://leetcode.com/problems/palindrome-permutation/)
```python
from collections import Counter
def main(s):
    book = Counter(s)
    odd = 0
    even = 0
    for i in book:
        if book[i] % 2 == 0:
            even += 1
        else:
            odd += 1
    return odd == (len(s) % 2)
```
#### Utilize counter to help count the letter occurrence:
- for even length, there should be no letter occurred in odd times
- for odd length, there should be one letter occurred in odd times
#### Assumption: N = the given string length
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