# Python-Practice

# Week 30 [3/22-3-28]

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
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)