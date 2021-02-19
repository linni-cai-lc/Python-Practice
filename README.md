# Python-Practice

# Week 31 [3/29-4/4]

# [1629](https://leetcode.com/problems/slowest-key/)
```python
def main(releaseTimes, keysPressed):
    maxi = 0
    res = ""
    for i in range(len(releaseTimes)):
        cur = releaseTimes[0] if i == 0 else releaseTimes[i] - releaseTimes[i-1]
        if cur > maxi:
            maxi = cur
            res = keysPressed[i]
        elif cur == maxi and keysPressed[i] > res:
            res = keysPressed[i]
    return res
```
#### Assumption: N = the number of release times = the number of keys pressed
#### Complexity: runtime = O(N), space = O(1)

# [1071](https://leetcode.com/problems/greatest-common-divisor-of-strings/)
```python
def main(str1:, str2):
    if len(str1) < len(str2):
        str1, str2 = str2, str1
    res = ""
    for i in range(1, len(str2)+1):
        cur = str2[:i]
        if len(str1.replace(cur, "")) == 0 and len(str2.replace(cur, "")) == 0:
            res = str2[:i]
    return res
```
#### Assumption: S1 = the length of string1, S2 = the length of string2
#### Complexity: runtime = O(S2*(S1+S2)), space = O(S1+S2)
```python
from math import gcd
def main(str1:, str2):
    if len(str1) < len(str2):
        str1, str2 = str2, str1
    res = ""
    for i in range(1, gcd(len(str1), len(str2))+1):
        cur = str2[:i]
        if len(str1.replace(cur, "")) == 0 and len(str2.replace(cur, "")) == 0:
            res = str2[:i]
    return res
```
#### Assumption: S1 = the length of string1, S2 = the length of string2
#### Complexity: runtime = O(S1/S2*(S1+S2)), space = O(S1+S2)
```python
from math import gcd
def main(str1:, str2):
    if len(str1) < len(str2):
        str1, str2 = str2, str1
    for i in range(gcd(len(str1), len(str2))+1, 0, -1):
        cur = str2[:i]
        if len(str1.replace(cur, "")) == 0 and len(str2.replace(cur, "")) == 0:
            return cur
    return ""
```
#### Assumption: S1 = the length of string1, S2 = the length of string2
#### Complexity: runtime = O(S1+S2), space = O(S1+S2)

# [157](https://leetcode.com/problems/read-n-characters-given-read4/)
```python
def main(buf, n):
    cnt = 0
    tmp = [None] * 4
    cur = read4(tmp)
    while cur and cnt < n:
        pre_cnt = cnt
        diff = min(n-cnt, cur)
        cnt += diff
        for i in range(diff):
            buf[pre_cnt+i] = tmp[i]
        cur = read4(tmp)
    return cnt
```
#### Assumption: N = the number of copy size
#### Complexity: runtime = O(N), space = O(1)

# [720](https://leetcode.com/problems/longest-word-in-dictionary/)
```python
from collections import defaultdict as dd
class Solution:
    def longestWord(self, words: List[str]) -> str:
        self.book = dd(list)
        for i in words:
            self.book[len(i)] += [i]
        self.res = ""
        for i in self.book[1]:
            self.dfs(i, 0)
        return self.res
    
    def dfs(self, cur, cnt):
        cnt += 1
        for i in self.book[len(cur)+1]:
            if cur + i[-1] == i:
                self.dfs(i, cnt)
        if (len(cur) > len(self.res)) or \
           (len(cur) == len(self.res) and cur < self.res):
            self.res = cur
```
#### Utilize DFS and dictionary to build up a trie, access key by word length build up from 1
#### Assumption: N = the total number of letters in the word list
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