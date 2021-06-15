# Python-Practice

# Week 57 [9/27-10/3]

# [1796](https://leetcode.com/problems/second-largest-digit-in-a-string/)
```python
def main(s):
   maxi = [-1, -1]
   for i in s:
      if i.isnumeric():
         cur = int(i)
         if cur > maxi[0]:
            maxi[0], maxi[1] = cur, maxi[0]
         elif cur != maxi[0] and cur > maxi[1]:
            maxi[1] = cur
   return maxi[1]
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [1543](https://leetcode.com/problems/fix-product-name-format/)
```sql
SELECT LOWER(TRIM(product_name)) AS PRODUCT_NAME,
       DATE_FORMAT(sale_date, "%Y-%m") AS SALE_DATE,
       COUNT(*) AS TOTAL
FROM Sales
WHERE sale_date BETWEEN "2000-01-01" AND "2000-12-30"
GROUP BY LOWER(TRIM(product_name)), DATE_FORMAT(sale_date, "%Y-%m")
ORDER BY PRODUCT_NAME ASC, SALE_DATE ASC
```
```sql
SELECT LOWER(TRIM(product_name)) AS PRODUCT_NAME,
       DATE_FORMAT(sale_date, "%Y-%m") AS SALE_DATE,
       COUNT(*) AS TOTAL
FROM Sales
WHERE YEAR(sale_date) = 2000
GROUP BY LOWER(TRIM(product_name)), DATE_FORMAT(sale_date, "%Y-%m")
ORDER BY PRODUCT_NAME ASC, SALE_DATE ASC
```
```sql
SELECT LOWER(TRIM(product_name)) AS PRODUCT_NAME,
       DATE_FORMAT(sale_date, "%Y-%m") AS SALE_DATE,
       COUNT(*) AS TOTAL
FROM Sales
WHERE YEAR(sale_date) = 2000
GROUP BY LOWER(TRIM(product_name)), MONTH(sale_date)
ORDER BY PRODUCT_NAME ASC, SALE_DATE ASC
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
