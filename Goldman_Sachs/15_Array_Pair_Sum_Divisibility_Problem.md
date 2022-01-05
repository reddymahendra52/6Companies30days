# 15. Array Pair Sum Divisibility Problem

## GFG(Geeks For Geeks)/Leetcode(1497)
### Prompt: 
Given an array of integers and a number k, write a function that returns true if given array can be divided into pairs such that sum of every pair is divisible by k.

```java

class Solution {
    public boolean canPair(int[] arr, int k) {
        // Code here
        int[] rmdfr = new int[k];
        for(int a : arr){
            int rmd = a % k;
            if(rmd < 0) rmd += k;
            rmdfr[rmd]++;
        }
        
        for(int i =1 ; i < k ; i++){
            if(rmdfr[i] != rmdfr[k-i])
                return false;
        }
        
        return rmdfr[0]%2 == 0;
    }
}

```
