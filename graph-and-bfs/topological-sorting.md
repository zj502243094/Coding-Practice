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

{% hint style="info" %}
[https://www.youtube.com/watch?v=B5hxqxBL2d0\&list=PLbaIOC0vpjNVRXM5J4Y1jrZwhoDTyMNXU\&index=4\&ab\_channel=%E5%8F%A4%E5%9F%8E%E7%AE%97%E6%B3%95](https://www.youtube.com/watch?v=B5hxqxBL2d0\&list=PLbaIOC0vpjNVRXM5J4Y1jrZwhoDTyMNXU\&index=4\&ab\_channel=%E5%8F%A4%E5%9F%8E%E7%AE%97%E6%B3%95)
{% endhint %}
