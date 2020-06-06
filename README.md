# Python-Practice
# Week 5 6.1-6.7

## Linked List
  - [61](https://leetcode.com/problems/rotate-list/)
  - constant number of multiple passes through the linked list, and constant number of temporary pointers.
  - if not head or k == 0 or not head.next: return head
  - temp = head, S = 0
  - while temp:  # get linked list length
    - S += 1, temp = temp.next
  - k %= S  # get rid of repeated rotates
  - if k == 0: return head  # original sequence
  - idx = S-k+1  # get index of expected head node
  - temp = head, cnt = 0
  - while cnt < idx-2:  # get node before expected head node
    - temp = temp.next, cnt += 1
  - headEnd = temp  # get pre-node of expected head node
  - cur = headEnd.next  # get expected head node
  - headEnd.next = None  # disconnect linked list ends with pre-node and linked list starts with expected head
  - temp = cur
  - while temp.next:  # get the end of linked list starts with expected head
    - temp = temp.next
  - curEnd = temp
  - curEnd.next = head  # connect the pre linked list
  - return cur  # linked list starts with expected head
  - O(N) `AC`

## Linked List 
  - [24](https://leetcode.com/problems/swap-nodes-in-pairs/)
  - one pass through the linked list, and constant number of temporary pointers
  - if not head or head.next: return head
  - dummy = ListNode(0)  # dummy head node, which allow us to get connect with first node for the first swap
  - curHead = dummy  # dynamic slower pointer
  - cur = head  # dynamic faster pointer
  - while cur and cur.next:
    - curHead.next = cur.next  # connect with the second of the pair
    - temp = cur  # get first of the pair
    - cur = cur.next.next  # update cur to the first of next pair
    - temp.next = None  # disconnect
    - curHead.next.next = temp  # connect with the first of the pair
    - curHead = curHead.next.next  # update curHead to the second of the pair, prepare for connection of next pair
  - if cur: curHead.next = cur  # connect to remaining odd node in the pair
  - return newHead.next  # remove dummy head and get the result
  - O(N) `AC` 
## sort+heapsort 	378
## sort+heapsort 	215
## Divide and Conquer	287
## Divide and Conquer	775
## Divide and Conquer	53
## Divide and Conquer	295*
## Divide and Conquer	84
## BST	450
## BST	98
## BST	1008
