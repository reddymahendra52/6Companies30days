# 5. Stock Span Problem
## GFG(Geeks For Geeks)
### Prompt:
The stock span problem is a financial problem where we have a series of **n** daily price quotes for a stock and we need to calculate the span of stock’s price for all **n** days. 
The span **Si** of the stock’s price on a given day **i** is defined as the maximum number of consecutive days just before the given day, for which the price of the stock on the current day is less than or equal to its price on the given day.
For example, if an array of 7 days prices is given as {100, 80, 60, 70, 60, 75, 85}, then the span values for corresponding 7 days are {1, 1, 1, 2, 1, 4, 6}.

```java
class Solution
{
    //Function to calculate the span of stockâ€™s price for all n days.
    public static int[] calculateSpan(int price[], int n)
    {
        // Your code here
         int [] result = new int[n];
        result[0] = 1;
        for (int i=1; i<n; i++) {
            result[i] = 1;
            for (int j = i-1; j>=0; j -= result[j]) {
                if (price[j] > price[i]) 
                    break;  
                result[i] += result[j];
            }
        }
        return result;
    }
    
}

```

# Similar Question
## Leetcode(901)
### Prompt:
Design an algorithm that collects daily price quotes for some stock and returns **the span** of that stock's price for the current day.

The **span** of the stock's price today is defined as the maximum number of consecutive days (starting from today and going backward) for which the stock price was less than or equal to today's price.
* For example, if the price of a stock over the next 7 days were `[100,80,60,70,60,75,85]`, then the stock spans would be `[1,1,1,2,1,4,6]`.
Implement the `StockSpanner` class:
* `StockSpanner()` Initializes the object of the class.
* int `next(int price)` Returns the **span** of the stock's price given that today's price is `price`.

```java

class StockSpanner {

   Stack<int[]> s;
    
    public StockSpanner() {
        s = new Stack<>();
    }
    
    
    public int next(int price) {
        int span = 1;
        while (!s.isEmpty() && price >= s.peek()[0]) { 
            span += s.peek()[1];
            s.pop();
        }
        s.push(new int[]{price, span});
        return span; 
    }
}

/**
 * Your StockSpanner object will be instantiated and called as such:
 * StockSpanner obj = new StockSpanner();
 * int param_1 = obj.next(price);
 */

```
