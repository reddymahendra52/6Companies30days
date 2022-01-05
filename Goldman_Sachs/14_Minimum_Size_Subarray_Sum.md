# 14. Minimum Size Subarray Sum

## Leetcode(209)
### Prompt: 
Given an array of positive integers `nums` and a positive integer `target`, return the minimal length of a **contiguous subarray** `[numsl, numsl+1, ..., numsr-1, numsr]` of which the sum is greater than or equal to `target`. If there is no such subarray, return `0` instead.

```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int result = Integer.MAX_VALUE;
        
        int left = 0;
        int sum = 0;
        
        for(int i=0 ; i < nums.length ; i++){
            sum = sum + nums[i];
            
            while(sum >= target){
                result = Math.min(result , i+1 - left);
                sum = sum - nums[left];
                left++;
            }
        }
        
        return (result != Integer.MAX_VALUE) ? result : 0 ;
    }
}

```
