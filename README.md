# Array-4

## Problem1 Array partition (https://leetcode.com/problems/array-partition/)

Time: O(n) + O(k) where n is the size of hashmap and k is min to max val
Space: O(n) size of hashmap 

class Solution:
    def arrayPairSum(self, nums: List[int]) -> int:
        res = 0
        map = {}
        min_val = float('inf')
        max_val = float('-inf')

        for num in nums:
            map[num] = map.get(num, 0) + 1
            min_val = min(min_val, num)
            max_val = max(max_val, num)
        
        flag = True
        for i in range(min_val, max_val + 1):
            if i not in map:
                continue

            if not flag:
                map[i] -= 1
                flag = True

            frq = map[i]
            if frq % 2 == 0 and flag:
                res += (frq // 2) * i

            if frq % 2 == 1 and flag:
                res += ((frq // 2) * i) + i
                map[i] = 0
                flag = False
        
        print(map)            
        return res


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
