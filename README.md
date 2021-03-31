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
#### Complexity: runtime = O(N^2), space = O(1)

```python
def main(currentState):
   res = []
   for i in range(len(currentState)-1):
      if currentState[i:i+2] == '++':
            res += [currentState[:i] + '--' + currentState[i+2:]]
   return res
```
#### Note: improve complexity to O(N)
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [1729](https://leetcode.com/problems/find-followers-count/)
```sql
SELECT user_id, COUNT(*) AS followers_count
FROM Followers
GROUP BY user_id
ORDER BY user_id
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