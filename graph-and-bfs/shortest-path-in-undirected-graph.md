# Shortest Path in Undirected Graph

[https://www.lintcode.com/problem/814/](https://www.lintcode.com/problem/814/)

```
public class Solution {
    /**
     * @param graph: a list of Undirected graph node
     * @param A: nodeA
     * @param B: nodeB
     * @return:  the length of the shortest path
     */
    public int shortestPath(List<Node> graph, Node A, Node B) {
        int res = 0;
        Set<Node> set = new HashSet<>();
        Queue<Node> q = new LinkedList<>();
        set.add(A);
        q.offer(A);
        while (!q.isEmpty()) {
            int size = q.size();
            for (int i = 0; i < size; i++) {
                Node cur = q.poll();
                if (cur == B) return res;
                for (Node nei : cur.neighbors) {
                    if (!set.contains(nei)) {
                        q.offer(nei);
                        set.add(nei);
                    }
                }
            }
            res++;
        }
        return -1;
    }
}
```
