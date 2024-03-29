# Two Sum IV - Input is a BST

[https://leetcode.com/problems/two-sum-iv-input-is-a-bst/](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/)

> Given the `root` of a Binary Search Tree and a target number `k`, return _`true` if there exist two elements in the BST such that their sum is equal to the given target_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/09/21/sum\_tree\_1.jpg)
>
> <pre><code>Input: root = [5,3,6,2,4,null,7], k = 9
> <strong>Output:
> </strong> true</code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2020/09/21/sum\_tree\_2.jpg)
>
> <pre><code>Input: root = [5,3,6,2,4,null,7], k = 28
> <strong>Output:
> </strong> false</code></pre>

{% hint style="info" %}
直接inorder 然后 相向双指针&#x20;

time O(n) space O(n)
{% endhint %}

```
class Solution {
    public boolean findTarget(TreeNode root, int k) {
        List<Integer> nums = new ArrayList<>();
        inorder(root, nums);
        int l = 0, r = nums.size() - 1;
        while (l < r) {
            if (nums.get(l) + nums.get(r) < k) l++;
            else if(nums.get(l) + nums.get(r) > k) r--;
            else return true;
        }
        return false;
    }
    private void inorder(TreeNode root, List<Integer> nums) {
        if (root == null) return;
        inorder(root.left, nums);
        nums.add(root.val);
        inorder(root.right, nums);
    }
}
```

```
class Solution {
    public boolean findTarget(TreeNode root, int k) {
        Set<Integer> set = new HashSet<>();
        return dfs(root, set, k);
    }
    private boolean dfs(TreeNode root, Set<Integer> set, int k) {
        if (root == null) return false;
        if (set.contains(k - root.val)) return true;
        set.add(root.val);
        return dfs(root.left, set, k) || dfs(root.right, set, k);
    }
}
```

{% hint style="info" %}
follow up

Time O(n) Space O(h)
{% endhint %}

```
class Solution {
    public boolean findTarget(TreeNode root, int k) {
        BSTIterator left = new BSTIterator(root, true);
        BSTIterator right = new BSTIterator(root, false);
        while (left.hasNext() && right.hasNext()) {
            int l = left.peek(), r = right.peek();
            if (l >= r) return false;
            if (l + r == k) return true;
            else if (l + r < k) left.next();
            else right.next();
        }
        return false;
    }
    
    class BSTIterator {
    
        Stack<TreeNode> stack;
        boolean forward;
        public BSTIterator(TreeNode root, boolean forward) {
            this.stack = new Stack<>();
            this.forward = forward;
            if (forward) pushAllLeft(root);
            else pushAllRight(root);
        }
    
        public int next() {
            TreeNode node = stack.pop();
            if (forward) pushAllLeft(node.right);
            else pushAllRight(node.left);
            return node.val;
        }
    
        public boolean hasNext() {
            return !stack.isEmpty();
        }
        
        public int peek() {
            return stack.peek().val;
        }
        
        private void pushAllLeft(TreeNode root) {
            while (root != null) {
                stack.push(root);
                root = root.left;
            }
        }
        private void pushAllRight(TreeNode root) {
            while (root != null) {
                stack.push(root);
                root = root.right;
            }
        }
    }
}
```
