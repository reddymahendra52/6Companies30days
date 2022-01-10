# 12. Column name from a given column number
## GFG(Geeks For Geeks)
### Prompt:
Given a positive integer, return its corresponding column title as appear in an Excel sheet.
Excel columns has a pattern like A, B, C, … ,Z, AA, AB, AC,…. ,AZ, BA, BB, … ZZ, AAA, AAB ….. etc. In other words, column 1 is named as “A”, column 2 as “B”, column 27 as “AA” and so on.

```java
class Solution
{
    String colName (long n)
    {
        // your code here
        String ans = "";
        while(n>0){
            n--;
            long val = n%26;
            char x = (char)(val + 65);
            ans = x + ans;
            n = n/26;
        }
        return ans;
    }
}

```

# Similar Question
## Excel Sheet Column Number /Leetcode(171)
### Prompt:
Given a string `columnTitle` that represents the column title as appear in an Excel sheet, return its corresponding column number.

```java
class Solution {
    public int titleToNumber(String s) {
        if (s == null) return -1;
        int sum = 0;
        // for each loop so we don't need to mess with index values.
        for (char c : s.toUpperCase().toCharArray()) {
            sum *= 26;
            sum += c - 'A' + 1;
        }
        return sum;
        
    }
}

```
