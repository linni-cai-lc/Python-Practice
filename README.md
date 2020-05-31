# Python-Practice
## Week 4 [5.25-5.31]
- [328](https://leetcode.com/problems/odd-even-linked-list/)
  - linked list
  - odd_head, even_head = LN(0), LN(0)
  - odd_cur, even_cur = oh, eh
  - cur = head
  - while cur
    - oc.next = cur  # get odd
    - oc = oc.next 
    - cur = cur.next
    - if cur: ec.next = cur, ec = ec.next, cur = cur.next  # get even
    - ec.next = None, oh = oh.next, oc.next = eh.next # remove first, odd connect to even
    - return oh
- [2](https://leetcode.com/problems/add-two-numbers/)
  - linked list
  - h1=l1, h2=l2, p1=l1, add=0
  - while h1 and h2
    - sumi = h1.val+h2.val+add
    - v1 = sumi%10
    - if sumi < 10: add = 0
    - else: add = sumi // 10
    - h1.val = v1
    - p1 = h1
    - h2.next and not h1.next: h1.next = ListNode(0)
    - h1.next and not h2.next: h2.next = ListNode(0)
    - h1 = h1.next, h2 = h2.next
  - if add: p1.next = ListNode(add)
  - return l1
  - O(M+N) `AC`  # M is the length of l1, N is the length of l2
- [141](https://leetcode.com/problems/linked-list-cycle/)
  - linked list
  - visited set
  - while head
    - if head in visited: return True
    - else: visited.add(head)
  - return False
  - O(N) `AC`
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
