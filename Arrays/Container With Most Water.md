
# Container With Most Water

https://leetcode.com/problems/container-with-most-water/

- Time: O(n)
- Space: O(1)


```python
class Solution:
    # Time: O(n)
    # Space: O(1)
    def maxArea(self, height: List[int]) -> int:
        # i points to first item
        # j points to last item
        i, j, max_area = 0, len(height) - 1, 0
        
        # O(n)
        while i < j:
            area = (j-i) * min(height[i], height[j])
            max_area = max(max_area, area)
            
            # Maximize the height by eliminating
            # the shorted height among the two
            if height[i] < height[j]:
                i += 1
            else:
                j -= 1
        return max_area
```
