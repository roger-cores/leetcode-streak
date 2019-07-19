
# 3Sum Closest

https://leetcode.com/problems/3sum-closest/

- Time: O(n^2)
- Space: O(1)


```python
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        
        # start with any sum
        # improve with each iteration
        closest_sum = nums[0] + nums[1] + nums[2]
        # minimize the distance
        min_distance = abs(target - closest_sum)
        
        # O(n log n)
        nums.sort()
        
        # O(n^2)
        for i in range(0, len(nums)-2):
            if i > 0 and nums[i-1] == nums[i]:
                continue
            left, right = i+1, len(nums)-1
            
            # Solve 2Sum closest with third number as nums[i]
            while left < right:
                current_sum = nums[i] + nums[left] + nums[right]
                distance = current_sum - target
                if min_distance > abs(distance):
                    min_distance = abs(distance)
                    closest_sum = current_sum
                
                if distance < 0:
                    left += 1
                elif distance > 0:
                    right -= 1
                else:
                    return target
            
        return closest_sum
```
