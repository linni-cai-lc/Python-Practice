# Python-Practice

# Week 67 [12/6-12/12]

# [388](https://leetcode.com/problems/longest-absolute-file-path/)
```python
def main(input):
   if '.' not in input:
      return 0
   lst = input.split('\n')
   book = []
   maxi = 0
   for i in lst:
      cnt = i.count('\t')
      book[cnt] = len(i) - cnt
      size = sum(book[:cnt+1]) + cnt
      if '.' in i and size > maxi:
         maxi = max(maxi, size)
   return maxi
```
#### Assumption:
- N = the length of the given input
#### Complexity: runtime = O(N), space = O(N)

# [565](https://leetcode.com/problems/array-nesting/)
```python
def main(nums):
   visited = set()
   maxi = 0
   for i in nums:
      if i not in visited:
         book = set()
         parent = i
         while parent not in visited:
            visited.add(parent)
            book.add(parent)
            parent = nums[parent]
         maxi = max(maxi, len(book]))
   return maxi
```
#### Assumption:
- N = the number of elements in the given array
#### Complexity: runtime = O(N), space = O(N)

# [1630](https://leetcode.com/problems/arithmetic-subarrays/)
```python
def main(nums, l, r):
   res = []
   for idx in range(len(l)):
      start = l[idx]
      end = r[idx]
      cur = sorted(nums[start:end+1])
      diff = cur[1] - cur[0]
      arith = True
      for i in range(2, len(cur)):
         if cur[i] - cur[i-1] != diff:
            arith = False
            break
      res += [arith]      
   return res
```
#### Assumption:
- N = the number of elements in the nums
- L = R = the length of sequences to check, L represents the start indices list, R represents the end indices list
- S = the size of each sequence to check
#### Complexity: runtime = O(LSlogS), space = O(L) the return result space

# [12](https://leetcode.com/problems/integer-to-roman/)
```python
def main(num):
   res = ""
   if num >= 1000:
      res += "M" * (num // 1000)
      num %= 1000
   if num >= 900:
      res += "CM"
      num -= 900
   if num >= 500:
      res += "D"
      num -= 500
   if num >= 400:
      res += "CD"
      num -= 400
   if num >= 100:
      res += "C" * (num // 100)
      num %= 100
   if num >= 90:
      res += "XC"
      num -= 90
   if num >= 50:
      res += "L"
      num -= 50
   if num >= 40:
      res += "XL"
      num -= 40
   if num >= 10:
      res += "X" * (num // 10)
      num %= 10
   if num >= 9:
      res += "IX"
      num -= 9
   if num >= 5:
      res += "V"
      num -= 5
   if num >= 4:
      res += "IV"
      num -= 4
   if num >= 1:
      res += "I" * (num // 1)
      num %= 1
   return res
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(1), space = O(N)
```python
def main(num: int) -> str:
   res, num = find_roman(num, 100, "")
   res, num = find_roman(num, 10, res)
   res, num = find_roman(num, 1, res)
   res, num = find_roman(num, 0.1, res)
   return res
  
def find_roman(num, num_digit, res):
   book = {
      1: 'I',
      5: 'V',
      10: 'X',
      50: 'L',
      100: 'C',
      500: 'D',
      1000: 'M'
   }
   num_bound = [10, 9, 5, 4]
   for idx in range(len(num_bound)):
      bound_digit = num_bound[idx]
      bound = int(bound_digit * num_digit)
      if num >= bound and bound > 0:
         if bound_digit == 10:
            res += book[bound] * (num // bound)
            num %= bound
         else:
            if bound_digit == 9 or bound_digit == 4:
               res += book[num_digit] + book[(bound_digit + 1) * num_digit]
            else:
               res += book[bound]
            num -= bound
   return [res, num]
```
#### Note: cleaner structure to remove code redundancy
#### Assumption: N = the given number size
#### Complexity: runtime = O(1), space = O(N)
```python
def main(num):
   book = {
      1: 'I',
      5: 'V',
      10: 'X',
      50: 'L',
      100: 'C',
      500: 'D',
      1000: 'M'
   }
   num_bounds = [10, 9, 5, 4]
   num_digits = [100, 10, 1, 0.1]
   res = ""
   for num_digit in num_digits:
      for num_bound in num_bounds:
         bound = int(num_bound * num_digit)
         if num >= bound and bound > 0:
            times = num // bound if num_bound == 10 else 1
            add = book[num_digit] + book[(num_bound + 1) * num_digit] if num_bound in (4, 9) else book[bound]
            res += add * times
            num -= bound * times
   return res
```
#### Note: cleaner structure to remove code redundancy, better performance
#### Assumption: N = the given number size
#### Complexity: runtime = O(1), space = O(N)

# [912](https://leetcode.com/problems/sort-an-array/)
```python
def main（nums):
   return sorted(nums)
```
#### Note: use python built-in sort function as base comparison
#### Assumption: N = the number of elements in the list
#### Complexity: runtime = O(NlogN), space = O(1)
```python
def main(nums):
   size = len(nums)
   if size in (0, 1):
      return nums
   mid = size // 2
   left = main(nums[:mid])
   right = main(nums[mid:])
   return merge(left, right)

def merge(left, right):
   res = []
   left_ptr = right_ptr = 0
   left_size, right_size = len(left), len(right)
   while left_ptr < left_size and right_ptr < right_size:
      if left[left_ptr] < right[right_ptr]:
         res += [left[left_ptr]]
         left_ptr += 1
      else:
         res += [right[right_ptr]]
         right_ptr += 1
   if left_ptr < left_size:
      res += left[left_ptr:]
   if right_ptr < right_size:
      res += right[right_ptr:]
   return res
```
#### Note: merge sort with recursion, divide and conquer
#### Assumption: N = the number of elements in the list
#### Complexity: runtime = O(NlogN), space = O(N)
```python
def main(nums):
   quick_sort(nums, 0, len(nums)-1)
   return nums

def quick_sort(nums, left, right):
   if right <= left: return
   pivot_idx = partition(nums, left, right)
   quick_sort(nums, left, pivot_idx-1)
   quick_sort(nums, pivot_idx+1, right)

def swap(nums, left, right):
   nums[left], nums[right] = nums[right], nums[left]

def partition(nums, left, right):
   mid_idx = (left + right) // 2
   left_val = nums[left]
   right_val = nums[right]
   mid_val = nums[mid_idx]
   median = min(max(left_val, right_val), mid_val)
   if mid_val == median:
      swap(nums, mid_idx, right)
   elif left_val == median:
      swap(nums, left, right)
   pivot_val = nums[right]
   separator_idx = left
   for i in range(left, right):
      if nums[i] < pivot_val:
         swap(nums, i, separator_idx)
         separator_idx += 1
   swap(separator_idx, right)
   return separator_idx
```
#### Note: quick sort with recursion, in-place sort, divide and conquer
#### Assumption: N = the number of elements in the list
#### Complexity: runtime = O(NlogN), space = O(logN) due to recursion call stack

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
