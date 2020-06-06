# Python-Practice
# Week 5 6.1-6.7

## Linked List 
  - [24](https://leetcode.com/problems/swap-nodes-in-pairs/)
  - one pass through the linked list, and have temporary constant number of pointers
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
