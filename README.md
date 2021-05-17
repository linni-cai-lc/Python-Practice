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

# []()
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
            flip_maxi = cnt                    
         else:
            maxi = max(maxi, cnt)
            cnt -= flip_maxi - 1
            flip_maxi = cnt       
   return max(maxi, cnt)
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
