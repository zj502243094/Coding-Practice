# Course Schedule

[https://leetcode.com/problems/course-schedule/](https://leetcode.com/problems/course-schedule/)

> There are a total of `numCourses` courses you have to take, labeled from `0` to `numCourses - 1`. You are given an array `prerequisites` where `prerequisites[i] = [ai, bi]` indicates that you **must** take course `bi` first if you want to take course `ai`.
>
> * For example, the pair `[0, 1]`, indicates that to take course `0` you have to first take course `1`.
>
> Return `true` if you can finish all courses. Otherwise, return `false`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: numCourses = 2, prerequisites = [[1,0]]
> <strong>Output:
> </strong> true</code></pre>

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
