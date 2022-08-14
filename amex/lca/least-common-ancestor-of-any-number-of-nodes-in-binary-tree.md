# Least Common Ancestor of any number of nodes in Binary Tree

[https://www.geeksforgeeks.org/least-common-ancestor-of-any-number-of-nodes-in-binary-tree/](https://www.geeksforgeeks.org/least-common-ancestor-of-any-number-of-nodes-in-binary-tree/)

> the LCA of any number of nodes in T is the shared common ancestor of the nodes that is located farthest from the root. \
> &#x20;
>
> <img src="https://media.geeksforgeeks.org/wp-content/uploads/20200206115435/lca2-1.jpg" alt="" data-size="original">
>
> **Example:** In the figure above:&#x20;
>
> ```
> LCA of nodes 12, 14, 15 is node 3
> LCA of nodes 3, 14, 15 is node 3
> LCA of nodes 6, 7, 15 is node 3
> LCA of nodes 5, 13, 14, 15 is node 1
> LCA of nodes 6, 12 is node 6
> ```

{% hint style="info" %}
```
Create a new list for capturing all the ancestors of the given nodes
Initially, there are No Matching Nodes. 
First Node in the Ancestors list is the LCA of given nodes


```
{% endhint %}

<pre><code><strong>class TreeNode {
</strong>	int val;
	TreeNode left;
	TreeNode right;

	TreeNode(int value)
	{
		this.val = value;
		left = right = null;
	}
}

public class LCAofAnyNumberOfNodes {
	public TreeNode lcaOfNodes(TreeNode root, List&#x3C;Integer> nodes) {
		
		List&#x3C;TreeNode> lca = new ArrayList&#x3C;TreeNode>();
		
		int matchingNodes = 0;
		getKeysCount(root, nodes, matchingNodes, lca);

		return ancestors.get(0);
	}

	private static int getKeysCount(TreeNode root, List&#x3C;Integer> nodes, 
		int matchingNodes, List&#x3C;TreeNode> lca) {
		if (root == null) return 0;

		// Search for left and right subtree for matching child Key Node.
		matchingNodes += getKeysCount(root.left, nodes, matchingNodes, lca)
			+ getKeysCount(root.right, nodes, matchingNodes, lca);
		
		//check if Root Node is also in Key Node
		if (nodes.contains(root.val)){
			matchingNodes++;
		}

		// when matching Nodes is equal to the Key Nodes found
		if (matchingNodes == nodes.size())
			lca.add(root);
		return matchingNodes;
	}
}
</code></pre>
