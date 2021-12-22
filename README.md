# Python-Practice

# Week 84 [4/4-4/10]

# [412](https://leetcode.com/problems/fizz-buzz/)
```python
def main(n):
   res = []
   for i in range(1, n+1):
      cur = ""
      if i % 3 == 0:
         cur += "Fizz"
      if i % 5 == 0:
         cur += "Buzz"
      if not cur:
         cur = str(i)
      res += [cur]
   return res
```
#### Assumption: N = the size of the given number
#### Complexity: runtime = O(N), space = O(1)

# [20](https://leetcode.com/problems/valid-parentheses/)
```python
def main(s):
   stack = []
   rev_book = {
      ')': '(',
      ']': '[',
      '}': '{',
   }
   for i in s:
      if i in rev_book.values():
         stack += [i]
      else:
         if not stack:
            return False
         cur = stack.pop()
         if cur != rev_book[i]:
            return False
   return not stack
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)

# [253](https://leetcode.com/problems/meeting-rooms-ii/)
```python
def main(intervals):
   intervals.sort(key=lambda x:(x[0], x[1]))
   pres = [intervals[0]]
   for idx in range(1, len(intervals)):
      start, end = intervals[idx]
      fit = False
      for pre_idx in range(len(pres)):
         pre_start, pre_end = pres[pre_idx]
         if start >= pre_end:
            pres[pre_idx] = intervals[idx]
            fit = True
            break
      if not fit:
         pres += [intervals[idx]]
   return len(pres)
```
#### Assumption: N = the number of intervals, K = the number of rooms
#### Complexity: runtime = O(N*K), space = O(K)

# [443](https://leetcode.com/problems/string-compression/)
```python
def main(chars):
   pre = None
   cnt = 0
   res = ""
   for i in chars:
      if i == pre:
         cnt += 1
      else:
         if pre:
            if cnt == 1:
               res += pre
            else:
               res += pre + str(cnt)
         cnt = 1
         pre = i
   if pre:
      if cnt == 1:
         res += pre
      else:
         res += pre + str(cnt)
   res_size = len(res)
   for i in range(res_size):
      chars[i] = res[i]
   return res_size
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N)
```python
def main(chars):
   pre = None
   cnt = 0
   left = 0
   for i in chars:
      if i == pre:
         cnt += 1
      else:
         if pre:
            chars[left] = pre
            left += 1
            if cnt > 1:
               cnt_str = str(cnt)
               for j in range(len(cnt_str)):
                  chars[left] = cnt_str[j]
                  left += 1
         cnt = 1
         pre = i
   if pre:
      chars[left] = pre
      left += 1
      if cnt > 1:
         cnt_str = str(cnt)
         for j in range(len(cnt_str)):
            chars[left] = cnt_str[j]
            left += 1
   return left
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [49](https://leetcode.com/problems/group-anagrams/)
```python
from collections import defaultdict as dd
def main(strs):
   book = dd(list)
   for i in strs:
      anagram = tuple(sorted(i))
      book[anagram] += [i]
   return book.values()      
```
#### Assumption: N = the number of elements in the given list, M = the length of the element
#### Complexity: runtime = O(NlogM), space = O(N)

# [71](https://leetcode.com/problems/simplify-path/)
```python
def main(path):
   stack = []
   cur = ''
   size = len(path)
   for idx in range(size+1):
      if idx < size:
         val = path[idx]
      if val == '/' or idx == size:
         if cur:
            if cur == '..':
               if stack:
                  stack.pop()
            elif cur == '.':
               pass
            else:
               stack += [cur]
            cur = ''
      else:
         cur += val
   return '/' + '/'.join(stack)
```
#### Assumption: N = the length of the given path
#### Complexity: runtime = O(N), space = O(N)

# [1282](https://leetcode.com/problems/group-the-people-given-the-group-size-they-belong-to/)
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

# [121](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
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

# [14](https://leetcode.com/problems/longest-common-prefix/)
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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
