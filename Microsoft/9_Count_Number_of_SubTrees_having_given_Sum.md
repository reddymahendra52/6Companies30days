# 9. Count Number of SubTrees having given Sum 
## GFG(Geeks For Geeks)
### Prompt:
Given a binary tree and an integer **X**. Your task is to complete the function **countSubtreesWithSumX()** that returns the count of the number of 
subtress having total node’s data sum equal to the value **X**.

```java
class Tree
{
    
    int count;
    private int subTreeSum(Node root, int X){
        if(root==null) return 0;
        int sum = root.data + subTreeSum(root.left, X) + subTreeSum(root.right, X);
        if(sum==X) count++;
        return sum;
    }
    
    //Function to count number of subtrees having sum equal to given sum.
    int countSubtreesWithSumX(Node root, int X)
    {
	    //Add your code here.
	    count = 0;
	    subTreeSum(root, X);
	    return count;
    }
}



```
