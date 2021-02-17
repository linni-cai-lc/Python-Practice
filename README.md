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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)