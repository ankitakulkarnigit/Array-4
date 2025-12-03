# Array-4

## Problem1 Array partition (https://leetcode.com/problems/array-partition/)

## Problem2 Maximum Subarray (https://leetcode.com/problems/maximum-subarray/)

Time: O(n)
Space: O(1)
iterate through, find running current sum. If nums[i] > currSum + nums[i] then set that as start of subarray else continue

class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        currSum = nums[0]
        maxSum = nums[0]
        start = 0
        end = 0
        currStart = 0
        for i in range(1,len(nums)):
            if nums[i] > currSum + nums[i]:
                currSum = nums[i]
                currStart = i
            else:
                currSum += nums[i]

            if currSum > maxSum:
                maxSum = currSum
                start = currStart
                end = i
        # print(nums[start:end+1])
        return maxSum
        


## Problem3  Next permutation(https://leetcode.com/problems/next-permutation/)
