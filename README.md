# Python-Practice

# Week 12 [11/16-11/22]

### Template
# []()
```
class Solution:
    def reverseVowels(self, s: str) -> str:
        s = list(s)
        size = len(s)
        left = 0
        right = size
        VOWEL = "aeiou"
        while left < right:
            # print("left", left, s[left])
            if s[left].lower() in VOWEL:
                while right >= 0:
                    right -= 1
                    # print("right", right, s[right])
                    if s[right].lower() in VOWEL:
                        s[left], s[right] = s[right], s[left]
                        break
            left += 1
        return "".join(s)
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
