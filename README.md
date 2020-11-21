# Python-Practice

# Week 12 [11/16-11/22]

# [704](https://leetcode.com/problems/binary-search/)
```
def main(nums, target):
  left = 0
  right = len(nums) - 1
  while left <= right:
    mid = (left + right) // 2
    if target < nums[mid]:
      right = mid - 1
    elif target > nums[mid]:
      left = mid + 1
    else:
      return mid
  return -1
```
#### Assumption: N = the number of elements in the given nums
#### Complexity: runtime = O(logN), space = O(1)

# [876](https://leetcode.com/problems/middle-of-the-linked-list/)
```
def main(head):
  slow = head
  fast = head
  while fast and fast.next:
    fast = fast.next.next
    slow = slow.next
  return slow
```
#### Assumption: N = the number of nodes in the given linked list
#### Complexity: runtime = O(N), space = O(1) with temporary constant number of variables

# [290](https://leetcode.com/problems/word-pattern/)
```
from collections import defaultdict as dd
def main(pattern, s):
  words = s.split("")
  if len(pattern) != len(words):
    return False
  word_book = dd(str)
  pattern_book = dd(str)
  for i in range(len(pattern)):
    cur_pattern = pattern[i]
    cur_word = words[i]
    if cur_word not in word_book and cur_pattern not in pattern_book:
      word_book[cur_word] = cur_pattern
      pattern_book[cur_pattern] = cur_word
    elif word_book[cur_word] != cur_pattern:
      return False
  return True
```
#### Assumption: N = the number of words in the given string, M = the number of unique words
#### Complexity: runtime = O(N), space = O(M) using 2 dictionary, hash maps

# [1441](https://leetcode.com/problems/build-an-array-with-stack-operations/)
```
def main(target, n):
  res = []
  cur = 0
  for i in target:
    while cur != i:
      cur += 1
      res.append("Push")
      if cur != i:
        res.append("Pop")
  return res
```
#### Assumption: N = the size of the given n, target size T is bounded by N
#### Complexity: runtime = O(N), space = O(N)

# [1047](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)
```
def main(S):
  stack = []
  for i in S:
    if not stack or stack[-1] != i:
      stack.append(i)
    else:
      while stack and stack[-1] == i:
        stack.pop(-1)
  return "".join(stack)
```
#### Assumption: N = the length of the given string, D = the length of duplicate string
#### Complexity: runtime = O(N), space = O(N - D)

# [844](https://leetcode.com/problems/backspace-string-compare/)
```
def main(S, T):
  return backspace(S) == backspace(T)

def backspace(s):
  stack = []
  for i in s:
    if i == "#":
      if stack:
        stack.pop(-1)
    else:
      stack.append(i)
  return stack
```
#### Assumption: N = the length of S, M = the length of T
#### Complexity: runtime = O(N + M), space = O(N + M)

# [1507](https://leetcode.com/problems/reformat-date/)
```
from datetime import datetime
def main(date):
  date = re.sub("st|nd|rd|th", "", date)
  return datetime.strptime(date, "%d %b %Y").strftime(%Y-%m-%d)
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N) use the string to convert between date object and string 

# [345](https://leetcode.com/problems/reverse-vowels-of-a-string/)
```
def main(s):
  s = list(s)
  size = len(s)
  left = 0
  right = size
  VOWEL = "aeiou"
  while left < right:
    if s[left].lower() in VOWEL:
      while right >= 0:
        right -= 1
        if s[right].lower() in VOWEL:
          s[left], s[right] = s[right], s[left]
          break
    left += 1
  return "".join(s)
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N) use a list to store the string, help on letter swap, otherwise string concatenation is extra O(N), which would bring up runtime complexity to O(N^2), we use more space to reduce time.

# [1480](https://leetcode.com/problems/running-sum-of-1d-array/)
```
def main(nums):
  for i in range(1, len(nums)):
    nums[i] += nums[i-1]
  return nums
```
#### Assumption: N = the length of the given list
#### Complexity: runtime = O(N), space = O(1) in place updating, exclude the given list space as extra

### Template
# []()
```
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)