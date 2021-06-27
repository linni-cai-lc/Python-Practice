# Python-Practice

# Week 59 [10/11-10/17]

# [1348](https://leetcode.com/problems/tweet-counts-per-frequency/)
```python
from collections import defaultdict as dd
from math import ceil
class TweetCounts:
    def __init__(self):
        self.book = dd(list)
        self.TIME = {
            'minute': 60,
            'hour': 3600,
            'day': 86400
        }

    def recordTweet(self, tweetName, time):
        self.book[tweetName] += [time]
        
    def getTweetCountsPerFrequency(self, freq, tweetName, startTime, endTime):
        gap = self.TIME[freq]
        res = [0] * ceil((endTime-startTime+1)/gap)
        
        for i in self.book[tweetName]:
            if startTime <= i <= endTime:
                res[(i-startTime)//gap] += 1
        return res
```
#### Assumption: N = the number of tweets
#### Complexity: runtime = O(N), space = O(N)

# [702](https://leetcode.com/problems/search-in-a-sorted-array-of-unknown-size/)
```python
def search(reader, target):
   if reader.get(0) == target:
      return 0
   l, r = 0, 1
   while reader.get(r) < target:
      l = r
      r <<= 1
   while l <= r:
      mid = (l + r) >> 1
      cur = reader.get(mid)
      if cur == target:
         return mid
      if cur > target:
         r = mid - 1
      else:
         l = mid + 1
   return -1
```
#### Note:
```
x << 1 = x * 2
x >> 1 = x / 2
```
#### Assumption: N = the number of elements in target
#### Complexity: runtime = O(logN), space = O(1)

# [1214](https://leetcode.com/problems/two-sum-bsts/)
```python
def twoSumBSTs(root1, root2, target):
   stack = []
   book = set()
   while stack or root1:
      while root1:
         stack += [root1]
         root1 = root1.left
      root1 = stack.pop()
      book.add(target - root1.val)
      root1 = root1.right
      
   while stack or root2:
      while root2:
         stack += [root2]
         root2 = root2.left
      root2 = stack.pop()
      if root2.val in book:
         return True
      root2 = root2.right
   return False
```
#### Note: Utilize stack to store all left children, store rest sum in hash set, quick look up for root2
#### Assumption: N1 = the number of elements in root1, N2 = the number of elements in root2 
#### Complexity: runtime = O(N1 + N2), space = O(N1 + N2)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
