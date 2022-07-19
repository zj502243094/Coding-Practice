# Binary Tree Preorder / Inorder / Poster Traversal

先序遍历（Preorder traversal）根左右

<img src="../../.gitbook/assets/image (9) (1).png" alt="" data-size="original">

中序遍历（Inorder traversal）左根右

![](<../../.gitbook/assets/image (8) (1) (1).png>)

后序遍历（Postorder traversal） 左右根 1 4 7 6 3 13 14 10 8

```
private class Main{
    public static void main(String[] args) {
        TreeNode node1 = new TreeNode(8);
        TreeNode node2 = new TreeNode(3);
        TreeNode node3 = new TreeNode(10);
        
        node1.left = node2;
        node1.right = node3;
        
        Solution solution = new Solution();
        solution.xxx(node1)
    }
}

class Solution{
    public void xxx(TreeNode x){
    }
}
```



```
class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        preorder(root, res);
        return res;
    }
    private void preorder(TreeNode root, List<Integer> res){
        if(root == null) return;
        res.add(root.val);
        preorder(root.left, res);
        preorder(root.right, res);
    }
}


class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        inorder(root, res);
        return res;
    }
    private void inorder(TreeNode root, List<Integer> res){
        if(root == null) return;
        
        inorder(root.left, res);
        res.add(root.val);
        inorder(root.right, res);
    }
}


class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        postorder(root, res);
        return res;
    }
    private void postorder(TreeNode root, List<Integer> res){
        if(root == null) return;
        
        postorder(root.left, res);
        postorder(root.right, res);
        res.add(root.val);
    }
}
```
