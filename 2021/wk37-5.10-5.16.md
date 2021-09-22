# Python-Practice

# Week 37 [5/10-5/16]

# [566](https://leetcode.com/problems/reshape-the-matrix/)
```python
def main(nums, r, c):
    if not nums or not nums[0] or r * c != len(nums) * len(nums[0]):
        return nums
    new_m = [[0] * c for _ in range(r)]
    cur_r = 0
    cur_c = 0
    for i in range(len(nums)):
        for j in range(len(nums[0])):
            new_m[cur_r][cur_c] = nums[i][j]
            cur_c += 1
            if cur_c == c:
                cur_c = 0
                cur_r += 1
    return new_m
```
#### Assumption: M = the number of rows in the given nums matrix, N = the number of columns in the given nums matrix, R = the number size of r, C = the number size of c
#### Complexity: runtime = O(MN), space = O(1) excluding result matrix

# [1337](https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/)
```python
from collections import Counter
def main(mat, k):
    book = Counter()
    for i in range(len(mat)):
        book[i] = -sum(mat[i])
    return [x[0] for x in book.most_common()[:k]]
```
#### Assumption: M, N = the matrix dimension M x N, K = the result size
#### Complexity: runtime = O(MN), space = O(M)

# [1184](https://leetcode.com/problems/distance-between-bus-stops/)
```python
def main(distance, start, destination):
    mini = min(start, destination)
    maxi = max(start, destination)
    forward = sum(distance[mini:maxi])
    backward = sum(distance[:mini])+sum(distance[maxi:])
    return min(forward, backward)
```
```python
def main(distance, start, destination):
    mini = min(start, destination)
    maxi = max(start, destination)
    forward = 0
    for i in range(mini, maxi):
        forward += distance[i]
    backward = 0
    for i in range(mini):
        backward += distance[i]
    for i in range(maxi, len(distance)):
        backward += distance[i]
    return min(forward, backward)
```
#### Note: sometimes calculating sum without slicing might be faster
#### Assumption: N = the number of elements in the distance list
#### Complexity: runtime = O(N), space = O(1)

# [374](https://leetcode.com/problems/guess-number-higher-or-lower/)
```python
def main(n):
    low = 0
    high = n
    while low <= high:
        mid = (low + high) // 2
        res = guess(mid)
        if res == 0:
            return mid
        elif res < 0:
            high = mid-1
        else:
            low = mid+1
    return -1
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(logN), space = O(1)

# [1417](https://leetcode.com/problems/reformat-the-string/)
```python
def main(s):
    letter = []
    number = []
    for i in s:
        if i.isnumeric():
            number += [i]
        else:
            letter += [i]
    size_n = len(number)
    size_l = len(letter)
    if size_n != 1 and size_l != 1 and (size_n == 0 or size_l == 0 or abs(size_n - size_l) > 1):
        return ""
    res = ""
    if size_n == size_l:
        for i in range(size_l):
            res += letter[i] + number[i]
    elif size_n > size_l:
        res += number[0]
        for i in range(size_l):
            res += letter[i] + number[i+1]
    else:
        res += letter[0]
        for i in range(size_n):
            res += number[i] + letter[i+1]
    return res
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)
```python
def main(s):
stack_letter = []
    stack_number = []
    pre_num = False
    res = ""
    size_number = 0
    size_letter = 0
    for i in s:
        if i.isnumeric():
            size_number += 1
            if not pre_num:
                pre_num = True
                res += i
            elif stack_letter:
                res += stack_letter.pop(0) + i
            else:
                stack_number += [i]
        else:
            size_letter += 1
            if pre_num:
                pre_num = False
                res += i
            elif stack_number:
                res += stack_number.pop(0) + i
            else:
                stack_letter += [i]
    rest_letter = len(stack_letter)
    rest_number = len(stack_number)
    if rest_letter == 2 and size_number > 0:
        res = stack_letter.pop(0) + res + stack_letter.pop(0)
    elif size_letter - size_number == 1:
        res = stack_letter.pop(0) + res
    elif size_number - size_letter == 1 and rest_number == 1:
        res += stack_number.pop(0)
    elif stack_letter and size_number == size_letter:
        res += stack_letter.pop(0)
    elif stack_letter or stack_number:
        res = ""
    return res
```
#### Note: improve to one-pass iteration
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)

# [748](https://leetcode.com/problems/shortest-completing-word/)
```python
from collections import Counter, defaultdict as dd
def main(licensePlate, words):
    book = Counter(licensePlate.lower())
    mini = sys.maxsize
    res = ""
    for i in words:
        curBook = Counter(i.lower())
        cnt = 0
        for j in book.keys():
            if j.isalpha():
                if j in curBook and book[j] <= curBook[j]:
                    cnt += book[j]
                else:
                    cnt = -1
                    break
        if cnt > -1 and len(i) < mini:
            res = i
            mini = len(i)
    return res
```
#### Assumption: L = the length of the license plate, W = the number of words
#### Complexity: runtime = O(LW), space = O(L+W)

# [598](https://leetcode.com/problems/range-addition-ii/)
```python
def main(m, n, ops):
    for i in ops:
        m = min(m, i[0])
        n = min(n, i[1])
    return m * n
```
#### Utilize a trick that each operation is start from the left upper corner, in row/col index, left upper corner is the minimum corner
#### Assumption: N = the number of operations
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