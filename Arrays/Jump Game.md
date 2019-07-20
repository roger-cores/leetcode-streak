
# Jump Game I

https://leetcode.com/problems/jump-game/

- Time: O(n)
- Space: O(1) | On reusing input array
- Space: O(n) | If input can't be edited

Best case can be improved further by only considering zeroes


```python
class Solution:
    # Time: O(n)
    # Space: O(1) | if array is reused for counts
    # Space: O(n) | if original array can't be edited
    
    # Best case can be improved by only considering zeroes
    def canJump(self, nums: List[int]) -> bool:
        
        # Corner cases
        if not nums or len(nums) == 0:
            return False
        
        if len(nums) == 1:
            return True
        
        if nums[0] >= len(nums) - 1:
            return True
        
        # Last Index is reachable trivially
        nums[-1] = 1
        
        # From second last element to 0th
        # Collects running counts of blocks 
        # that can reach last element from n-2 to 0
        for i in range(len(nums)-2, -1, -1):
            # If last element is reachable in one step
            if i + nums[i] >= len(nums)-1:
                # Set nums[i] to count at nums[i+1] + 1
                nums[i] = nums[i+1] + 1
            elif nums[i+1] - nums[i + nums[i] + 1] != 0:
                nums[i] = nums[i+1] + 1
            else:
                # No reachable path through this element
                # Do not increment count
                nums[i] = nums[i+1]
        
        return nums[0] != nums[1]
```
