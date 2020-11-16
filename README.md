# Python-Practice

# Week 12 [11/16-11/22]

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

### Template
# []()
```
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)