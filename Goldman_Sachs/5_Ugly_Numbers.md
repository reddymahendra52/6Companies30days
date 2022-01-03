# 5. Ugly Numbers

## GFG(Geeks For Geeks)
### Prompt: 
Ugly numbers are numbers whose **only prime factors** are **2, 3 or 5.** The sequence 1, 2, 3, 4, 5, 6, 8, 9, 10, 12, 15, … shows the first 11 ugly numbers. By convention, 1 is included. Write a program to find **Nth** Ugly Number.

```java
class Solution {
    /* Function to get the nth ugly number*/
    long getNthUglyNo(int n) {
        // code here
        long[] dp = new long[n+1];
        dp[1] = 1;
        
        int p2 = 1;
        int p3 = 1;
        int p5 = 1;
        
        for(int i=2; i <=n ; i++){
            long f1 = 2 * dp[p2];
            long f2 = 3 * dp[p3];
            long f3 = 5 * dp[p5];
            
            long min = Math.min(f1,Math.min(f2,f3));
            dp[i] = min;
            
            if(min == f1){
                p2++;
            }
            if(min == f2){
                p3++;
            }
            if(min == f3){
                p5++;
            }
            
        }
        
        return dp[n];
        
    }
}


```

## Similar Question
## LeetCode (263)
### Prompt:
An ugly number is a positive integer whose prime factors are limited to **2, 3, and 5.**

Given an integer n, return true if n is an **ugly number.**

```java
class Solution {
    public boolean isUgly(int n) {
        if(n<=0)
            return false;
        
        int[] arr = {2,3,5};
        
        for(int prime : arr){
            while(n%prime == 0){
                n = n / prime;
            }
        }
        
        
        return n==1;
        
    }
}

```

