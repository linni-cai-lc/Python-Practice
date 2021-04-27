# Python-Practice

# Week 42 [6/14-6/20]

# [1741](https://leetcode.com/problems/find-total-time-spent-by-each-employee/)
```sql
SELECT event_day AS day, emp_id, SUM(out_time-in_time) AS total_time
FROM Employees
GROUP BY day, emp_id;
```

# [1688](https://leetcode.com/problems/count-of-matches-in-tournament/)
```python
from math import ceil
def main(n):
   match = 0
   total_match = 0
   while n >= 2:
      match = n // 2
      total_match += match
      n = ceil(n / 2)
   return total_match
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(logN), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
