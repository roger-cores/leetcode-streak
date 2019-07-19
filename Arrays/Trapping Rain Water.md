
# Trapping Rain Water

https://leetcode.com/problems/trapping-rain-water/

- Time: O(n)
- Space: O(n)


```python
class Solution:
    # Time: O(n)
    # One pass over the data, each height will 
    # be appended and popped at most once
    # Space: O(n) for the two stacks
    def trap(self, height: List[int]) -> int:
        count = 0
        
        # stacks to keep track of traps between walls
        stack, rev_stack = [], []
        start_height, end_height = 0, 0
        
        # For each height
        for i in range(0, len(height)):
            
            # traverse from right to left
            if height[0-i-1] <= end_height:
                rev_stack.append(height[0-i-1])
            else:
                while rev_stack:
                    count += end_height - rev_stack.pop()
                end_height = height[0-i-1]
            
            # traverse from left to right
            if height[i] < start_height:
                stack.append(height[i])
            else:
                while stack:
                    count += start_height - stack.pop()
                start_height = height[i]
        return count
```
