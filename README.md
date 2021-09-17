# Python-Practice

# Week 72 [1/10-1/16]

# [917](https://leetcode.com/problems/reverse-only-letters/)
```python
def main(s):
   res = list(s)
   size = len(s)
   left = 0
   right = size - 1
   while left < right:
      left_val = res[left]
      while not left_val.isalpha() and left < right:
         left += 1
         left_val = res[left]
      right_val = res[right]
      while not right_val.isalpha() and left < right:
         right -= 1
         right_val = res[right]
      res[left], res[right] = res[right], res[left]
      left += 1
      right -= 1
   return ''.join(res)
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)

# [1557](https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/)
```python
def main(n, edges):
   return set(range(n)) - set(end for _, end in edges)
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(N)

# [890](https://leetcode.com/problems/find-and-replace-pattern/)
```python
def main(words, pattern):
   def get_pattern(word):
      word_book = {}
      word_format = []
      word_cnt = 0
      for i in word:
         if i not in word_book:
            word_cnt += 1
            word_book[i] = word_cnt
         word_format += [word_book[i]]
      return word_format
   
   pattern_format = get_pattern(pattern)
   res = []
   for word in words:
      word_format = get_pattern(word)
      if word_format == pattern_format:
         res += [word]
   return res
```
#### Assumption: W = the number of words, L = the length of word
#### Complexity: runtime = O(WL), space = O(WL)

# [950](https://leetcode.com/problems/reveal-cards-in-increasing-order/)
```python
def main(deck):
   size = len(deck)
   deck.sort()
   res = [None] * size
   idx = collections.deque(range(size))
   for i in deck:
      res[idx.popleft()] = i
      if idx:
         idx += [idx.popleft()]
   return res
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(NlogN), space = O(N)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
