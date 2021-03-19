# Python-Practice

# Week 36 [5/3-5/9]

# [1173](https://leetcode.com/problems/immediate-food-delivery-i/)
```sql
SELECT ROUND(IMM.CNT * 100 / TOT.CNT,2) AS immediate_percentage
FROM (
    SELECT COUNT(*) AS CNT
    FROM Delivery
    WHERE order_date = customer_pref_delivery_date
) AS IMM, (
    SELECT COUNT(*) AS CNT
    FROM Delivery
) AS TOT;
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