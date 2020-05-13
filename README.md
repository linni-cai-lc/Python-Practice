# Python-Practice
## Week 2 [5.11-5.17]
- [240](https://leetcode.com/problems/search-a-2d-matrix-ii)
  - sorted 2D matrix search
  - row = height - 1, col = 0, starts at left bottom corner
  - cur < target: col++
  - cur > target: row--
  - cur = target: True
  - O(n + m) `AC`
- [34](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
  - array binary search
  - extreme find via binary search
  - O(logN) `AC`
- [875](https://leetcode.com/problems/koko-eating-bananas/)
  - array binary search
  - use math.ceil to calculate the number of hours to eat -> compare sum with target
  - reduce eat time from large to small
  - O(NlogM) `AC`

### Divide and Conquer
- [215]()
- [23](https://leetcode.com/problems/merge-two-sorted-lists/)
  - go through both lists
  - connect with rest list after while loop
  - O(n + m) `AC`
- [21]()
- [53]()
- [241]()
- [169]()
- [167]()
