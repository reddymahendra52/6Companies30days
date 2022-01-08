# 3. IPL 2021 - Match Day 2 
## GFG(Geeks For Geeks)
### Prompt:
Due to the rise of covid-19 cases in India, this year BCCI decided to organize knock-out matches in IPL rather than a league.

Today is matchday 2 and it is between the most loved team Chennai Super Kings and the most underrated team - Punjab Kings. Stephen Fleming, 
the head coach of CSK, analyzing the batting stats of Punjab. He has stats of runs scored by all N players in the previous season and he wants 
to find the maximum score for each and every contiguous sub-list of size K to strategize for the game.

```java
class Solution {
    static ArrayList<Integer> max_of_subarrays(int arr[], int n, int k) {
        // Your code here
        ArrayList<Integer> list = new ArrayList<>();
       Deque<Integer> dq = new LinkedList<>();
       int i = 0;
       for (;i<k;i++){
           while(!dq.isEmpty() && arr[i]>=arr[dq.peekLast()]){
               dq.removeLast();
           }
           dq.addLast(i);
       }
       
       for(;i<n;i++){
           int x = arr[dq.peek()];
           list.add(x);
           while(!dq.isEmpty() && dq.peek()<=i-k){
               dq.removeFirst();
           }
           while(!dq.isEmpty() && arr[i]>=arr[dq.peekLast()]){
               dq.removeLast();
           }
           dq.addLast(i);
       }
       
       int x = arr[dq.peek()];
       list.add(x);
       return list;
    }
}

```

# Similar Question
## Sliding Window Maximum/Leetcode(239)
### Prompt:
You are given an array of integers `nums`, there is a sliding window of size `k` which is moving from the very left of the array to the very right. 
You can only see the `k` numbers in the window. Each time the sliding window moves right by one position.

Return the max sliding window.

```java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
         int n = nums.length;
            List<Integer> result = new ArrayList();
            LinkedList<Integer> indexes = new LinkedList();

            for (int i = 0; i < n; i++) {
                while (indexes.size() > 0 && indexes.getFirst() <= i - k)
                    indexes.removeFirst();
                while (indexes.size() > 0 && nums[i] >= nums[indexes.getLast()])
                    indexes.removeLast();
                indexes.addLast(i);
                if (i >= k - 1)
                    result.add(nums[indexes.getFirst()]);
            }

            return result.stream().mapToInt(x -> x).toArray();
    }
}

```
