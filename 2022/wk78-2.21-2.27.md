# Python-Practice

# Week 78 [2/21-2/27]

# [1903](https://leetcode.com/problems/largest-odd-number-in-string/)
```python
def main(num):
    for i in range(len(num), -1, -1):
        if int(num[i-1]) % 2 == 1:
            return num[:i]
    return ""
```
#### Assumption: N = the length of the given number string
#### Complexity: runtime = O(N), space = O(1)

# [1455](https://leetcode.com/problems/check-if-a-word-occurs-as-a-prefix-of-any-word-in-a-sentence/)
```python
def main(sentence, searchWord):
    lst = sentence.split(" ")
    for idx, val in enumerate(lst):
        if val.startswith(searchWord):
            return idx + 1
    return -1
```
#### Assumption: N = the length of the sentence
#### Complexity: runtime = O(N), space = O(1)

# [1491](https://leetcode.com/problems/average-salary-excluding-the-minimum-and-maximum-salary/)
```python
def main(salary):
    return (sum(salary) - max(salary) - min(salary)) / (len(salary) - 2)
```
#### Assumption: N = the number of elements in the given salary list
#### Complexity: runtime = O(N), space = O(1)

# [314](https://leetcode.com/problems/binary-tree-vertical-order-traversal/)
```python
def main(root)
    book = {}
    
    def dfs(idx, cur, level):
        if not cur:
            return
        if idx not in book:
            book[idx] = {}
        if level not in book[idx]:
            book[idx][level] = []
        book[idx][level] += [cur.val]
        dfs(idx-1, cur.left, level+1)  
        dfs(idx+1, cur.right, level+1)

    dfs(0, root, 0)
    res = []
    for idx in sorted(book.keys()):
        lst = []
        for level in sorted(book[idx].keys()):
            lst += book[idx][level]
        res += [lst]
    return res
```
#### Assumption:
- N = the number of nodes in the tree
- w = the width of the tree
- H = the height of the tree
#### Complexity: runtime = O(W*logH), space = O(N)

# [2047](https://leetcode.com/problems/number-of-valid-words-in-a-sentence/)
```python
def main(sentence):
    cnt = 0
    HYPHEN = '-'
    PUNCTUATION = '!.,'
    SPACE = ' '
    for word in sentence.split(' '):
        size = len(word)
        if size > 0:
            valid = True
            hyphen_cnt = 0
            for i in range(size):
                cur = word[i]
                if cur.isdigit() or cur == SPACE:
                    valid = False
                    break
                elif cur.islower():
                    continue
                elif cur == HYPHEN:
                    if hyphen_cnt == 0 and 0 < i < size - 1 and word[i-1].islower() and word[i+1].islower():
                        hyphen_cnt += 1
                    else:
                        valid = False
                        break
                elif cur in PUNCTUATION and i == size - 1:
                    continue
                else:
                    valid = False
                    break
            if valid:
                cnt += 1
    return cnt
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [1933](https://leetcode.com/problems/check-if-string-is-decomposable-into-value-equal-substrings/)
```python
def main(s):
    two_cnt = 0
    pre = None
    cnt = 1
    for i in s:
        if i == pre:
            cnt += 1
        else:
            if not pre or cnt % 3 == 0:
                pass
            elif cnt == 2 or (cnt - 2) % 3 == 0:
                two_cnt += 1
            else:
                return False
            if two_cnt > 1:
                return False
            cnt = 1
        pre = i
    if (cnt - 2) % 3 == 0:
        two_cnt += 1
    return two_cnt == 1 and not(pre and cnt == 1)
```
#### Assumption: N = the length of the given string
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
