# DAY21

## 117. 填充每个节点的下一个右侧

```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node next;

    public Node() {}
    
    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, Node _left, Node _right, Node _next) {
        val = _val;
        left = _left;
        right = _right;
        next = _next;
    }
};
*/

class Solution {
    public Node connect(Node root) {
        if(root==null){
            return root;
        }
        if(root.left!=null&&root.right!=null){
            root.left.next=root.right;
        }
        if(root.left!=null&&root.right==null){
            root.left.next=getNext(root.next);
        }
        if(root.right!=null){
            root.right.next=getNext(root.next);
        }
        //要先connect右节点再左节点
        connect(root.right);
        connect(root.left);  
        return root;
    }
    public Node getNext(Node root){
        if(root==null){
            return null;
        }
        if(root.left!=null){
            return root.left;
        }
        if(root.right!=null){
            return root.right;
        }
        if(root.next!=null){
            return getNext(root.next);
        }
        return null;
    }
}
```



## 572. 另一棵树的子树

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if(root==null &&subRoot==null){
            return true;
        }
        if(root==null &&subRoot!=null){
            return false;
        }
        return isSametree(root,subRoot)||isSubtree(root.left,subRoot)||isSubtree(root.right,subRoot);
    }
    public boolean isSametree(TreeNode root,TreeNode subRoot){
        if(root==null &&subRoot==null){
            return true;
        }
        return root!=null&&subRoot!=null&&root.val==subRoot.val&&isSametree(root.left,subRoot.left)&&isSametree(root.right,subRoot.right);
    }
}
```

