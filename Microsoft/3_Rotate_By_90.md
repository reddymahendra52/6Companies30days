# Rotate By 90 Degree
## GFG(Geeks For Geeks)
### Prompt:
Given a square **matrix[][]** of size **N x N**. The task is to rotate it by **90 degrees in an anti-clockwise** direction without using any extra space.

```java
class GFG
{
    static void rotate(int matrix[][]) 
    {
        // Code Here
        int N = matrix.length;
        
        for(int i=0; i < N ; i++){
            for(int j=i ; j < N ; j++){
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        
        for(int i=0 ; i < N ; i++){
            for(int j=0 ; j<(N/2) ; j++){
                int temp = matrix[j][i];
                matrix[j][i] = matrix[N-1-j][i];
                matrix[N-1-j][i] = temp;
            }
        }
    }
}

```

# Similar Question
## Rotate Image Clockwise /Leetcode(48)
### Prompt:
You are given an `n x n` 2D `matrix` representing an image, rotate the image by **90** degrees (clockwise).

You have to rotate the image **in-place**, which means you have to modify the input 2D matrix directly. **DO NOT** allocate another 2D matrix and do the rotation.

```java
class Solution {
    public void rotate(int[][] matrix) {
        int N = matrix.length;
        
        for(int i=0; i < N ; i++){
            for(int j=i ; j < N ; j++){
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
       
        for(int i=0 ; i < N ; i++){
            for(int j=0 ; j<(N/2) ; j++){
                int temp = matrix[i][j];
                matrix[i][j] = matrix[i][N-1-j];
                matrix[i][N-1-j] = temp;
            }
        }
            
    }
}

```
