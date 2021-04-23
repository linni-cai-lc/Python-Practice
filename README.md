# Python-Practice

# Week 41 [6/7-6/13]

# [914](https://leetcode.com/problems/x-of-a-kind-in-a-deck-of-cards/)
```python
from collections import Counter
def main(deck):
   book = Counter(deck)
   size = len(deck)
   vals = book.values()
   for i in range(2, size+1):
      if size % i == 0:
         same = True
         for j in vals:
            same = same and j % i == 0
         if same:
            return True
   return False
```
#### Assumption: N = the number of cards in the deck
#### Complexity: runtime = O(N^2), space = O(N)

# [1005](https://leetcode.com/problems/maximize-sum-of-array-after-k-negations/)
```python
from heapq import heapify, heapreplace
def main(A, K):
   heapify(A)
   while K > 0 and A[0] < 0:
      heapreplace(A, -A[0])
      K -= 1
   if K % 2 == 1:
      heapreplace(A, -A[0])
   return sum(A)
```
#### Assumption: N = the number of elements in A, K = times of process
#### Complexity: runtime = O(NlogN), space = O(N)

# [1736](https://leetcode.com/problems/latest-time-by-replacing-hidden-digits/)
```python
def main(time):
   res = ''
   for idx, val in enumerate(time):
      if val == ':' or val != '?':
            res += val
            continue
      if idx == 0:
            h2 = time[1]
            if h2 < '4' or h2 == '?':
               res += '2'
            else:
               res += '1'
      elif idx == 1:
            h1 = res
            if h1 == '2':
               res += '3'
            else:
               res += '9'
      elif idx == 3:
            res += '5'
      else:
            res += '9'
   return res
```
#### Assumption: N = the number string length
#### Complexity: runtime = O(N), space = O(1) excluding return result space

# [1511](https://leetcode.com/problems/customer-order-frequency/)
```sql
SELECT CID AS customer_id, name
FROM (
    SELECT Orders.customer_id AS CID, SUM(Product.price * Orders.quantity) AS SPENT
    FROM Orders INNER JOIN Product ON Product.product_id = Orders.product_id
    WHERE YEAR(Orders.order_date) = 2020 AND
          MONTH(Orders.order_date) BETWEEN 6 AND 7
    GROUP BY customer_id, MONTH(Orders.order_date)
    HAVING SPENT >= 100
) AS MERGE INNER JOIN Customers ON MERGE.CID = Customers.customer_id
GROUP BY CID
HAVING COUNT(CID) = 2;
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