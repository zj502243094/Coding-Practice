# Graph Valid Tree

[https://leetcode.com/problems/graph-valid-tree/](https://leetcode.com/problems/graph-valid-tree/)

> You have a graph of `n` nodes labeled from `0` to `n - 1`. You are given an integer n and a list of `edges` where `edges[i] = [ai, bi]` indicates that there is an undirected edge between nodes `ai` and `bi` in the graph.
>
> Return `true` _if the edges of the given graph make up a valid tree, and_ `false` _otherwise_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/12/tree1-graph.jpg)
>
> <pre><code>Input: n = 5, edges = [[0,1],[0,2],[0,3],[1,4]]
> <strong>Output: true</strong></code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/12/tree2-graph.jpg)
>
> <pre><code>Input: n = 5, edges = [[0,1],[1,2],[2,3],[1,3],[1,4]]
> <strong>Output: false</strong></code></pre>

{% hint style="info" %}
构建出图， &#x20;

最后判断 map. size 是否等于 n 如果等于n 表示 从 起始点开始 可以找到所有点 联通上了
{% endhint %}

```
class Solution {
    public boolean validTree(int n, int[][] edges) {
        if (n - 1 != edges.length) return false;
        Map<Integer, Set<Integer>> graph = init(n, edges);
        Set<Integer> set = new HashSet();
        Queue<Integer> q = new LinkedList();
        q.offer(0);
        set.add(0);
        while (!q.isEmpty()) {
            int cur = q.poll();
            for (int nei : graph.get(cur)) {
                if (!set.contains(nei)) {
                    q.offer(nei);
                    set.add(nei);
                }
            }
        }
        return (set.size() == n);
    }
    private Map<Integer, Set<Integer>> init(int n, int[][] edges) {
        Map<Integer, Set<Integer>> graph = new HashMap();
        for (int i = 0; i < n; i++) {
            graph.put(i, new HashSet<Integer>());
        }
        for (int i = 0; i < edges.length; i++) {
            int a = edges[i][0];
            int b = edges[i][1];
            graph.get(a).add(b);
            graph.get(b).add(a);
        }
        return graph;
    }
}
```
