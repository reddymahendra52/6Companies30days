# 6. Greatest Common Divisor of Strings 

## Leetcode(1071)
### Prompt: 
For two strings `s` and `t`, we say **"t divides s"** if and only if `s = t + ... + t` (i.e., t is concatenated with itself one or more times).

Given two strings str1 and str2, return the largest string `x` such that `x` divides both `str1` and `str2`.

```java
class Solution {
    public String gcdOfStrings(String str1, String str2) {
        if (!(str1+str2).equals(str2+str1))  return "";
    
    int gcdVal = gcd(str1.length() , str2.length());
    return str2.substring(0, gcdVal);
    
    }

    public static int gcd(int p, int q) {
        if (q == 0) return p;
        else return gcd(q, p % q);
    }    
    
}

```
