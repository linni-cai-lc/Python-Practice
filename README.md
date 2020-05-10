# Python-Practice

## Week 1 [5.4-5.10]
### Tree Data Structure Practice
- Binary Search		
  - [74](https://leetcode.com/problems/search-a-2d-matrix/)
    - brute force O(N^2) loop through all elements `AC`
  - [33](https://leetcode.com/problems/search-in-rotated-sorted-array/submissions/)
    - brute force O(N) loop through all elements `AC`
  - [81](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/submissions/)
    - brute force O(N) loop through all elements `AC`
  - [153](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
    - brute force O(N) loop through all elements `AC`

- Tree Traversal: `recurstion` + `iterative`
  #### Binary Tree
  - [144](https://leetcode.com/problems/binary-tree-preorder-traversal/)
    - pre-order: root->left->right
    - recursive O(N) loop through all elements `AC`
    - iterative O(N) use stack, store right->left `AC`  
  - [94](https://leetcode.com/problems/binary-tree-inorder-traversal/)
    - in-order: left->root->right
    - recursive O(N) loop through all elements `AC`
    - iterative O(N) use stack, store right->root->left in visited `AC`
  - [145](https://leetcode.com/problems/binary-tree-postorder-traversal/)
    - post-order: left->right->root
    - recursive O(N) loop through all elements `AC`
    - iterative O(N) use stack, store root->right->left in visited `AC`
  - [102](https://leetcode.com/problems/binary-tree-level-order-traversal/)
    - level-order: top->bottom, for each level, left->right
    - recursive O(N) loop through all elements `AC`
    - iterative O(N) use queue to store (node, level), left->right `AC`
  - [107](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)
    - level-order: bottom->top, for each level, left->right
    - recursive O(N) loop through all elements `AC`
    - iterative O(N) use queue to store (node, level), left->right `AC`
  ### N-ary Tree
  - [429](https://leetcode.com/problems/n-ary-tree-level-order-traversal/)
    - level-order: top->bottom, for each level, children left->children right
    - recursive O(N) loop through all elements `AC`
    - iterative O(N) use queue to store (node, level), left->right `AC`
  - [589](https://leetcode.com/problems/n-ary-tree-preorder-traversal/)
    - pre-order: root->children left->children right
    - recursive O(N) loop through all elements `AC`
    - iterative O(N) use stack, store right->left `AC`   
  - [590](https://leetcode.com/problems/n-ary-tree-postorder-traversal/)
    - post-order: children left->children right->root
    - recursive O(N) loop through all elements `AC`
    - iterative O(N) use stack, store root->right->left in visited `AC`
