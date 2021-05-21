# Python-Practice

# Week 44 [6/28-6/30]

# [1422](https://leetcode.com/problems/maximum-score-after-splitting-a-string/)
```python
def maxScore(s):
   cur_0 = 0
   cur_1 = s.count("1")
   maxi = 0
   for i in s[:-1]:
      if i == "0":
         cur_0 += 1
      else:
         cur_1 -= 1
      maxi = max(maxi, cur_0+cur_1)
   return maxi
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [1423](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)
```python
def maxScore(cardPoints, k):
   cnt = len(cardPoints) - k
   R = sum(cardPoints[cnt:])
   L = 0
   res = R
   for i in range(k):
      L += cardPoints[i]
      R -= cardPoints[cnt]
      cnt += 1
      res = max(res, L + R)
   return res
```
#### Assumption: K = the number size of k
#### Complexity: runtime = O(K), space = O(1) 

# [485](https://leetcode.com/problems/max-consecutive-ones/)
```python
def findMaxConsecutiveOnes(nums):
   cnt = 0
   maxi = 0
   for i in nums:
      if i == 1:
         cnt += 1
      else:
         maxi = max(maxi, cnt)
         cnt = 0
   return max(maxi, cnt)
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1) 

# [487](https://leetcode.com/problems/max-consecutive-ones-ii/)
```python
def findMaxConsecutiveOnes(self, nums: List[int]) -> int:
        cnt = 0
        flip = False
        maxi = 0
        idx = 0
        flip_next = -1
        while idx < len(nums):
            i = nums[idx]
            if i == 1:
                cnt += 1
                idx += 1
            else:
                if not flip:
                    flip = True
                    cnt += 1
                    idx += 1
                    flip_next = idx
                else:
                    maxi = max(maxi, cnt)
                    cnt = 0
                    idx = flip_next
                    flip = False
        return max(maxi, cnt)
                    
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N^2), space = O(1) 
```python
def findMaxConsecutiveOnes(self, nums: List[int]) -> int:
   cnt = 0
   flip = False
   maxi = 0
   idx = 0
   flip_maxi = 0
   for i in nums:
      if i == 1:
         cnt += 1
      else:
         if not flip:
            flip = True
            cnt += 1                   
         else:
            maxi = max(maxi, cnt)
            cnt -= flip_maxi - 1
         flip_maxi = cnt       
   return max(maxi, cnt)
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1) 

