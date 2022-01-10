# 9. Valid Sudoku
## GFG(Geeks For Geeks)
### Prompt:
Given an incomplete Sudoku configuration in terms of a 9x9  2-D square matrix(**mat[][]**) the task to check if the current configuration is valid or not where a 0 represents an empty block.
Note: Current valid configuration does not ensure validity of the final solved sudoku. 

```java
class Solution{
    static int isValid(int mat[][]){
        // code here
        HashSet<String>  seen = new HashSet<>();
        
        for(int i=0; i < mat.length ; i++){
            for(int j=0; j < mat[i].length; j++){
                int current_val = mat[i][j];
                if(current_val != 0 ){
                    if(!seen.add(current_val + "found in row"+ i) || 
                       !seen.add(current_val + "found in col"+ j) ||
                       !seen.add(current_val + "found in subbox"+ i/3 + "-" + j/3) ) return 0;
                }
                
                
            }
        }
        
        return 1 ;
    }
}

```

# Similar Question
## Leetcode(36)
### Prompt:
Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated **according to the following rules:**

1. Each row must contain the digits `1-9` without repetition.
2. Each column must contain the digits `1-9` without repetition.
3. Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.

```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        HashSet<String>  seen = new HashSet();
        
        for(int i=0; i < 9 ; i++){
            for(int j=0; j < 9; j++){
                char current_val = board[i][j];
                if(current_val != '.'){
                    if(!seen.add(current_val + "found in row"+ i) || 
                       !seen.add(current_val + "found in col"+ j) ||
                       !seen.add(current_val + "found in subbox"+ i/3 + "-" + j/3) ) return false;
                }
                
                
            }
        }
        
        return true;
    }
}

```
