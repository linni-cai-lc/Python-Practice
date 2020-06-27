# Python-Practice

## Week 8 [6.22-6.28]

## [108](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/) Convert Sorted Array to Binary Search Tree
  - utilize pre-order
  - main(nums):
    - return preorder(nums, 0, len(nums)-1)
  - preorder(nums, L, R):
    - if L > R: return None
    - else:
      - M = (L+R)//2 # get the middle node
      - root = TreeNode(nums[mid])
      - root.left = preorder(nums, L, mid-1) # escape the middle node, recursive through left subtree
      - root.right = preorder(nums, mid+1, R) # escape the middle node, recursive through right subtree
      - return root
  - runtime: O(N), space: O(N) `AC` 

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
