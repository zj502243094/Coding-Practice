# Delete Node in a BST

[https://leetcode.com/problems/delete-node-in-a-bst/](https://leetcode.com/problems/delete-node-in-a-bst/)

> Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return _the **root node reference** (possibly updated) of the BST_.
>
> Basically, the deletion can be divided into two stages:
>
> 1. Search for a node to remove.
> 2. If the node is found, delete the node.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/09/04/del\_node\_1.jpg)![](<../../.gitbook/assets/image (11).png>)

{% hint style="info" %}
BST 满足 左根右 从大到小顺序

1. root.val != key 向左右找
2. root.val == key&#x20;
   1. 如果root 左右都是空 直接null 删除
   2. 如果左或右为空 直接返回root.left / right
   3. 左右都不为空 在左边找到最大的值 填到root 并且 root.left 要删一遍找到的值
{% endhint %}

```
class Solution {
    public TreeNode deleteNode(TreeNode root, int key) {
        if(root == null) return null;
        if(root.val < key){
            root.right = deleteNode(root.right, key);
        }else if(root.val > key){
            root.left = deleteNode(root.left, key);
        }else{
            if(root.left == null && root.right == null){
                return null;
            }else if(root.left == null){
                return root.right;
            }else if(root.right == null){
                return root.left;
            }else{
                int leftMax = findBSTMax(root.left);
                root.val = leftMax;
                root.left = deleteNode(root.left, leftMax);
            }
        }
        return root;
    }
    
    private int findBSTMax(TreeNode root){
        if(root.right == null) return root.val;
        return findBSTMax(root.right);
    }
}
```
