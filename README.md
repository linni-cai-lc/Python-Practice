# Python-Practice

# Week 53 [8/30-9/5]

# [121](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
```python
def main(prices):
   max_diff = 0
   mini = sys.maxsize
   for idx, val in enumerate(prices):
      if val < mini:
         mini = val
      elif val - mini > max_diff:
         max_diff = val - mini
   return max_diff
```
#### Assumption: N = the number of prices
#### Complexity: runtime = O(N), space = O(1)

# [122](code.com/problems/best-time-to-buy-and-sell-stock-ii/)
```python
def main(prices):
   max_diff = 0
   for idx in range(1, len(prices)):
      if prices[idx] > prices[idx-1]:
         max_diff += prices[idx] - prices[idx-1]
   return max_diff
```
#### Assumption: N = the number of prices
#### Complexity: runtime = O(N), space = O(1)

# [123](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)
```python
def main(prices):
   cost1 = sys.maxsize
   cost2 = sys.maxsize
   diff1 = 0
   diff2 = 0
   for i in prices:
      cost1 = min(cost1, i)
      diff1 = max(diff1, i - cost1)

      cost2 = min(cost2, i - diff1)
      diff2 = max(diff2, i - cost2)
   return diff2
```
#### Assumption: N = the number of prices
#### Complexity: runtime = O(N), space = O(1)
```python
def main(prices):
   k = 2
   cost = [sys.maxsize] * k
   diff = [0] * k
   for i in prices:
      for j in range(k):
         cost[j] = min(cost[j], i - (diff[j-1] if j > 0 else 0))
         diff[j] = max(diff[j], i - cost[j])
   return diff[k-1]
```
#### Assumption: N = the number of prices
#### Complexity: runtime = O(N), space = O(1)

# [188](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/)
```python
def main(k, prices)
   if k == 0:
      return 0
   cost = [sys.maxsize] * k
   diff = [0] * k
   for i in prices:
      for j in range(k):
         cost[j] = min(cost[j], i - (diff[j-1] if j > 0 else 0))
         diff[j] = max(diff[j], i - cost[j])
   return diff[k-1]
```
#### Assumption: K = the given k size, P = the number of prices
#### Complexity: runtime = O(KP), space = O(K)

# [1880](https://leetcode.com/problems/check-if-word-equals-summation-of-two-words/)
```python
def main(firstWord, secondWord, targetWord):
   def get_num(word):
      num = ""
      for i in word:
         num += str(ord(i)-ord('a'))
      return int(num)

   first = get_num(firstWord)
   second = get_num(secondWord)
   target = get_num(targetWord)
   return first+second == target
```
#### Assumption: N1,N2,N3 = the length of first/second/thrid word
#### Complexity: runtime = O(N1+N2+N3), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
