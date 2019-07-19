
# Rotate Image

https://leetcode.com/problems/rotate-image/

- Time: O(n^2)
- Space: O(1)


```python
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        
        def swap(matrix, i, j, k, l):
            matrix[i][j], matrix[k][l] = matrix[k][l], matrix[i][j]
        
        n = len(matrix)
        
        i = 0
        
        # Runtime is O(n^2)
        # Space is O(1)
        
        # For each concentric square
        # There can be n/2 concentric circles
        while i < n:
            # For each element on the first row
            # loop executes n-1, n-3, n-5 etc times
            for j in range(n-1, i, -1):
                swap(matrix, i, j, j, n-1)
                swap(matrix, i, j, i+n-j-1, i)
                swap(matrix, i+n-j-1, i, n-1, i+n-j-1)
            i += 1
            n -= 1
```
