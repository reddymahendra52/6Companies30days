# 9. Number following a pattern 

## GFG(Geeks For Geeks)
### Prompt: 
Given a pattern containing only I's and D's. I for increasing and D for decreasing.
Devise an algorithm to print the minimum number following that pattern.
Digits from 1-9 and digits can't repeat.

```java
class Solution{
    static String printMinNumberForPattern(String arr){
        // code here
        int min_avail = 1, pos_of_I = 0;
 
              //vector to store the output
              ArrayList<Integer> al = new ArrayList<>();
               
              // cover the base cases
              if (arr.charAt(0) == 'I')
              {
                  al.add(1);
                  al.add(2);
                  min_avail = 3;
                  pos_of_I = 1;
              }
 
              else
              {
                  al.add(2);
                  al.add(1);
                  min_avail = 3;
                  pos_of_I = 0;
              }
 
              // Traverse rest of the input
              for (int i = 1; i < arr.length(); i++)
              {
                   if (arr.charAt(i) == 'I')
                   {
                       al.add(min_avail);
                       min_avail++;
                       pos_of_I = i + 1;
                   }
                   else
                   {
                       al.add(al.get(i));
                       for (int j = pos_of_I; j <= i; j++)
                            al.set(j, al.get(j) + 1);
 
                       min_avail++;
                   }
              }
              
              String res = "";
              
              for (int i = 0; i < al.size(); i++)
                    res = res + al.get(i);
              
              return res;
        
        
    }
}

```
