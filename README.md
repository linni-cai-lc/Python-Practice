# Python-Practice

# Week 35 [4/26-5/2]

# [1299](https://leetcode.com/problems/replace-elements-with-greatest-element-on-right-side/)
```python
def main(arr):
   res = [-1]
   maxi = 0
   for i in range(len(arr)-2, -1, -1):
      maxi = max(maxi, arr[i+1])
      res += [maxi]
   return res[::-1]
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1) excluding the result

# [985](https://leetcode.com/problems/sum-of-even-numbers-after-queries/)
```python
def main(A, queries):
   sumi = sum([i for i in A if i % 2 == 0])
   res = []
   for val, idx in queries:
      pre = A[idx]
      A[idx] += val
      pos = A[idx]
      if pre % 2 == 0:
         if pos % 2 == 0:
            sumi += pos - pre
         else:
            sumi -= pre
      elif pos % 2 == 0:
         sumi += pos
      res += [sumi]
   return res
```
#### Assumption: N = the number of elements in the queries
#### Complexity: runtime = O(N), space = O(1) excluding the result

# [1587](https://leetcode.com/problems/bank-account-summary-ii/)
```sql
SELECT Users.name, SUM(Transactions.amount) AS balance
FROM Users INNER JOIN Transactions ON Users.account = Transactions.account
GROUP BY Users.name
HAVING balance > 10000;
```

# [734](https://leetcode.com/problems/sentence-similarity/)
```python
from collections import defaultdict as dd
def main(sentence1, sentence2, similarPairs):
   similar_book = dd(set)
   for i, j in similarPairs:
      similar_book[i].add(j)
      similar_book[j].add(i)
   if len(sentence1) != len(sentence2):
      return False
   for i in range(len(sentence1)):
      cur1 = sentence1[i]
      cur2 = sentence2[i]
      if cur1 == cur2:
         continue
      else:
         if cur1 in similar_book and cur2 in similar_book[cur1]:
            continue
         else:
            return False
   return True
```
#### Assumption: N = the number of elements in similar pairs
#### Complexity: runtime = O(N), space = O(1)

# [69](https://leetcode.com/problems/sqrtx/)
```python
from math import sqrt, floor
def main(x):
   return floor(sqrt(x))
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(1), space = O(1)

# [884](https://leetcode.com/problems/uncommon-words-from-two-sentences/)
```python
from collections import Counter
def main(A, B):
   A = A.split(" ")
   B = B.split(" ")
   count_a = Counter(A)
   count_b = Counter(B)
   res = []
   for i in set(A).symmetric_difference(set(B)):
      if count_a[i] == 1 or count_b[i] == 1:
         res += [i]
   return res
```
#### Assumption: A = the number of elements in list a, B = the number of elements in list b
#### Complexity: runtime = O(A+B), space = O(A+B)

# [1137](https://leetcode.com/problems/n-th-tribonacci-number/)
```python
def main(self, n:)
   if n <= 1:
      return n
   self.book = [0] * (n + 1)
   self.book[1] = 1
   self.book[2] = 1
   return self.helper(n) 
   
def helper(self, cur):
   if cur <= 2:
      return self.book[cur]
   else:
      if not self.book[cur-1]:
            self.helper(cur-1)
      if not self.book[cur-2]:
            self.helper(cur-2)
      if not self.book[cur-3]:
            self.helper(cur-3)
      self.book[cur] = self.book[cur-1] + self.book[cur-2] + self.book[cur-3]
      return self.book[cur]
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(N), space = O(N)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)