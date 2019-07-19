
# Set Matrix Zeroes

https://leetcode.com/problems/set-matrix-zeroes/

- Time: O(mn)
- Space: O(1)

A rather complicated and lenthy solution to save on space


```python
class Solution:
    # Time: O(mn)
    # Space: O(1) | First row and column are used to store O(m+n) information
    def setZeroes(self, matrix: List[List[int]]) -> None:
        
        if len(matrix) == 0:
            return
        
        if len(matrix[0]) == 0:
            return
        
        n, m = len(matrix), len(matrix[0])
        
        # Convenience function for strict equal
        def is_equal(val1, val2):
            return val1 == val2 and type(val1) == type(val2)
        
        
        # One mn pass
        for i in range(n):
            for j in range(m):
                
                if matrix[i][j] == 0:
                    
                    if j == 0 and (is_equal(matrix[0][j], True) or is_equal(matrix[0][j], 0)):
                        matrix[0][j] = 0
                    else:
                        matrix[0][j] = False
                    
                    if i == 0 and (is_equal(matrix[i][0], False) or is_equal(matrix[i][0], 0)):
                        matrix[i][0] = 0
                    else:
                        matrix[i][0] = True
                    
        # Two mn passes
        for j in range(1, m):
            if is_equal(matrix[0][j], False):
                for i in range(1, n):
                    matrix[i][j] = 0
                    
        for i in range(1, n):
            if is_equal(matrix[i][0], True):
                for j in range(1, m):
                    matrix[i][j] = 0
                    
                    
        # Two m+n passes
        origin = matrix[0][0]
        if is_equal(origin, 0) or is_equal(origin, True):
            for j in range(m):
                matrix[0][j] = 0
        if is_equal(origin, 0) or is_equal(origin, False):
            for i in range(n):
                matrix[i][0] = 0
                
        for i in range(n):
            if is_equal(matrix[i][0], True):
                matrix[i][0] = 0
        for j in range(m):
            if is_equal(matrix[0][j], False):
                matrix[0][j] = 0
                    
        
        
```
