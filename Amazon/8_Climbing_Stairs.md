# 8. Count ways to N'th Stair(Order does not matter)
## GFG(Geeks For Geeks)
### Prompt:
There are **N** stairs, and a person standing at the bottom wants to reach the top. The person can climb either **1 stair or 2 stairs at a time**. Count the number of ways, 
the person can reach the top (**order does not matter**).
**Note:** Order does not matter means for n=4 {1 2 1},{2 1 1},{1 1 2} are considered same.

```java
class Solution
{
    //Function to count number of ways to reach the nth stair 
    //when order does not matter.
    Long countWays(int m)
    {
        // your code here
        long[] dp = new long[m+1];
        dp[0] = 1;
        dp[1] = 1;
        long   mod = 1000000007;
        for(int i=2 ; i <=m ; i++){
            dp[i] = (dp[i-2]+1)%mod;
        }
        
        return dp[m]%mod;
    }    
}
```

# Similar Question
## Climbing Stairs/ Leetcode (70)
### Prompt:
You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

```java

class Solution {
    public int climbStairs(int n) {
        int[] dp = new int[n+1];
        dp[0] = 1;
        dp[1] = 1;
        for(int i=2 ; i <=n ; i++){
            dp[i] = dp[i-1]+dp[i-2];
        }
        
        return dp[n];
    }
}

```
