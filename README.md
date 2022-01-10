# Python-Practice

# Week 87 [4/25-5/1]

# 1. [518](https://leetcode.com/problems/coin-change-2/)
```python
def main(amount, coins):
   dp = [0] * (amount+1)
   dp[0] = 1
   for i in coins:
      for j in range(i, amount+1):
         dp[j] += dp[j-i]
   return dp[-1]
```
#### Assumption: N = the number of coins, A = the size of the amount
#### Complexity: runtime = O(N * A), space = O(A)

### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
