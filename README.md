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
  
def find_roman(self, num, num_digit, res):
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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
