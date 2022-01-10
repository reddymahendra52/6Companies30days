# 9. Nuts And Bolts Problem
## GFG(Geeks For Geeks)
### Prompt:
Given a set of **N** nuts of different sizes and **N** bolts of different sizes. There is a one-one mapping between nuts and bolts. Match nuts and bolts efficiently.

Comparison of a nut to another nut or a bolt to another bolt is not allowed. It means nut can only be compared with bolt and bolt can only be compared with nut to see 
which one is bigger/smaller.
The elements should follow the following order ! # $ % & * @ ^ ~ .

```java

class Solution {
    void matchPairs(char nuts[], char bolts[], int n) {
        // code here
        HashMap<Character,Integer>match=new HashMap<>();
        for(int i=0;i<n;i++)
        {
            match.put(nuts[i],i);
        }
        for(int i=0;i<n;i++)
        {
             if(match.containsKey(bolts[i]))
             nuts[i]=bolts[i];
            
        }
        Arrays.sort(nuts);
        Arrays.sort(bolts);
    }
}

```
