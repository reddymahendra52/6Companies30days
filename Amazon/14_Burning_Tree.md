# 14. Burning Tree
## GFG(Geeks For Geeks)
### Prompt:
Given a binary tree and a node called target. Find the minimum time required to burn the complete binary tree if the target is set on fire. 
It is known that in 1 second all nodes connected to a given node get burned. That is its left child, right child, and parent.

```java

class Solution
{
    /*class Node {
    	int data;
    	Node left;
    	Node right;
    
    	Node(int data) {
    		this.data = data;
    		left = null;
    		right = null;
    	}
    }*/
    
    static boolean targetFound;
    static int burningTime;
    
    public static int minTime(Node root, int target) 
    {
        targetFound = false;
        burningTime = 0;
        
        burnTree(root, target);
        return burningTime;
    }
    
    static int burnTree(Node root, int target) {
        if(root == null) {
            return 0;
        }   
        
        boolean fireFromParent = false;
        boolean targetFromLeft = false;
        boolean targetFromRight = false;
        
        if(root.data == target) {
            targetFound = true;
        }else if(targetFound == true) {
            fireFromParent = true;
        }
        
        int left = burnTree(root.left, target);
        if(targetFound) {
            targetFromLeft = true;
        }
        
        int right = burnTree(root.right, target);
        if(targetFound) {
            targetFromRight = true;
        }
        
        if(root.data == target) {
            burningTime = Math.max(burningTime, Math.max(left, right));
            return Math.min(left, right) + 1;
        } else if(!fireFromParent && targetFound) {
            burningTime = Math.max(burningTime, left+right);
            return (targetFromLeft)? left+1 : right+1;
        }
        
        return Math.max(left, right) + 1;
}
}

```