# [1004](https://leetcode.com/problems/max-consecutive-ones-iii/)
```python
def main(nums, k):
   L = 0
   for i in range(len(nums)):
      k -= 1 - nums[i]
      if k < 0:
         k += 1 - nums[L]
         L += 1
   return len(nums) - L
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [198](https://leetcode.com/problems/house-robber/)
```python
def main(nums):
prepre = 0
   pre = nums[0]
   for i in range(1, len(nums)):
      cur = max(pre, prepre+nums[i])
      prepre = pre
      pre = cur
   return pre
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)
```python
def main(nums):
   dp = [0] * len(nums)
   dp[0] = nums[0]
   for i in range(1, len(nums)):
      dp[i] = max(dp[i-1], nums[i]+dp[i-2])
   return dp[-1]
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N)

# [213](https://leetcode.com/problems/house-robber-ii/)
```python
def main(nums):
   if len(nums) < 4:
      return max(nums)
   size = len(nums)
   prepre_1,pre_1,prepre_2,pre_2 = 0,0,0,0
   for i in range(size):
      cur1, cur2 = None, None
      if 0 <= i < size-1:
         cur1 = max(pre_1, prepre_1+nums[i-1])
         prepre_1 = pre_1
         pre_1 = cur1
      if 0 < i < size:
         cur2 = max(pre_2, prepre_2+nums[i-1])
         prepre_2 = pre_2
         pre_2 = cur2
   return max(pre_1, pre_2)
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [337](https://leetcode.com/problems/house-robber-iii/)
```python
def main(root):
   return max(dfs(root))

def dfs(root):
   if not root:
      return (0, 0)
   left_child = self.dfs(root.left)
   right_child = self.dfs(root.right)
   return (root.val + left_child[1] + right_child[1], max(left_child) + max(right_child))
```
#### Assumption: N = the number of children in the tree
#### Complexity: runtime = O(N), space = O(1)

# [256](https://leetcode.com/problems/paint-house/)
```python
def minCost(self, costs: List[List[int]]) -> int:
   dp = [[-1] * 3 for _ in range(len(costs))]
   return min(
      self.dfs(costs, len(costs), 0, 0, dp),
      self.dfs(costs, len(costs), 1, 0, dp),
      self.dfs(costs, len(costs), 2, 0, dp)
   )

def dfs(self, costs, nrow, col, row, dp):
   if row == nrow:
      return 0
   if dp[row][col] == -1:
      if col == 0:
         dp[row][col] = costs[row][0] + min(self.dfs(costs, nrow, 1, row+1,dp),self.dfs(costs, nrow, 2, row+1,dp))
      elif col == 1:
         dp[row][col] = costs[row][1] + min(self.dfs(costs, nrow, 0, row+1,dp),self.dfs(costs, nrow, 2, row+1,dp))
      else:
         dp[row][col] = costs[row][2] + min(self.dfs(costs, nrow, 0, row+1,dp),self.dfs(costs, nrow, 1, row+1,dp))
   return dp[row][col]
```
#### Note: TOP DOWN method with recursion and memoization
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N)
```python
def main(costs):
   dp = [[-1] * 3 for _ in range(len(costs))]
   dp[0] = costs[0][:]
   nrow = len(costs)
   for row in range(1, nrow):
      dp[row][0] = costs[row][0] + min(dp[row-1][1], dp[row-1][2])
      dp[row][1] = costs[row][1] + min(dp[row-1][0], dp[row-1][2])
      dp[row][2] = costs[row][2] + min(dp[row-1][0], dp[row-1][1])
   return min(dp[-1])
```
#### Note: BOTTOM UP method with iteration
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N)
```python
def main(costs):
   dp = costs[0][:]
   nrow = len(costs)
   for row in range(1, nrow):
      new_dp = dp[:]
      new_dp[0] = costs[row][0] + min(dp[1], dp[2])
      new_dp[1] = costs[row][1] + min(dp[0], dp[2])
      new_dp[2] = costs[row][2] + min(dp[0], dp[1])
      dp = new_dp
   return min(dp)
```
#### Note: BOTTOM UP method with iteration, save space
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)
```python
def main(costs):
   dp = costs[0][:]
   nrow = len(costs)
   for row in range(1, nrow):
      new_dp = dp[:]
      for col in range(3):
         tmp = dp[col]
         dp[col] = sys.maxsize
         new_dp[col] = costs[row][col] + min(dp)
         dp[col] = tmp
      dp = new_dp
   return min(dp)
```
#### Note: BOTTOM UP method with iteration, save space, reduce color redundancy
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [265](https://leetcode.com/problems/paint-house-ii/)
```python
def main(costs):
   dp = costs[0][:]
   nrow = len(costs)
   ncol = len(costs[0])
   for row in range(1, nrow):
      new_dp = dp[:]
      for col in range(ncol):
         tmp = dp[col]
         dp[col] = sys.maxsize
         new_dp[col] = costs[row][col] + min(dp)
         dp[col] = tmp
      dp = new_dp
   return min(dp)
```
#### Note: Based on 256 BOTTOM UP with iteration, save space
#### Assumption: N = the number of elements in the given list, K = the number of colors
#### Complexity: runtime = O(NK), space = O(K)

# [1473](https://leetcode.com/problems/paint-house-iii/)
```python
def main(houses, cost, nrow, ncol, target):
   @lru_cache(None)
   def helper(row, pre_color, neighbor):
      if row == nrow:
         if neighbor == target:
            return 0
         else:
            return sys.maxsize
      if houses[row] > 0:
         return helper(row+1, houses[row], neighbor+int(pre_color != houses[row]))
      cur = sys.maxsize
      for col in range(1, ncol+1):
         cur = min(cur, cost[row][col-1] + helper(row+1, col, neighbor + int(pre_color != col)))
      return cur
   res = helper(0, -1, 0)
   if res == sys.maxsize:
      return -1
   else:
      return res
```
#### Note: TOP DOWN with recursion
#### Assumption: N = the number of houses, K = the number of colors, T = the number of neighbors
#### Complexity: runtime = O(NK), space = O(NK) using recursive stack
```python
def main(houses, cost, nrow, ncol, target):
   # color, #block: min cost
   old_dp = {(0, 0): 0}
   new_dp = {}
   for house_idx, house_color in enumerate(houses):
      color_range = [house_color]
      if house_color == 0:
         color_range = list(range(1, ncol+1))
      for new_color in color_range:
            for color, block in old_dp:
               new_block = block + int(color != new_color)
               if new_block > target:
                  continue
               new_dp[(new_color, new_block)] = min(
                  new_dp.get((new_color, new_block), sys.maxsize),
                  old_dp[(color, block)] + cost[house_idx][new_color-1] * int(new_color != house_color)
               )
      old_dp, new_dp = new_dp, {}
   res = [old_dp[color, block] for color, block in old_dp if block == target]
   if not res:
      return -1
   else:
      return min(res)
```
#### Note: BOTTOM UP with iteration, bad time complexity, but alternative space solution
#### Assumption: N = the number of houses, K = the number of colors, T = the number of neighbors
#### Complexity: runtime = O(NKT), space = O(NK)

# [55](https://leetcode.com/problems/jump-game/)
```python
def canJump(self, nums: List[int]) -> bool:
   return self.dfs(nums, 0, len(nums))
   
def dfs(self, nums, idx, end):
   if idx >= end - 1:
      return True
   cur = nums[idx]
   res = False
   for i in range(idx+1, idx+cur+1):
      res = res or self.dfs(nums, i, end)
   return res
```
#### Note: TOP DOWN with recursion, bad time complexity, TLE
#### Assumption: N = the number of elements in the given list, K = the element value range in the given list
#### Complexity: runtime = O(N^2), space = O(N)
```python
def canJump(self, nums: List[int]) -> bool:
   return self.dfs(nums, 0, len(nums), [-1] * len(nums)) > 0
   
def dfs(self, nums, idx, end, dp):
   if idx >= end - 1:
      return True
   cur = nums[idx]
   if dp[idx] == -1:
      dp[idx] = False
      for i in range(idx+1, idx+cur+1):
         dp[idx] = dp[idx] or self.dfs(nums, i, end, dp)
   return dp[idx]
```
#### Note: TOP DOWN with recursion, bad time complexity, TLE
#### Assumption: N = the number of elements in the given list, K = the element value range in the given list
#### Complexity: runtime = O(N^K), space = O(N)
```python
def canJump(self, nums: List[int]) -> bool:
   size = len(nums)
   dp = [False] * size
   dp[-1] = True
   for i in range(size-2, -1, -1):
      for j in range(i+1, min(i+nums[i]+1, size)):
            if dp[j]:
               dp[i] = True
               break
   return dp[0]
```
#### Note: BOTTOM UP with iteration, bad time complexity, TLE
#### Assumption: N = the number of elements in the given list, K = the element value range in the given list
#### Complexity: runtime = O(N^2), space = O(N)
```python
def canJump(self, nums: List[int]) -> bool:
   end = len(nums)-1
   for i in range(end-1, -1, -1):
      if i + nums[i] >= end:
         end = i
   return end == 0
```
#### Note: Utilize Greedy, trace backward from the jump list, use the last location for the next comparison
#### Assumption: N = the number of elements in the given list, K = the element value range in the given list
#### Complexity: runtime = O(N), space = O(1)

# [1306](https://leetcode.com/problems/jump-game-iii/)
```python
def canReach(self, arr: List[int], start: int) -> bool:
   return self.dfs(arr, start) > 0
   
def dfs(self, arr, idx):
   if idx >= len(arr) or idx < 0 or arr[idx] < 0:
      return False
   elif arr[idx] == 0:
      return True
   else:
      arr[idx] = -arr[idx]
      return self.dfs(arr, idx+arr[idx]) or self.dfs(arr, idx-arr[idx])
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N)

# [1345](https://leetcode.com/problems/jump-game-iv/)
```python
from collections import defaultdict
def minJumps(self, arr: List[int]) -> int:
   size = len(arr)
   if size == 1:
      return 0
   book = defaultdict(list)
   visited = set()
   for idx, val in enumerate(arr):
      book[val] += [idx]
   queue = [0]
   cur_level = 0
   while queue:
      new_queue = []
      for cur_idx in queue:
         if cur_idx == size - 1:
            return cur_level
         if cur_idx not in visited:
            visited.add(cur_idx)
            if cur_idx + 1 < size and cur_idx + 1 not in visited:
               new_queue += [cur_idx+1]
            if cur_idx - 1 >= 0 and cur_idx-1 not in visited:
               new_queue += [cur_idx-1]
            for same in book[arr[cur_idx]]:
               if same != cur_idx and same not in visited:
                  new_queue += [same]
            book[arr[cur_idx]] = []
      queue = new_queue
      cur_level += 1
   return -1
```
#### Note: Utilize BFS to do level traversal, search and update queue for each level, reduce time complexity 
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(N)

# [1345](https://leetcode.com/problems/jump-game-iv/)
```python
from collections import defaultdict
def minJumps(arr):
   size = len(arr)
   if size == 1:
      return 0
   book = defaultdict(list)
   visited = set()
   for idx, val in enumerate(arr):
      book[val] += [idx]
   queue = [0]
   cur_level = 0
   while queue:
      new_queue = []
      for cur_idx in queue:
         if cur_idx == size - 1:
            return cur_level
         if cur_idx not in visited:
            visited.add(cur_idx)
            if cur_idx + 1 < size and cur_idx + 1 not in visited:
               new_queue += [cur_idx+1]
            if cur_idx - 1 >= 0 and cur_idx-1 not in visited:
               new_queue += [cur_idx-1]
            for same in book[arr[cur_idx]]:
               if same != cur_idx and same not in visited:
                  new_queue += [same]
            book[arr[cur_idx]] = []
      queue = new_queue
      cur_level += 1
   return -1
```
#### Note: BOTTOM UP with iteration
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(N)

# [1340](https://leetcode.com/problems/jump-game-v/)
```python
def maxJumps(self, arr, d):
   dp = [0] * len(arr)
   maxi = 0
   for i in range(len(arr)):
      maxi = max(maxi, self.dfs(arr, d, i, dp))
   return maxi
   
def dfs(self, arr, d, idx, dp):
   if dp[idx] > 0:
      return dp[idx]
   maxi = 0
   for k in range(idx-1, max(idx-d, 0)-1, -1):
      if arr[idx] <= arr[k]:
         break
      maxi = max(maxi, self.dfs(arr, d, k, dp))
   for k in range(idx+1, min(idx+d+1, len(arr))):
      if arr[idx] <= arr[k]:
         break
      maxi = max(maxi, self.dfs(arr, d, k, dp))
   dp[idx] = maxi + 1
   return dp[idx]
```
#### Note: TOP DOWN method with recursion
#### Assumption: N = the number of elements in the given list, D = the length of distance to jump
#### Complexity: runtime = O(ND), space = O(N)

# [239](https://leetcode.com/problems/sliding-window-maximum/)
```python
def main(nums, k):
   res = []
   queue = deque()
   for idx, val in enumerate(nums):
      while queue and nums[queue[-1]] < val:
         queue.pop()
      queue += [idx]
      if queue[0] == idx - k:
         queue.popleft()
      if idx >= k - 1:
         res += [nums[queue[0]]]
   return res
```
#### Note: Sliding window, utilize deque, pop right when the list value is smaller than the current value, pop right when the index is out of bound, if the index hit the k-1, it means the first element of the queue is the maximum of the current window, append it to the result output.
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N)

# [1696](https://leetcode.com/problems/jump-game-vi/)
```python
def main(nums, k):
   size = len(nums)
   dp = [0] * size
   dp[0] = nums[0]
   queue = deque()
   queue += [0]
   for i in range(1, size):
      if queue and queue[0] < i - k:
         queue.popleft()
      dp[i] = dp[queue[0]] + nums[i]
      while queue and dp[i] >= dp[queue[-1]]:
         queue.pop()
      queue += [i]
   return dp[-1]
```
#### Note: Sliding window, utilize deque
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N)

# [1176](https://leetcode.com/problems/diet-plan-performance/)
```python
def dietPlanPerformance(calories, k, lower, upper):
   cur = sum(calories[:k])
   score = 0
   if cur > upper:
      score += 1
   if cur < lower:
      score -= 1
   for i in range(k, len(calories)):
      cur += calories[i] - calories[i - k]
      if cur > upper:
         score += 1
      if cur < lower:
         score -= 1
   return score     
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)
```python
def dietPlanPerformance(calories, k, lower, upper):
   cur = sum(calories[:k])
   score = 0
   for i in range(k-1, len(calories)):
      if i - k >= 0:
         cur += calories[i] - calories[i - k]
      score += int(cur > upper)
      score -= int(cur < lower)
   return score
```
#### Assumption: N = the number of elements in the given list
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
