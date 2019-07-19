
# Search in Rotated Sorted Array

https://leetcode.com/problems/search-in-rotated-sorted-array/

- Time: O(log n)
- Space: O(1)


```python
class Solution:
    
    # Time: O(log n)
    # Space: O(1)
    def search(self, nums: List[int], target: int) -> int:
        
        # Classic BST approach
        low, high = 0, len(nums)-1
        while low <= high:
            mid = low + ((high - low) >> 1)
            if nums[mid] == target:
                return mid
            elif nums[mid] < nums[high]: # right side is sorted
                if target > nums[mid] and target <= nums[high]:
                    low = mid + 1
                else:
                    high = mid - 1
            else: # left side is sorted
                if target < nums[mid] and target >= nums[low]:
                    high = mid - 1
                else:
                    low = mid + 1
            
        return -1
```
