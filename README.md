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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
