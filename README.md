# Python-Practice

# Week 38 [5/17-5/23]

# [293](https://leetcode.com/problems/flip-game/)
```python
def main(currentState):
   res = []
   i = 0
   exist = 0
   while exist > -1:
      exist = currentState[i:].find("++")
      if exist > -1:
            s = currentState[:i+exist] + currentState[i+exist:].replace("++", "--", 1)
            res += [s]
            i += exist + 1
      else:
            break
   return res
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)