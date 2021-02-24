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

# [171](https://leetcode.com/problems/excel-sheet-column-number/)
```python
def main(s):
   res = 0
   for i in range(len(s)):
      res *= 26
      res += ord(s[i]) - ord('A') + 1
   return res
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [1768](https://leetcode.com/problems/merge-strings-alternately/)
```python
def main(word1, word2):
   res = ""
   i = 0
   while i < len(word1) and i < len(word2):
      res += word1[i] + word2[i]
      i += 1
   if i < len(word1):
      res += word1[i:]
   if i < len(word2):
      res += word2[i:]
   return res
```
#### Assumption: W1 = the length of word1, W2 = the length of word2
#### Complexity: runtime = O(W1+W2), space = O(1) excluding result string

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)