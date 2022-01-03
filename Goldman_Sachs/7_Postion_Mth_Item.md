# 7. Find the position of M-th item 

## GFG(Geeks For Geeks)
### Prompt: 
**M** items are to be delivered in a circle of size **N**. Find the position where the **M-th** item will be delivered if we start from a given position **K**. Note that items are distributed at adjacent positions starting from **K**.

```java
class Solution {
    static int findPosition(int n , int m , int k) {
        // code here
        if (m <= n - k + 1)
            return m + k - 1;

        m = m - (n - k + 1);
 
        return (m % n == 0) ? n : (m % n);
        
    }
};

```
