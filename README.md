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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)