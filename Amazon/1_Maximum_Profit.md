# 1. Calculating Maximum Profit 
## GFG(Geeks For Geeks)
### Prompt:
In the stock market, a person buys a stock and sells it on some future date. Given the stock prices of **N** days in an array **A[ ]** and a positive integer **K**,
 find out the maximum profit a person can make in at-most **K** transactions. A transaction is equivalent to (buying + selling) of a stock and new transaction 
can start only when the previous transaction has been completed.

```java
class Solution {
    static int maxProfit(int k, int N, int prices[]) {
        // code here
        int len = N;
        if(len<=1 || k<=0)
            return 0;
        
        int profit = 0;
        if(k>= len/2){
            for(int i=0 ; i < len-1 ; i++){
                if(prices[i] < prices[i+1])
                    profit = profit + prices[i+1] - prices[i];
            }
            return profit;
        }
        
        int[] buy = new int[k];
        Arrays.fill(buy,Integer.MIN_VALUE);
        int[] sell = new int[k];
        
        for(int i=0; i < N ; i++){
            for(int j=0 ; j < k ; j++){
                buy[j] = Math.max(buy[j], j==0 ? 0-prices[i] : sell[j-1]- prices[i]);
                sell[j] = Math.max(sell[j], buy[j]+prices[i]);
            }
        }
        
        return sell[k-1];
        
    }
}

```

# Similar Question
## Best Time to Buy and Sell Stock IV /Leetcode(188)
### Prompt:
You are given an integer array `prices` where `prices[i]` is the price of a given stock on the `ith` day, and an integer `k`.

Find the maximum profit you can achieve. You may complete at most `k` transactions.

**Note:** You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

```java

class Solution {
    public int maxProfit(int k, int[] prices) {
        int len = prices.length;
        if(len<=1 || k<=0)
            return 0;
        
        int profit = 0;
        if(k>= len/2){
            for(int i=0 ; i < len-1 ; i++){
                if(prices[i] < prices[i+1])
                    profit = profit + prices[i+1] - prices[i];
            }
            return profit;
        }
        
        int[] buy = new int[k];
        Arrays.fill(buy,Integer.MIN_VALUE);
        int[] sell = new int[k];
        
        for(int i=0; i < prices.length ; i++){
            for(int j=0 ; j < k ; j++){
                buy[j] = Math.max(buy[j], j==0 ? 0-prices[i] : sell[j-1]- prices[i]);
                sell[j] = Math.max(sell[j], buy[j]+prices[i]);
            }
        }
        
        return sell[k-1];
    }
}

```

