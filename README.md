# Python-Practice
## Week 6 [6.8-6.14]

## Divide and Conquer	775
## Divide and Conquer	53
## Divide and Conquer	295*
## Divide and Conquer	84
## BST	450
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
  


