# Python-Practice

# Week 80 [3/7-3/13]

# [495](https://leetcode.com/problems/teemo-attacking/)
```python
def main(timeSeries, duration):
   cnt = 0
   pre = -1
   for i in timeSeries:
      diff = 0
      if pre >= i:
         diff = pre - i + 1
      cnt = cnt - diff + duration
      pre = i + duration - 1        
   return cnt
```
#### Assumption: N = the number of elements in the given time series
#### Complexity: runtime = O(N), space = O(1)

# [2057](https://leetcode.com/problems/smallest-index-with-equal-value/)
```python
def main(nums):
   for i in range(len(nums)):
      val = nums[i]
      if i % 10 == val:
         return i
   return -1
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [1974](https://leetcode.com/problems/minimum-time-to-type-word-using-special-typewriter/)
```python
def main(word):
   pre = 'a'
   cnt = 0
   for i in word:
      diff = abs(ord(i) - ord(pre))
      cnt += 1 + min(26 - diff, diff)
      pre = i
   return cnt
```
#### Assumption: N = the length of the given word
#### Complexity: runtime = O(N), space = O(1)

# [1952](https://leetcode.com/problems/three-divisors/)
```python
def main(n):
   cnt = 2
   for i in range(2, n):
      if n % i == 0:
         cnt += 1
      if cnt > 3:
         return False
   return cnt == 3
```
#### Assumption: N = the size of the given number
#### Complexity: runtime = O(N), space = O(1)

# [1235](https://leetcode.com/problems/maximum-profit-in-job-scheduling/)
```python
def main(startTime, endTime, profit):
   size = len(startTime)
   jobs = [] # a list of [start, end, profit]
   maxProfit = [-1] * size
   for i in range(size):
      jobs += [[startTime[i], endTime[i], profit[i]]]
   jobs.sort(key=lambda x:x[0])
   # append sorted start time
   for i in range(size):
      startTime[i] = jobs[i][0]

   def findMaxProfit(pos):
      if pos == size:
         return 0
      if maxProfit[pos] != -1:
         return maxProfit[pos]
      curStart, curEnd, curProfit = jobs[pos]
      nextJobPos = findNextJob(curStart, curEnd)
      maxProfit[pos] = max(findMaxProfit(pos+1), findMaxProfit(nextJobPos) + curProfit)
      return maxProfit[pos]

   def findNextJob(curStart, curEnd):
      left = 0
      right = size - 1
      while left <= right:
         mid = (left + right) // 2
         if startTime[mid] >= curEnd: # overlap
            right = mid - 1
         else:
            left = mid + 1
      return left
   
   return findMaxProfit(0)
```
#### Assumption: N = the number of elements in the startTime/endTime/profit list
#### Complexity: runtime = O(NlogN), space = O(N)

# [723](https://leetcode.com/problems/candy-crush/)
```python
def main(board):
   nrow = len(board)
   ncol = len(board[0])
   crush = False
   for row in range(nrow):
      for col in range(ncol-2):
         if abs(board[row][col]) == abs(board[row][col+1]) == abs(board[row][col+2]) != 0:
            board[row][col] = board[row][col+1] = board[row][col+2] = -abs(board[row][col])
            crush = True
   for row in range(nrow-2):
      for col in range(ncol):
         if abs(board[row][col]) == abs(board[row+1][col]) == abs(board[row+2][col]) != 0:
            board[row][col] = board[row+1][col] = board[row+2][col] = -abs(board[row][col])
            crush = True
   for col in range(ncol):
      row_right = nrow - 1
      for row in range(nrow-1,-1,-1):
         if board[row][col] > 0:
            board[row_right][col] = board[row][col]
            row_right -= 1
      for row_right in range(row_right, -1, -1):
         board[row_right][col] = 0
   return self.candyCrush(board) if crush else board
```
#### Assumption: N = the number of elements in the board
#### Complexity: runtime = O(N^2), space = O(1)

# [1758](https://leetcode.com/problems/minimum-changes-to-make-alternating-binary-string/)
```python
def main(s):
   oddZero = 0
   oddOne = 0
   evenZero = 0
   evenOne = 0
   for idx in range(len(s)):
      if s[idx] == "0":
         if idx % 2 == 0:
            evenZero += 1
         else:
            oddZero += 1
      else:
         if idx % 2 == 0:
            evenOne += 1
         else:
            oddOne += 1
   if oddZero > evenZero or oddOne < evenOne:
      return oddOne + evenZero
   else:
      return evenOne + oddZero
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [682](https://leetcode.com/problems/baseball-game/)
```python
def main(ops):
   stack = []
   record = 0
   for i in ops:
      score = 0
      if i.isnumeric():
            score = int(i)
      elif i.startswith('-'):
            score = -int(i[1:])
      elif i == 'C':
            if stack:
               last = stack.pop()
               record -= last
               score = 0
      elif i == 'D':
            score = stack[-1] * 2
      elif i == '+':
            score = stack[-2] + stack[-1]
      if score != 0:
            stack += [score]
            record += score
   return record
```
#### Assumption: N = the number of operations in the given list
#### Complexity: runtime = O(N), space = O(N)

# [1995](https://leetcode.com/problems/count-special-quadruplets/)
```python
def main(nums):
   cnt = 0
   size = len(nums)
   for i in range(size):
      for j in range(i+1, size):
         for k in range(j+1, size):
            for l in range(k+1, size):
               if nums[i] + nums[j] + nums[k] == nums[l]:
                  cnt += 1
   return cnt                    
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N^4), space = O(1)

# [2023](https://leetcode.com/problems/number-of-pairs-of-strings-with-concatenation-equal-to-target/)
```python
def main(num, target):
   cnt = 0
   size = len(nums)
   for i in range(size):
      for j in range(i+1, size):
         if nums[i] + nums[j] == target:
            cnt += 1
         if nums[j] + nums[i] == target:
            cnt += 1
   return cnt
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N^2), space = O(1)

# [2068](https://leetcode.com/problems/check-whether-two-strings-are-almost-equivalent/)
```python
from collections import Counter
def main(word1, word2):
   book1 = Counter(word1)
   book2 = Counter(word2)
   for i in set(book1.keys()):
      occur_1 = book1[i]
      occur_2 = book2[i]
      if abs(occur_1 - occur_2) > 3:
         return False
      else:
         del book1[i]
         del book2[i]
   for i in book2:
      occur_1 = book1[i]
      occur_2 = book2[i]
      if abs(occur_1 - occur_2) > 3:
         return False
   return True
```
#### Assumption: N = the length of word1/word2
#### Complexity: runtime = O(N), space = O(N)

# [2073](https://leetcode.com/problems/time-needed-to-buy-tickets/)
```python
def main(tickets, k):
   size = len(tickets)
   buy_cnt = size
   cnt = 0
   while buy_cnt > 0:
      buy_cnt = 0
      for idx in range(size):
         val = tickets[idx]
         if val > 0:
            tickets[idx] -= 1
            cnt += 1
            buy_cnt += 1
         if tickets[k] == 0:
            return cnt
```
#### Assumption: N = the number of tickets
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
