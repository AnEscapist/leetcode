# Median of Two Sorted Arrays

## Description
There are two sorted arrays **nums1** and **nums2** of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

You may assume **nums1** and **nums2** cannot be both empty.

**Examples:**
```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```
```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```
**Tags:** Array, Binary Search, Divide and conquer

## Thoughts:
1: Merge these two arrays then sort and get the median. However, the time complexity of this method is O(m+n)log(m+n).

2: Use binary search:

  Let's start with how to find the k-th smallest number in these two arrays.
  
  If A = [1, 3, 5, 7], B = [2, 4, 6, 8, 9, 10], k = 7, k // 2 = 7 // 2 = 3. The 3rd element of A is A[2] = 5, the 3rd element of B is B[2] = 6.
  
  Since A[2] < B[2], A[0], A[1], A[2] cannot be the k-th smallest number. Then getKthSmallest(A, B, 7) equals to getKthSmallest(A', B, 4),
  where A' = [7].

# Solution
```python
class Solution:
    def getKthSmallest(self, A, B, k):
        lenA, lenB = len(A), len(B)
        if lenA > lenB: return self.getKthSmallest(B, A, k)
        if lenA == 0: return B[k-1]
        if k == 1: return min(A[0], B[0])
        pa = min(k//2, lenA)
        pb = k - pa
        if A[pa-1] < B[pb-1]:
            return self.getKthSmallest(A[pa:], B, pb)
        else:
            return self.getKthSmallest(A, B[pb:], pa)
    
    def findMedianSortedArrays(self, A, B):
        lenA, lenB = len(A), len(B)
        if (lenA + lenB) % 2 == 1:
            return self.getKthSmallest(A, B, (lenA + lenB) // 2 + 1)
        else:
            return (self.getKthSmallest(A, B, (lenA + lenB) // 2) + self.getKthSmallest(A, B, (lenA + lenB) // 2 + 1)) * 0.5
```
