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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)