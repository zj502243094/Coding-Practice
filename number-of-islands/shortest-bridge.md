# Shortest Bridge

[https://leetcode.com/problems/shortest-bridge/](https://leetcode.com/problems/shortest-bridge/)

> You are given an `n x n` binary matrix `grid` where `1` represents land and `0` represents water.
>
> An **island** is a 4-directionally connected group of `1`'s not connected to any other `1`'s. There are **exactly two islands** in `grid`.
>
> You may change `0`'s to `1`'s to connect the two islands to form **one island**.
>
> Return _the smallest number of_ `0`_'s you must flip to connect the two islands_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: grid = [[0,1],[1,0]]
> <strong>Output: 1</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: grid = [[0,1,0],[0,0,0],[0,0,1]]
> <strong>Output: 2</strong></code></pre>
>
> **Example 3:**
>
> <pre><code>Input: grid = [[1,1,1,1,1],[1,0,0,0,1],[1,0,1,0,1],[1,0,0,0,1],[1,1,1,1,1]]
> <strong>Output: 1</strong></code></pre>

{% hint style="info" %}
1. DFS找到第一座岛屿然后全部标记为visited 放进Queue
2. 从起点q 做BFS 然后一层层扩展 直到下一个岛屿
{% endhint %}

```
class Solution {
    int[][] dirs = new int[][]{{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
    Queue<int[]> q = new LinkedList<>();
    public int shortestBridge(int[][] grid) {
        int m = grid.length, n = grid[0].length;
        boolean[][] visit = new boolean[m][n];
        boolean found = false;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 1 && !found) {
                    dfs(grid, i, j, visit);
                    found = true;
                    break;
                }
            }
        }
        int res = 0;
        while (!q.isEmpty()) {
            int size = q.size();
            for (int i = 0; i < size; i++) {
                int[] cur = q.poll();
                for (int[] dir : dirs) {
                    int x = cur[0] + dir[0], y = cur[1] + dir[1];
                    if (x >= 0 && y >= 0 && x < m && y < n && !visit[x][y]) {
                        if (grid[x][y] == 1) return res;
                        q.offer(new int[]{x, y});
                        visit[x][y] = true;
                    }
                }
            }
            res++;
        }
        return -1;
    }
    private void dfs(int[][] grid, int x, int y, boolean[][] visit) {
        if (x < 0 || x >= grid.length || y < 0 || y >= grid[0].length || grid[x][y] == 0 || visit[x][y]) return;
        visit[x][y] = true;
        q.offer(new int[]{x, y});
        for (int[] dir : dirs) {
            dfs(grid, x + dir[0], y + dir[1], visit);
        }
    }
}
```
