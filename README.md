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

# 2. [780](https://leetcode.com/problems/reaching-points/)
```python
def main(sx, sy, tx, ty):
   while tx >= sx and ty >= sy:
      if tx == ty:
         break
      elif tx > ty:
         if ty > sy:
            tx %= ty
         else:
            return (tx-sx) % ty == 0
      else:
         if tx > sx:
            ty %= tx
         else:
            return (ty-sy) % tx == 0
   return tx == sx and ty == sy
```
#### Assumption: TX = the size of number tx, TY = the size of number ty
#### Complexity: runtime = O(log(max(TX, TY))), space = O(1 )

### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
