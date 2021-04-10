# Python-Practice

# Week 39 [5/24-5/30]

# [1757](https://leetcode.com/problems/recyclable-and-low-fat-products/)
```sql
SELECT product_id
FROM Products
WHERE low_fats = 'Y' AND recyclable = 'Y';
```

# [1179](https://leetcode.com/problems/reformat-department-table/)
```sql
SELECT id, 
   SUM(IF(month = 'Jan', revenue, NULL)) AS Jan_Revenue,
   SUM(IF(month = 'Feb', revenue, NULL)) AS Feb_Revenue,
   SUM(IF(month = 'Mar', revenue, NULL)) AS Mar_Revenue,
   SUM(IF(month = 'Apr', revenue, NULL)) AS Apr_Revenue,
   SUM(IF(month = 'May', revenue, NULL)) AS May_Revenue,
   SUM(IF(month = 'Jun', revenue, NULL)) AS Jun_Revenue,
   SUM(IF(month = 'Jul', revenue, NULL)) AS Jul_Revenue,
   SUM(IF(month = 'Aug', revenue, NULL)) AS Aug_Revenue,
   SUM(IF(month = 'Sep', revenue, NULL)) AS Sep_Revenue,
   SUM(IF(month = 'Oct', revenue, NULL)) AS Oct_Revenue,
   SUM(IF(month = 'Nov', revenue, NULL)) AS Nov_Revenue,
   SUM(IF(month = 'Dec', revenue, NULL)) AS Dec_Revenue
FROM Department
GROUP BY id;
```

# [1777](https://leetcode.com/problems/products-price-for-each-store/)
```sql
SELECT product_id, 
   SUM(IF(store = 'store1', price, NULL)) AS store1,
   SUM(IF(store = 'store2', price, NULL)) AS store2,
   SUM(IF(store = 'store3', price, NULL)) AS store3
FROM Products
GROUP BY product_id;
```

# [1287](https://leetcode.com/problems/element-appearing-more-than-25-in-sorted-array/)
```python
from math import ceil
def main(arr):
   size = ceil(len(arr) * 0.25)
   cnt = -1
   pre = arr[0]
   for i in arr:
      if i == pre:
            cnt += 1
      else:
            if cnt > size:
               break
            else:
               cnt = 1
      pre = i
   return pre      
```
#### Note: one pass iteration, stop early strategy.
#### Assumption: N = the number of elements in the arr
#### Complexity: runtime = O(N), space = O(1)
```python
from collections import Counter
def main(arr):
   return Counter(arr).most_common()[0][0]          
```
#### Note: shortest code, however, it is slower than the previous method, also worse runtime+space. 
#### Assumption: N = the number of elements in the arr
#### Complexity: runtime = O(N), space = O(N)

# [1342](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/)
```python
def main(num):
   cnt = 0
   while num > 0:
      if num % 2 == 0:
            num /= 2
      else:
            num -= 1
      cnt += 1
   return cnt
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(logN), space = O(1)

# [1816](https://leetcode.com/problems/truncate-sentence/)
```python
def main(s, k):
   return " ".join(s.split(" ")[:k])
```
#### Assumption: N = the length of the given string, K = truncate length
#### Complexity: runtime = O(N), space = O(1)
```python
def main(s, k):
   cur = 0
   idx = 0
   while cur < k and idx < len(s):
         if s[idx] == " ":
            cur += 1
         idx += 1
   return s[:idx].rstrip()
```
#### Assumption: N = the length of the given string, K = truncate length
#### Complexity: runtime = O(N), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)