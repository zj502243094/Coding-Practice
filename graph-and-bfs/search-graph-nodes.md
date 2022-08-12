# Search Graph Nodes

> Given a `undirected graph`, a `node` and a `target`, return the nearest node to given node which value of it is target, return `NULL` if you can't find.
>
> There is a `mapping` store the nodes' values in the given parameters.
>
>
>
> **样例**
>
> Example 1:
>
> ```
> Input:
> {1,2,3,4#2,1,3#3,1,2#4,1,5#5,4}
> [3,4,5,50,50]
> 1
> 50
> Output:
> 4
> Explanation:
> 2------3  5
>  \     |  | 
>   \    |  |
>    \   |  |
>     \  |  |
>       1 --4
> Give a node 1, target is 50
>
> there a hash named values which is [3,4,10,50,50], represent:
> Value of node 1 is 3
> Value of node 2 is 4
> Value of node 3 is 10
> Value of node 4 is 50
> Value of node 5 is 50
>
> Return node 4
> ```

<pre><code>/**
 * Definition for graph node.
 * class GraphNode {
 *     int label;
 *     ArrayList&#x3C;UndirectedGraphNode> neighbors;
 *     UndirectedGraphNode(int x) { 
 *         label = x; neighbors = new ArrayList&#x3C;UndirectedGraphNode>(); 
 *     }
 * };
 */
<strong>class Solution {
</strong>    public GraphNode searchNode(ArrayList&#x3C;GraphNode> graph,
                                Map&#x3C;GraphNode, Integer> values,
                                GraphNode node, int target) {
                                
        Queue&#x3C;GraphNode> q = new LinkedList&#x3C;>();
        Set&#x3C;GraphNode> set = new HashSet&#x3C;>();
        q.offer(node);
        set.add(node);
        
        while (!q.isEmpty()) {
            GraphNode cur = q.poll();
            if (values.get(cur) == target) {
                return cur;
            }
            for (GraphNode neighbor : cur.neighbors) {
                if (!set.contains(neighbor)) {
                    q.offer(neighbor);
                    set.add(neighbor);
                }
            }
        }
        return null;
    }
}</code></pre>
