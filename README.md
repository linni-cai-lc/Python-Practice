# Python-Practice
## Week 6 [6.8-6.14]

## Math	[775](https://leetcode.com/problems/global-and-local-inversions/)
  - mini = len(A)
  - for i in range(len(A)-1,-1,-1):
    - mini = min(mini, A[i])
    - if i >= 2 and A[i-2] > mini: return False # EXIST more global inversion than local inversion
  - return True
  - O(N) `AC`

## Set	[53](https://leetcode.com/problems/maximum-subarray/)
  - sumi = maxi = A[0]
  - for i in A[1:]:
    - sumi = max(i, sumi+i)
    - maxi = max(maxi, sumi)
  - return maxi
  - O(N) `AC`

## Heap [295](https://leetcode.com/problems/find-median-from-data-stream/)
  - normal sort O(NlogN) `AC`
  - two heaps
  - small, large = [], [] 
  - ### both are min heap, to maintain order, small will be negative min heap 
  - ### i.e. min 1,2,3->-3-2,-1 popmin=-3 
  - ### i.e. max 4,5,6 popmin = 4
  - add num:
    - heappush(large, num)
    - heappush(small, -heappop(large))
    - if len(large) < len(small):
      - heappush(large, -heappop(small))
  - find mid
    - if len(large) > len(small):
      - return large[0]
    - return (large[0]-small[0])/2
  - O(logN) `AC`
  
## Stack [84](https://leetcode.com/problems/largest-rectangle-in-histogram/)
  - stack = [-1] # it prevents the last element out of scope, converts the area to be negative
  - maxi = 0
  - for i in range(len(heights)):
    - while len(stack) > 1 and heights[stack[-1]] >= heights[i]:
      - maxi = max(maxi, heights[stack.pop(-1)] * (i - stack[-1] - 1))
  - while len(stack) > 1:
    - maxi = max(maxi, heights[stack.pop(-1) * (len(heights) - stack[-1] - 1))
  - O(N) `AC`

## BST [450](https://leetcode.com/problems/delete-node-in-a-bst/)
  - most_left:
    - while root.left: root = root.left
  - most_right:
    - while root.right: root = root.right
  - delete:
    - if not root: return None
    - val = root.val
    - if val > key: root.left = delete(root.left, key)
    - if val < key: root.right = delete(root.right, key)
    - if val = key:
      - if not root.left and not root.right: return None
      - elif root.left:
        - root.val = most_right(root.left).val
        - root.left = delete(root.left, key)
      - else: # root.right
        - root.val = most_left(root.right).val
        - root.right = delete(root.right, key)
    - return root
    - if root has left, find predecessor, the largest node smaller than root
    - if root has right, find successor, the smallest node larger than root
    - O(logN) `AC`

## BST [98](https://leetcode.com/problems/validate-binary-search-tree/) 
  - check bst recursively, LEFT < ROOT < RIGHT
  - in main function:
    - reutrn recursive(A, -sys.maxsize, sys.maxsize)
  - in recursive function:
    - if not root: return True
    - val = root.val
    - return mini < val < maxi and helper(A, mini, val) and helper(A, val, maxi)
  - O(N) `AC`

## BST [1008](https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/)
  - in main function:
    - global idx = 0
    - return recursive(A, -sys.maxsize, sys.maxsize)
  - in recursive function:
    - if idx >= len(A): return None # out of scope
    - val = A[idx] # catch the current key
    - root = None # initialize root
      - if mini < val < maxi: # correctly locate the position of bst node
      - idx += 1 # increment to next node
      - root = TreeNode(val) # allocate current node
      - root.left = recursive(A, mini, val) # assign the children of current node
      - root.right = recursive(A, val, maxi) # assign the children of current node
    - return root
  - O(N) `AC`

## Divide and Conquer	[287](https://leetcode.com/problems/find-the-duplicate-number/)
  - utilize set
  - s = set(A)
  - return (sum(A)-sum(s))//(len(A)-len(s))
  - total cost: O(N) `AC`

## sort+heapsort 	[215](https://leetcode.com/problems/kth-largest-element-in-an-array/)
  - heapq.nlargest(k, A)[k-1]
  - total cost: O(klogN) `AC`

## sort+heapsort 	[378](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)
  - utilize min heap
  - m = len(A)
  - build a heap of first element of each row
  - for i in range(min(k, m)): heap.append((A[i][0], i, 0)) # val, row, col
  - heapq.heapify(heap)
  - decrement k to 0, do delete min and insert larger val in the next col
  - while k:
    - val, row, col = heapq.heappop(heap)
    - if col<m-1: heapq.heappush(heap, (A[row][col+1], row, col+1))
    - k -= 1
  - return val
  - N: # elements in the matrix A
  - k: kth smallest
  - M: min(N, k)
  - heap build: O(M)
  - heap delete min: O(logM)
  - heap insert next col: O(logM)
  - k times delete: O(klogM)
  - total cost: O(M+klogM) `AC`  
  


