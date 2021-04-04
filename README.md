# Python-Practice

# Week 38 [5/17-5/23]

# [293](https://leetcode.com/problems/flip-game/)
```python
def main(currentState):
   res = []
   i = 0
   exist = 0
   while exist > -1:
      exist = currentState[i:].find("++")
      if exist > -1:
            s = currentState[:i+exist] + currentState[i+exist:].replace("++", "--", 1)
            res += [s]
            i += exist + 1
      else:
            break
   return res
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N^2), space = O(1)

```python
def main(currentState):
   res = []
   for i in range(len(currentState)-1):
      if currentState[i:i+2] == '++':
            res += [currentState[:i] + '--' + currentState[i+2:]]
   return res
```
#### Note: improve complexity to O(N)
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [1729](https://leetcode.com/problems/find-followers-count/)
```sql
SELECT user_id, COUNT(*) AS followers_count
FROM Followers
GROUP BY user_id
ORDER BY user_id
```

# [1809](https://leetcode.com/problems/ad-free-sessions/)
```sql
SELECT session_id
FROM Playback LEFT JOIN Ads
  ON Playback.customer_id = Ads.customer_id
AND Ads.timestamp BETWEEN start_time and end_time
WHERE Ads.customer_id IS NULL
```

# [1748](https://leetcode.com/problems/sum-of-unique-elements/)
```python
from collections import Counter
def main(nums):
   book = Counter(nums)
   sumi = 0
   for i in book:
      if book[i] == 1:
            sumi += i
   return sumi
```
#### Assumption: N = the number of elements in the nums
#### Complexity: runtime = O(N), space = O(N)

# [1795](https://leetcode.com/problems/rearrange-products-table/)
```sql
SELECT product_id, "store1" AS store, store1 AS price
FROM Products
WHERE store1 IS NOT NULL
UNION
SELECT product_id, "store2" AS store, store2 AS price
FROM Products
WHERE store2 IS NOT NULL
UNION
SELECT product_id, "store3" AS store, store3 AS price
FROM Products
WHERE store3 IS NOT NULL;
```

# [1789](https://leetcode.com/problems/primary-department-for-each-employee/)
```sql
SELECT employee_id, department_id
FROM Employee
WHERE primary_flag = 'Y'
UNION
SELECT employee_id, department_id
FROM Employee
GROUP BY employee_id
HAVING COUNT(employee_id) = 1;
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