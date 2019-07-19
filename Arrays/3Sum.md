
# 3Sum

https://leetcode.com/problems/3sum/

- Time: O(n^2)
- Space: O(n chose 3)



```python
class Solution:
    
    # Time: O(n^2)
    # Space: O(n chose 3) when all numbers are unique 
    # and all possible triplets are valid
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        results = []
        
        # O(n log n)
        nums.sort()
        
        # O(n^2)
        for i in range(0, len(nums)-2):
            
            # Skip over duplicates
            if i > 0 and nums[i-1] == nums[i]:
                continue
                
            # Solve 2Sum with nums[i] 
            # as third member of the triplet
            left, right = i+1, len(nums)-1
            
            while left < right:
                current_sum = nums[i] + nums[left] + nums[right]
                if current_sum > 0:
                    right -= 1
                elif current_sum < 0:
                    left += 1
                else:
                    results.append([nums[i], nums[left], nums[right]])
                    left += 1
                    right -= 1
                    while left < right and nums[left] == nums[left-1]:
                        left += 1
                    while left < right and nums[right] == nums[right+1]:
                        right -= 1
                    
            
        return results
```
