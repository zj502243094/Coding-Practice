# Course Schedule

[https://leetcode.com/problems/course-schedule/](https://leetcode.com/problems/course-schedule/)

```
class Solution {
    public boolean canFinish(int nums, int[][] edges) {
        Map<Integer, List<Integer>> graph = new HashMap<>();
        int[] indegree = new int[nums];
        for (int[] edge : edges) {
            int start = edge[1], end = edge[0];
            graph.computeIfAbsent(start, x -> new ArrayList<>()).add(end);
            indegree[end]++;
        }
        Queue<Integer> q = new LinkedList<>();
        for (int i = 0; i < nums; i++) {
            if (indegree[i] == 0) q.add(i);
        }
        int count = 0;
        while (!q.isEmpty()) {
            int cur = q.poll();
            count++;
            for (int nei : graph.getOrDefault(cur, new ArrayList<>())) {
                if (--indegree[nei] == 0) q.offer(nei);
            }
        }
        return count == nums;
    }
}
```
