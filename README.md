# Python-Practice

# Week 9 7/6-7/12

# [23](https://leetcode.com/problems/merge-k-sorted-lists/)
  - utilize heap to sort list node
  - in python, unless having `__lt__` in object class definition, 
    we'll need idx to avoid clashes in heapq push
  ## initialize
  - q = []
  - idx = 0 # to prevent clash
  ## build heap
  - for i in lists:
  - if i:
    - heappush(q, (i.val, idx, i))
    - idx += 1
  ## merge sort
  - dummy = LN(-1)
  - cur = dummy
  - while res:
    - _, _, temp = heappop(res)
    - cur.next = temp # append element into result
    - cur = cur.next # update to next pointer
    - if cur.next:
      - heappush(q, (cur.next.val, idx, cur.next))
      - idx += 1
  - return dummy.next
  ## runtime O(NlogK), space O(K)
  ## N: the number of elements of all linked lists
  ## K: the number of linked lists
  
  
