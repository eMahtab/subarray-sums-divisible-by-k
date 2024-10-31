# Subarray sums divisible by k
## https://leetcode.com/problems/subarray-sums-divisible-by-k

Given an integer array nums and an integer k, return the number of non-empty subarrays that have a sum divisible by k.

A subarray is a contiguous part of an array. 
```
Example 1:
Input: nums = [3,4,1,6,2,5], k = 7
Output: 6
Explanation: There are 6 subarrays with a sum divisible by k = 7:
[3,4], [1,6], [3,4,1,6], [2,5], [1,6,2,5], [3,4,1,6,2,5]

Example 2:

Input: nums = [4,5,0,-2,-3,1], k = 5
Output: 7
Explanation: There are 7 subarrays with a sum divisible by k = 5:
[4, 5, 0, -2, -3, 1], [5], [5, 0], [5, 0, -2, -3], [0], [0, -2, -3], [-2, -3]

Example 3:

Input: nums = [5], k = 9
Output: 0
```

## Constraints:

1. 1 <= nums.length <= 3 * 10^4
2. -10^4 <= nums[i] <= 10^4
3. 2 <= k <= 10^4

## Implementation :
```java
class Solution {
    public int subarraysDivByK(int[] nums, int k) {
        int runningSum = 0;
        Map<Integer,Integer> map = new HashMap<>(); // remainders
        int count = 0;
        map.put(0, 1);
        int n = nums.length;
        for(int i = 0; i < n; i++) {
            runningSum += nums[i];
            int mod = runningSum % k;
            if(mod < 0)
              mod += k;

            if(map.containsKey(mod)) {
                count += map.get(mod);
            }
            map.put(mod, map.getOrDefault(mod,0)+1);
        }
        return count;
    }
}
```
