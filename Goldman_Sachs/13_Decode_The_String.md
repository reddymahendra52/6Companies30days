# 13. Decode the string

## GFG(Geeks For Geeks)/ Leetcode (394)
### Prompt: 
The encoding rule is: `k[encoded_string]`, where the encoded_string inside the square brackets is being repeated exactly `k` times. Note that `k` is guaranteed to be a positive integer.

You may assume that the input string is always valid; there are no extra white spaces, square brackets are well-formed, etc.

Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, `k`. For example, there will not be input like `3a` or `2[4]`.

```java
class Solution {
    public String decodeString(String s) {
        Stack<Integer> counts = new Stack();
        Stack<String> result = new Stack();
        String res = "";
        int index = 0;
        
        while(index < s.length()){
            if(Character.isDigit(s.charAt(index))){
                int count = 0;
                while(Character.isDigit(s.charAt(index))){
                    count = 10 * count + (s.charAt(index) - '0');
                    index += 1; 
                }
              counts.push(count);  
            }else if (s.charAt(index) == '['){
                result.push(res);
                res = "";
                index += 1;
            }else if (s.charAt(index) == ']'){
                StringBuilder temp = new StringBuilder(result.pop());
                int count = counts.pop();
                for(int i=0 ; i < count ; i++){
                    temp.append(res);
                }
                res = temp.toString();
                index += 1;
            }else {
                res += s.charAt(index);
                index += 1; 
            }
            
        }
        
        return res;
        
    }
}

```
