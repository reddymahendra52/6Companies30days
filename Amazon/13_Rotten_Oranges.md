# 13. Rotten Oranges
## Leetcode(994)
### Prompt:
You are given an `m x n` grid where each cell can have one of three values:

* 0 representing an empty cell,
* 1 representing a fresh orange, or
* 2 representing a rotten orange.
Every minute, any fresh orange that is **4-directionally** adjacent to a rotten orange becomes rotten.

Return the minimum number of minutes that must elapse until no cell has a fresh orange. If this is impossible, return `-1`.

```java

class Solution {
    public int orangesRotting(int[][] grid) {
        Queue<int[]> q = new LinkedList();
        
        int freshCount = 0;
        for(int i=0 ; i < grid.length ; i++){
            for(int j=0; j < grid[i].length ; j++){
                if(grid[i][j] == 2){
                    q.add(new int[]{i,j});
                }
                if(grid[i][j] == 1){
                    freshCount++;
                }
            }
        }
        
        int[][] direction = {{1,0},{0,1},{-1,0},{0,-1}};
        int time = 0;
        
        while(!q.isEmpty() && freshCount > 0){
            time++;
            int size = q.size();
            while(size-- > 0){
                int[] xy = q.poll();
                for(int[] d : direction){
                    int x = xy[0] + d[0];
                    int y = xy[1] + d[1];
                    
                    if(x<0 || y<0 || x>= grid.length || y>=grid[x].length || grid[x][y] == 0 || grid[x][y] == 2)
                        continue;
                    
                    q.add(new int[]{x,y});
                    grid[x][y] = 2;
                    freshCount--;
                    
                }
            }
        }
        
        return freshCount == 0 ? time: -1;
        
    }
}

```
