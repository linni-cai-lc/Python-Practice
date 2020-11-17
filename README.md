# Python-Practice

# Week 12 [11/16-11/22]

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

### Template
# []()
```
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)