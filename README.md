# Python-Practice

# Week 32 [4/5-4/11]

# [1431](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/)
```python
def main(candies, extraCandies):
   maxi = max(candies)
   res = []
   for i in candies:
      if i + extraCandies >= maxi:
            res += [True]
      else:
            res += [False]
   return res
```
#### Assumption: N = the number of kids in the candies list
#### Complexity: runtime = O(N), space = O(1) excluding result array

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)