# Python-Practice
## Week 7 [6.15-6.21]

## [230](https://leetcode.com/problems/kth-smallest-element-in-a-bst/) Kth Smallest Element in a BST
  - Utilize stack to store left nodes, and 
  - stack = []
  - val = None
  - while k > 0:
    - while root:
      - stack.append(root)
      - root = root.left
    - root = stack.pop(-1)
    - k -= 1
    - val = root.val
    - root = root.right
 - return val
 - O(H + k) `AC`

## [98](https://leetcode.com/problems/validate-binary-search-tree/) Validate Binary Search Tree
  - main(root):
    - return recursive(root, -sys.maxsize, sys.maxsize)
  - recursive(root, mini, maxi):
    - if not root: return True
    - return mini < root.val < maxi and recursive(root.left, mini, root.val) and recursive(root.right, root.val, maxi)
    - O(N) `AC`

## [110](https://leetcode.com/problems/balanced-binary-tree/) Balanced Binary Tree
  - main(root):
    - if not root: return True
    - return abs(recursive(root.left) - recursive(root.right)) <= 1 and main(root.left) and main(root.right)
  - recursive(root):
    - if not root: return 0
    - return max(1+recursive(root.left),1+recursive(root.right))
  - O(N) `AC`

## [101](https://leetcode.com/problems/symmetric-tree/) Symmetric Tree
  - main(root):
    - return not root or (root and recursive(root.left, root.right))
  - recursive(L,R):
    - if not L and not R: return True
    - if not L or not R: return False
    - return L.val == R.val and helper(L.left, R.right) and helper(L.right, R.left)
  - O(N) `AC `

## [226](https://leetcode.com/problems/invert-binary-tree/) Invert Binary Tree
  - if not root: return root
  - temp = root.left
  - root.left = invertTree(root.right)
  - root.right = invertTree(temp)
  - return root
  - O(N) `AC`

## 56  Merge Intervals
## 75 Sort Colors
## 373 Find K Pairs with Smallest Sums
## 692 Top K Frequent Words
## 450 Delete Node in a BST
## 110 Balanced Binary Tree
## 287 Find the Duplicate Number
## 775 Global and Local Inversions
## 53 Maximum Subarray (DP and Divide and Conquer approach)
## 295  Find Median from Data Stream
## 410 Split Array Largest Sum 
## 668 Kth Smallest Number in Multiplication Table
