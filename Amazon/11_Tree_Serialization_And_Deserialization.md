# Tree Serialization And Deserialization
## GFG(Geeks For Geeks)
### Prompt:
Serialization is to store a tree in an array so that it can be later restored and Deserialization is reading tree back from the array. 
Now your task is to complete the function **serialize** which stores the tree into an array **A[ ]** and **deSerialize** which deserializes the array to the tree and returns it.
**Note:** The structure of the tree must be maintained. Multiple nodes can have the same data.

```java
class Tree 
{
    //Function to serialize a tree and return a list containing nodes of tree.
	public void serialize(Node root, ArrayList<Integer> A) 
	{
	    //code here
	    if(root == null){
	        A.add(-1);
	        return ;
	    }
	    
	    A.add(root.data);
	    serialize(root.left,A);
	    serialize(root.right,A);
	}
	
	//Function to deserialize a list and construct the tree.
    public Node deSerialize(ArrayList<Integer> A)
    {
        //code here
        if(A.get(0) == -1){
            A.remove(0);
            return null;
        }
        
        Node newNode = new Node(A.get(0));
        A.remove(0);
        newNode.left = deSerialize(A);
        newNode.right = deSerialize(A);
        return newNode;
        
    }
};

```

# Similar Question
## Leetcode(297)
### Prompt:
Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

```java
public class Codec {

        // Encodes a tree to a single string.
        public String serialize(TreeNode root) {
            if (root == null) return "";

            StringBuilder sb = new StringBuilder("");

            Queue<TreeNode> q = new LinkedList();
            q.add(root);

            while (q.size() > 0) {
                TreeNode node = q.poll();
                if (node == null) {
                    sb.append("n ");
                    continue;
                }
                sb.append(node.val + " ");
                q.add(node.left);
                q.add(node.right);
            }

            return sb.toString();
        }

        // Decodes your encoded data to tree.
        public TreeNode deserialize(String data) {
            if (data == "") return null;
            String[] s = data.split(" ");

            TreeNode root = new TreeNode(Integer.parseInt(s[0]));

            Queue<TreeNode> q = new LinkedList();
            q.add(root);

            for (int i = 1; i < s.length; i++) {
                TreeNode parent = q.poll();
                if (!s[i].equals("n")) {
                    parent.left = new TreeNode(Integer.parseInt(s[i]));
                    q.add(parent.left);
                }
                i++;
                if (i < s.length && !s[i].equals("n")) {
                    parent.right = new TreeNode(Integer.parseInt(s[i]));
                    q.add(parent.right);
                }
            }

            return root;
        }
    }

```

