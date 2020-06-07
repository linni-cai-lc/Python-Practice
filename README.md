# Python-Practice
# Week 5 6.1-6.7

## Hash Table
  - [373](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/)
  - brute force
    - make pairs of length k^2
    - sort by key=lambda x:x[0]+x[1]
    - return lst[:k]
    - O(k^2) `AC`
  - heap
    - for i in range(k);
      - if A[RA] <= B[RB]:  # if current A is small, loop through RB
        - for j in B[RB:]: heapq.heappush(heap, (A[RA], j))
        - RA += 1
      - else:  # if current B is small, loop through RA
        - for j in A[RA:]: heapq.heappush(heap, (j, B[RB]))
        - RB += 1
    - return heapq.nsmallest(k, heap, key=sum)
    - O(klogk) `AC`

## Hash Table
  - [692](https://leetcode.com/problems/top-k-frequent-words/)
  - c = Counter(words).most_common()
  - c = sorted(c, key=lambda i:(-i[1], i[0]))  # first sort count DESC, then sort word alphabetically ASC
  - return [i for i,j in c[:k]]
  - O(N) `AC`

## Hash Table
  - [202](https://leetcode.com/problems/happy-number/)
  - visit = set()
  - sumi = n
  - while sumi != 1:
    - lst = list(str(n))
    - sumi = sum([int(i)**2 for i in lst])
    - if sumi in visit: return False
    - visit.add(sumi)
  - return True
  - O(N) `AC`
  
## Hash Table
  - [771](https://leetcode.com/problems/jewels-and-stones/)
  - j = set(J)
  - return sum([1 for i in S if i in j])
  - we convert J into a set j, then searching i in j costs O(1), otherwise it will be O(N)
  - runtime: O(N); space: O(N) `AC`

## Hash Table
  - [205](https://leetcode.com/problems/isomorphic-strings/)
  - build two hash dict, each key is string letter
  - for i in range(len(s)):
    - if s[i] in sb and sb[s[i]] != t[i]: return False
    - elif t[i] in tb and tb[t[i]] != s[i]: return False
    - else: sb[s[i]] = t[i], tb[t[i]] = s[i]
  - return True
  - runtime: O(N); space: O(N) `AC`

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
