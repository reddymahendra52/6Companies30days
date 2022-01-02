# 3. Count the subarrays having product less than k
## GFG(Geeks For Geeks)
### Prompt
Given an array of positive numbers, the task is to find the number of possible contiguous subarrays having product less than a given number k.

```java
class Solution {
    
    public int countSubArrayProductLessThanK(long a[], long n, long k)
    {
         if(k<=1) return 0;
        
        long prod = 1;
        int count = 0;
        
        int left = 0;
        int right = 0;
        
        while(right < n){
            prod = prod * a[right];
            
            while(prod >= k ){
                prod = prod/a[left];
                left++;
            }
            
            count = count + right - left + 1;
            right++;
            
        }
        
        return count;
    }
}

```
## Similar Question
## LeetCode (713)
### Prompt:
Given an array of integers **nums** and an integer **k**, return the number of contiguous subarrays where the product of all the elements in the subarray is strictly less than **k**.

```java

class Solution {
    public int numSubarrayProductLessThanK(int[] nums, int k) {
        
        if(k<=1) return 0;
        
        int prod = 1;
        int count = 0;
        
        int left = 0;
        int right = 0;
        
        while(right < nums.length){
            prod = prod * nums[right];
            
            while(prod >= k ){
                prod = prod/nums[left];
                left++;
            }
            
            count = count + right - left + 1;
            right++;
            
        }
        
        return count;
    }
}

```


