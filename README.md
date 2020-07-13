# Python-Practice

# Week 9 7/6-7/12
# [977](https://leetcode.com/problems/squares-of-a-sorted-array/)
  - find min absolute, take it as median
  - median is the first element, use two pointers move left and move right
  ## find min absolute
  - mid = 0
  - diff = sys.maxsize
  - for idx, val in enumerate(A):
    - if abs(val) < diff:
      - mid = idx
      - diff = abs(val)
  ## initialize two pointers
  - l, r = mid-1, mid+1
  - res = [A[mid]**2]
  ## loop through symmetric array
  - while l >= 0 and r < len(A):
    - if A[r] < abs(A[l]):
      - res.append(A[r]**2) # smaller right
      - r += 1
    - else:
      - res.append(A[l]**2) # smaller left
      - l -= 1
  ## explore rest array
  - while l >= 0:
    - res.append(A[l]**2)
    - l -= 1
  - while r < len(A):
    - res.append(A[r]**2)
    - r += 1
  - return res
  - runtime: O(N), space: O(N), two passes

# [88](https://leetcode.com/problems/merge-sorted-array/)
  - place larger numbers in nums1 and nums2 in the back of nums1
  - utilize index track backwards
  ## initialize
  - idx1, idx2, idx = m-1, n-1, m+n-1
  ## track backwards
  - while idx1 >= 0 and idx2 >= 0:
    - if nums1[idx1] < nums2[idx2]:
      - nums1[idx] = nums2[idx2] # put larger element of nums2
      - idx2 -= 1
    - else:
      - nums1[idx] = nums1[idx1] # put larger element of nums1
      - idx1 -= 1
    - idx -= 1
  - nums1[:idx2+1] = nums2[:idx2+1] # put smaller element of nums2
  - runtime: O(N+M), space: O(1)
  
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
  
  
