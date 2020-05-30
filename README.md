# Python-Practice
## Week 4 [5.25-5.31]
- [206](https://leetcode.com/problems/reverse-linked-list/)
  - linked list
    - 1->   2->3->4->5
      ^     ^
      cur   nex
  - 1->None
    ^
    pre
    - 2->   3->4->5
      ^     ^
      cur   nex
  - 2->1->None
    ^
    pre
    - 3->   4->5
      ^     ^
      cur   nex 
  - 3->2->1->None
    ^
    pre
    - 4->   5
      ^     ^
      cur   nex
  - 4->3->2->1->None
    ^
    pre
    - 5->   None
      ^     ^
      cur   nex
  - 5->4->3->2->1->None
    ^
    pre
    - None
      ^     
      cur   
  - pre = None
  - cur = head
  - while cur:
    - nex = cur.next
    - cur.next = pre
    - pre = cur
    - cur = nex
  - return pre
  - O(N) `AC`
- [237](https://leetcode.com/problems/delete-node-in-a-linked-list/)
  - linked list
  - replace the current node with the next node
  - O(1) `AC`
- [1061](https://leetcode.com/problems/lexicographically-smallest-equivalent-string/)
  - union find
  - find(i)
    - if book[i] != i: book[i]=find(book[i])
    - return book[i]
  - union(a,b)
    - fa, fb = find(a), find(b)
    - if fa = fb: return
    - if fa < fb: book[fb] = fa
    - else: book[fa] = fb
  - for a,b in zip(A,B):
    - if a != b: book = book.union(a,b)
  - for i in S:
    - result += book.find(i)
- O((A+S)log(A)) `AC`  # A and B same length



- [148]()
- [19]()
- [206]()
- [160]()
- [2]()
- [237]()
- [169]()
- [215]()
- [5]()
- [154]()
- [654]()
- [153]()
