# Python-Practice

# Week 85 [4/11-4/17]

# 1. [1282](https://leetcode.com/problems/group-the-people-given-the-group-size-they-belong-to/)
```python
from collections import defaultdict as dd
def main(groupSizes):
   book = dd(list)
   for idx in range(len(groupSizes)):
      val = groupSizes[idx]
      group = book[val]
      if not group:
         group += [[idx]]
      else:
         last = group[-1]
         if len(last) == val:
            group += [[idx]]
         else:
            last += [idx]
   res = []
   for i in book:
      res += book[i]
   return res
```
#### Assumption: N = the group size
#### Complexity: runtime = O(N), space = O(N)

# 2. [121](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
```python
def main(prices):
   size = len(prices)
   maxi = 0
   mini = sys.maxsize
   for idx in range(size):
      mini = min(mini, prices[idx])
      maxi = max(maxi, prices[idx] - mini)
   return maxi
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# 3. [14](https://leetcode.com/problems/longest-common-prefix/)
```python
def main(strs):
   common = strs[0]
   size = len(strs)
   for idx in range(1, size):
      cur = strs[idx]
      new_common = ""
      left = 0
      right = 0
      left_size = len(common)
      right_size = len(cur)
      while left < left_size and right < right_size:
         if common[left] == cur[right]:
            new_common += common[left]
         else:
            break
         left += 1
         right += 1
      common = new_common
   return common
```
#### Assumption: N = the number of elements, M = the length of element
#### Complexity: runtime = O(N * M), space = O(M)

# 4. [811](https://leetcode.com/problems/subdomain-visit-count/)
```python
from collections import Counter
def main(cpdomains):
   book = Counter()
   for i in cpdomains:
      cnt, domains = i.split(" ")
      cnt = int(cnt)
      domainList = domains.split(".")
      for j in range(len(domainList)-1, -1, -1):
         cur = ".".join(domainList[j:])
         book[cur] += cnt
   res = []
   for i in book:
      res += [str(book[i]) + " " + i]
   return res
```
#### Assumption: N = the number of domains
#### Complexity: runtime = O(N), space = O(N)

# 5. [415](https://leetcode.com/problems/add-strings/)
```python
def main(num1, num2):
   left_size = len(num1)
   right_size = len(num2)
   left = left_size - 1
   right = right_size - 1
   res = ""
   add = 0
   while left >= 0 or right >= 0:
      cur_left = 0
      cur_right = 0
      if left >= 0:
         cur_left = int(num1[left])
      if right >= 0:
         cur_right = int(num2[right])
      cur_sum = cur_left + cur_right + add
      add = cur_sum // 10
      remainder = cur_sum % 10
      res = str(remainder) + res
      left -= 1
      right -= 1
   while add > 0:
      remainder = add % 10
      add //= 10
      res = str(remainder) + res
   return res
```
#### Assumption: N1 = the length of num1, N2 = the length of num2
#### Complexity: runtime = O(max(N1, N2)), space = O(max(N1, N2))

### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
