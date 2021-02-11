# Python-Practice

# Week 30 [3/22-3-28]

# [746](https://leetcode.com/problems/min-cost-climbing-stairs/)
```python
def main(cost):
   c1, c2 = 0, 0
   for i in cost[::-1]:
      c1, c2 = i + min(c1, c2), c1
   return min(c1, c2)
```
#### Note: this is a dp problem. Let's assume F(i) = the min cost of the i th element, the dp formula is F[i] = C[i] + min(F[i-1], F[i-2]), since it is easier to calculate from the back to the front. When we have cost reversed version, convert to a new formula: F[i] = C[i] + min(F[i+1], F[i+2]). c1 is to accumulate cost with current cost, c2 is to give up current cost (skip).
#### Assumption: N = the number of elements in the cost list
#### Complexity: runtime = O(N), space = O(1)

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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)