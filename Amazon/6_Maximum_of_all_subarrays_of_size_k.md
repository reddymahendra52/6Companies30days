# 6. Maximum of all subarrays of size k
## GFG(Geeks For Geeks)
### Prompt:
Given an array arr[] of size N and an integer K. Find the maximum for each and every contiguous subarray of size K.

```java

class Solution
{
    //Function to find maximum of each subarray of size k.
    static ArrayList <Integer> max_of_subarrays(int arr[], int n, int k)
    {
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
