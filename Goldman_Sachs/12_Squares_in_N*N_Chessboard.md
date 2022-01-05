# 12. Squares in N*N Chessboard

## GFG(Geeks For Geeks)
### Prompt: 
Find total number of Squares in a N*N cheesboard.

```java
class Solution {
    static Long squaresInChessBoard(Long N) {
        // code here
        if(N==1) return (long)1;
        return (N*N)+squaresInChessBoard(N-1);
    }
};

```
