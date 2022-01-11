# 4. Matrix in Spiral Form
## GFG(Geeks For Geeks)
### Prompt:
Given a matrix of size r*c. Traverse the matrix in spiral form.

```java
class Solution
{
    //Function to return a list of integers denoting spiral traversal of matrix.
    static ArrayList<Integer> spirallyTraverse(int matrix[][], int r, int c)
    {
        // code here 
        ArrayList<Integer> res = new ArrayList<>();
        
        if(matrix.length == 0 ) return res;
        
        int rowBegin = 0;
        int rowEnd = matrix.length - 1;
        int colBegin = 0;
        int colEnd = matrix[0].length - 1;
        
        while(rowBegin <= rowEnd && colBegin <= colEnd){
            
            for(int i= colBegin; i <=colEnd ; i++){
                res.add(matrix[rowBegin][i]);
            }
            
            rowBegin++;
            
            for(int i= rowBegin; i <=rowEnd ; i++){
                res.add(matrix[i][colEnd]);
            }
            
            colEnd--;
            
            if(rowBegin <= rowEnd){
                for(int i= colEnd ; i>=colBegin ; i--){
                    res.add(matrix[rowEnd][i]);
                }
            }
            
            rowEnd--;
            
            if(colBegin <= colEnd){
                for(int i= rowEnd ; i>=rowBegin ; i--){
                    res.add(matrix[i][colBegin]);
                }
            }
            
            colBegin++;
            
        }
        
         return res;
    }
}


```

# Similar Question
## Leetcode(54)
### Prompt:
Given an m x n matrix, return all elements of the matrix in spiral order.

```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        
        List<Integer> res = new ArrayList();
        
        if(matrix.length == 0 ) return res;
        
        int rowBegin = 0;
        int rowEnd = matrix.length - 1;
        int colBegin = 0;
        int colEnd = matrix[0].length - 1;
        
        while(rowBegin <= rowEnd && colBegin <= colEnd){
            
            for(int i= colBegin; i <=colEnd ; i++){
                res.add(matrix[rowBegin][i]);
            }
            
            rowBegin++;
            
            for(int i= rowBegin; i <=rowEnd ; i++){
                res.add(matrix[i][colEnd]);
            }
            
            colEnd--;
            
            if(rowBegin <= rowEnd){
                for(int i= colEnd ; i>=colBegin ; i--){
                    res.add(matrix[rowEnd][i]);
                }
            }
            
            rowEnd--;
            
            if(colBegin <= colEnd){
                for(int i= rowEnd ; i>=rowBegin ; i--){
                    res.add(matrix[i][colBegin]);
                }
            }
            
            colBegin++;
            
        }
        
         return res;
        
    }
}

```
