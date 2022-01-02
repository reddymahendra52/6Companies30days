# 4. Run Length Encoding 
## GFG(Geeks For Geeks)
### Prompt:
Given a string, Your task is to  complete the function **encode** that returns the **run length encoded** string for the given string.
**eg** if the input string is “wwwwaaadexxxxxx”, then the function should return “w4a3d1e1x6″.
You are required to complete the function **encode** that takes only one argument the string which is to be encoded and returns the encoded string.

```java
class GfG
 {
	String encode(String str)
	{
          //Your code here
          char[] ch = str.toCharArray();
        int cnt = 1;
        StringBuilder sb = new StringBuilder("");
        sb.append(ch[0]);
        for(int i = 1; i< ch.length;i++){
            if (ch[i] == ch[i-1]){
                cnt++;
            }else{
                sb.append(cnt);
                cnt = 1;
                sb.append(ch[i]);
            }
        }
        sb.append(cnt);
        return sb.toString();
	}
	
 }

```
