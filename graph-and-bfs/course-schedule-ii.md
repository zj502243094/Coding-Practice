# Course Schedule II

[https://leetcode.com/problems/course-schedule-ii/](https://leetcode.com/problems/course-schedule-ii/)

```
class Solution {
    public int[] findOrder(int numCourses, int[][] edges) {
        int[] res = new int[numCourses];
        int[] indegree = new int[numCourses];
        
        Map<Integer, List<Integer>> graph = new HashMap<>();
        for (int[] edge : edges) {
            int start = edge[1], end = edge[0];
            graph.computeIfAbsent(start, x -> new ArrayList<>()).add(end);
            indegree[end]++;
        }
        Queue<Integer> q = new LinkedList<>();
        for (int i = 0; i < numCourses; i++) {
            if (indegree[i] == 0) q.offer(i);
        }
        int count = 0;
        while (!q.isEmpty()) {
            int cur = q.poll();
            res[count++] = cur;
            for (int nei : graph.getOrDefault(cur, new ArrayList<>())) {
                if (--indegree[nei] == 0) q.offer(nei);
            }
        }
        return count == numCourses ? res : new int[0];
    }
}
```
