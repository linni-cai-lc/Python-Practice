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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
