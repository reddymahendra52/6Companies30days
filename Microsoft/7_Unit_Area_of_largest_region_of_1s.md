# 7. Unit Area of largest region of 1's 
## GFG(Geeks For Geeks)
### Prompt:

Given a grid of dimension **nxm** containing 0s and 1s. Find the unit area of the largest region of 1s.
Region of 1's is a group of 1's connected 8-directionally (horizontally, vertically, diagonally).

```java
class Solution
{
    //Function to find unit area of the largest region of 1s.
    public int findMaxArea(int[][] grid)
    {
        // Code here
    
     int result=0;
       for(int i=0;i<grid.length;i++) {
           for(int j=0;j<grid[0].length;j++) {
               if(grid[i][j] == 1) {
                   int num = search(i,j,grid);
                   result = result > num ? result : num;
               }
           }
       }
       return result;
   }
   
   public int search(int i,int j, int[][]grid) {
       
       if(i < 0 || j<0 || i >= grid.length || j >= grid[0].length || grid[i][j] == 0 ) 
           return 0;
       
       grid[i][j] = 0;
       int sum = 0;
       sum += search(i+1,j,grid);
       sum += search(i,j+1,grid);
       sum += search(i,j-1,grid);
       sum += search(i-1,j,grid);
       
       sum += search(i+1,j+1,grid);
       sum += search(i-1,j-1,grid);
       sum += search(i+1,j-1,grid);
       sum += search(i-1,j+1,grid);
       return sum + 1;
   }    
}  

```
