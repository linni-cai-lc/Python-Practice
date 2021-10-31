# Python-Practice

# Week 79 [2/28-3/6]

# [1598](https://leetcode.com/problems/crawler-log-folder/)
```python
def main(logs):
    PARENT = '../'
    CURRENT = './'
    cur = 0
    for i in logs:
        if i == PARENT:
            cur = max(0, cur-1)
        elif i == CURRENT:
            pass
        else:
            cur += 1
    return cur
```
#### Assumption: N = the number of elements in the log list
#### Complexity: runtime = O(N), space = O(1)

# [1945](https://leetcode.com/problems/sum-of-digits-of-string-after-convert/)
```python
def main(s, k):
    cur = ''
    for i in s:
        cur += str(ord(i) - ord('a') + 1)
    while k > 0:
        k -= 1
        new_cur = 0
        for i in cur:
            new_cur += int(i)
        cur = str(new_cur)
    return int(cur)      
```
#### Assumption: N = the length of the given string, K = the number of conversions
#### Complexity: runtime = O(logN * K), space = O(logN * K)
```python
def main(s, k):
    cur = ''
    for i in s:
        cur += str(ord(i) - ord('a') + 1)
    while k > 0:
        k -= 1
        cur = str(sum(list(map(int, list(cur)))))
    return int(cur)      
```
#### Assumption: N = the length of the given string, K = the number of conversions
#### Complexity: runtime = O(logN * K), space = O(logN * K)

# [2046](https://leetcode.com/problems/sort-linked-list-already-sorted-using-absolute-values/)
```python
def main(head):
    pre = head
    cur = head.next
    while cur:
        if cur.val < 0:
            pre.next = cur.next
            cur.next = head
            head = cur
            cur = pre.next
        else:
            pre = cur
            cur = cur.next
    return head
```
#### Assumption: N = the number of nodes in the list
#### Complexity: runtime = O(N), space = O(1)

# [1725](https://leetcode.com/problems/number-of-rectangles-that-can-form-the-largest-square/)
```python
def main(rectangles):
    maxi_width = 0
    maxi_cnt = 0
    for i, j in rectangles:
        cur_width = min(i, j)
        if cur_width > maxi_width:
            maxi_width = cur_width
            maxi_cnt = 1
        elif cur_width == maxi_width:
            maxi_cnt += 1
    return maxi_cnt          
```
#### Assumption: N = the number of rectangle elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [1935](https://leetcode.com/problems/maximum-number-of-words-you-can-type/)
```python
def main(text, brokenLetters):
    cnt = 0
    broken = set(brokenLetters)
    for i in text.split(' '):
        if not set(i).intersection(broken):
            cnt += 1
    return cnt
```
#### Assumption: W = the number of words in the given text, B = the number of broken letters
#### Complexity: runtime = O(W*B), space = O(W+B)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
