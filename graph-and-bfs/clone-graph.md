# Clone Graph

[https://leetcode.com/problems/clone-graph/](https://leetcode.com/problems/clone-graph/)

> Given a reference of a node in a [**connected**](https://en.wikipedia.org/wiki/Connectivity\_\(graph\_theory\)#Connected\_graph) undirected graph.
>
> Return a [**deep copy**](https://en.wikipedia.org/wiki/Object\_copying#Deep\_copy) (clone) of the graph.
>
> Each node in the graph contains a value (`int`) and a list (`List[Node]`) of its neighbors.
>
> ```
> class Node {
>     public int val;
>     public List<Node> neighbors;
> }
> ```

```
class Solution {
    public Node cloneGraph(Node node) {
        if (node == null) return null;
        HashMap<Node, Node> map = new HashMap();
        Queue<Node> q = new LinkedList();
        
        Node copy = new Node(node.val);
        map.put(node, copy);
        q.add(node);
        while (!q.isEmpty()) {
            Node cur = q.poll();
            for (Node neighbor : cur.neighbors) {
                if (!map.containsKey(neighbor)) {
                    q.add(neighbor);
                    Node copyNeighbor = new Node(neighbor.val);
                    map.put(neighbor, copyNeighbor);
                }
                map.get(cur).neighbors.add(map.get(neighbor));
            }
        }
        return copy;
    }
}
```

{% hint style="info" %}
[https://www.cnblogs.com/springfor/p/3874591.html](https://www.cnblogs.com/springfor/p/3874591.html)
{% endhint %}
