# 2. Longest Mountain in Array

## Leetcode(845)
### Prompt:
You may recall that an array arr is a **mountain array** if and only if:
* `arr.length >= 3`
* There exists some index i **(0-indexed)** with `0 < i < arr.length - 1` such that:
    * `arr[0] < arr[1] < ... < arr[i - 1] < arr[i]`
    * `arr[i] > arr[i + 1] > ... > arr[arr.length - 1]`
Given an integer array `arr`, return the length of the longest subarray, which is a mountain. Return `0` if there is no mountain subarray.

```java

class Solution {
    public int longestMountain(int[] arr) {
        int res = 0;
        int n = arr.length;
        
        for(int i=1; i < n ; i++){
            int count = 1;
            boolean flag = false;
            
            
            //increasing sequence
            int j = i;
             
            while(j<n && arr[j] > arr[j-1]){
                j++;
                count++;
            }
            
            //decreasing sequence
            
            while(i!=j && j<n && arr[j]<arr[j-1]){
                j++;
                count++;
                flag = true;
            }
            
            //max of length
            
            if(i!=j && flag && count>2){
                res = Math.max(res,count);
                j--;
            }
            
            i=j;
            
        }
        
        return res;
    }
}

```
