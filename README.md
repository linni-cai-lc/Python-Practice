# Python-Practice

# Week 23 [1/31-1/7]

# [521](https://leetcode.com/problems/longest-uncommon-subsequence-i/)
```python
def main(a, b):
   if a == b:
      return -1
   return max(len(a), len(b))
```
#### Assumption: A = the length of string a, B = the length of string b
#### Complexity: runtime = O(min(A, B)), space = O(1)
#### Intuition: dominant time cost is on string comparison, provides min(A, B), for different lengths, comparison finished early on shorter string.

# [1662](https://leetcode.com/problems/check-if-two-string-arrays-are-equivalent/)
```python
def main(word1, word2):
   l = 0
   r = 0
   l_idx = 0
   r_idx = 0
   while l < len(word1) and r < len(word2):
      if word1[l][l_idx] != word2[r][r_idx]:
         return False
      l_idx += 1
      r_idx += 1
      if l_idx == len(word1[l]):
         l += 1
         l_idx = 0
      if r_idx == len(word2[r]):
         r += 1
         r_idx = 0
   return l == len(word1) and r == len(word2)
```
#### Assumption:
W1 = the number of words in word1 list, \
L1 = the length of a word in word1 list, \
W2 = the number of words in word2 list, \
L2 = the length of a word in word2 list
#### Complexity: runtime = O(W1L1+W2L2), space = O(1)

# [1527](https://leetcode.com/problems/patients-with-a-condition/)
```sql
SELECT patient_id, patient_name, condtions
FROM Patients
WHERE conditions LIKE "% DIAB1%" OR conditions LIKE "DIAB1%"
```

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)