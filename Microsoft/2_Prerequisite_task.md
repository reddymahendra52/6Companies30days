# 2. Prerequisite Tasks
## GFG(Geeks For Geeks)
### Prompt:
There are a total of N tasks, labeled from 0 to N-1. Some tasks may have prerequisites, for example to do task 0 you have to first complete task 1, 
which is expressed as a pair: [0, 1]
Given the total number of **tasks N** and a list of **prerequisite pairs P**, find if it is possible to finish all tasks.

```java
class Solution {
    public boolean isPossible(int numCourses, int[][] prerequisites)
    {
        // Your Code goes here
        List<Integer>[] graph = new ArrayList[numCourses];
        
        for(int i=0; i < numCourses ; i++){
            graph[i] = new ArrayList();
        }
        
        int[] indegree = new int[numCourses];
        for(int[] e: prerequisites){
            graph[e[0]].add(e[1]);
            indegree[e[1]]++;
        }
        
        Queue<Integer> queue = new LinkedList();
        
        for(int i=0; i < numCourses ; i++){
            if(indegree[i]==0)
                queue.add(i);
        }
        
        while(!queue.isEmpty()){
            int current = queue.poll();
            for(int c : graph[current]){
                indegree[c]--;
                if(indegree[c]==0)
                    queue.add(c);
            }
            numCourses--;
        }
        
        return numCourses == 0;
    }
    
}

```

# Similar Question
## Leetcode(207)
### Prompt:
There are a total of `numCourses` courses you have to take, labeled from `0` to `numCourses - 1`. You are given an array `prerequisites` where `prerequisites[i] = [ai, bi]` indicates that you must take course `bi` first if you want to take course `ai`.

For example, the pair `[0, 1]`, indicates that to take course `0` you have to first take course `1`.
Return `true` if you can finish all courses. Otherwise, return `false`.

```java
class Solution {
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        List<Integer>[] graph = new ArrayList[numCourses];
        
        for(int i=0; i < numCourses ; i++){
            graph[i] = new ArrayList();
        }
        
        int[] indegree = new int[numCourses];
        for(int[] e: prerequisites){
            graph[e[0]].add(e[1]);
            indegree[e[1]]++;
        }
        
        Queue<Integer> queue = new LinkedList();
        
        for(int i=0; i < numCourses ; i++){
            if(indegree[i]==0)
                queue.add(i);
        }
        
        while(!queue.isEmpty()){
            int current = queue.poll();
            for(int c : graph[current]){
                indegree[c]--;
                if(indegree[c]==0)
                    queue.add(c);
            }
            numCourses--;
        }
        
        return numCourses == 0;
    }
}

```
