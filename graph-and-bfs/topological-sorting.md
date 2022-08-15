# Topological Sorting

> [https://www.lintcode.com/problem/127/](https://www.lintcode.com/problem/127/)

```
public List<Node> topSort(List<Node> graph) {
        List<Node> res = new ArrayList();
        Map<Node, Integer> map = new HashMap<>();
        for (Node node : graph) {
            for (Node nei : node.neighbors) {
                map.put(nei, map.getOrDefault(nei, 1) + 1);
            }
        }
        Queue<Node> q = new LinkedList<>();
        for (Node node : graph) {
            if (!map.containsKey(node)) {
                q.offer(node);
            }
        }
        while (!q.isEmpty()) {
            Node cur = q.poll();
            res.add(cur);
            for (Node nei : cur.neighbors) {
                map.put(nei, map.get(nei) - 1);
                if (map.get(nei) == 0) {
                    q.offer(nei);
                }
            }
        }
        return res;
    }
```
