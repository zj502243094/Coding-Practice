# Max Area of Island

[https://leetcode.com/problems/max-area-of-island/](https://leetcode.com/problems/max-area-of-island/)

> You are given an `m x n` binary matrix `grid`. An island is a group of `1`'s (representing land) connected **4-directionally** (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.
>
> The **area** of an island is the number of cells with a value `1` in the island.
>
> Return _the maximum **area** of an island in_ `grid`. If there is no island, return `0`.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/05/01/maxarea1-grid.jpg)

```
class Solution {
    int[][] dirs = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
    public int maxAreaOfIsland(int[][] grid) {
        int m = grid.length, n = grid[0].length;
        int res = 0;
        int[] area = new int[1];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 1) {
                    area[0] = 0;
                    bfs(grid, i, j, area);
                    res = Math.max(res, area[0]);
                }
            }
        } 
        return res;
    }
    private void bfs(int[][] grid, int row, int col, int[] area) {
        Queue<int[]> q = new LinkedList<>();
        q.offer(new int[]{row, col});
        while (!q.isEmpty()) {
            int[] cur = q.poll();
            int x = cur[0], y = cur[1];
            if (x >= 0 && x < grid.length && y >= 0 && y < grid[0].length && grid[x][y] == 1) {
                grid[x][y] = 0;
                area[0]++;
                for (int[] dir : dirs) q.offer(new int[]{x + dir[0], y + dir[1]});
            }
        }
    }
}
```

```
class Solution {
    int[][] dirs = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
    public int maxAreaOfIsland(int[][] grid) {
        int m = grid.length, n = grid[0].length;
        int res = 0;
        boolean[][] visit = new boolean[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 1 && !visit[i][j]) {
                    int area = bfs(grid, i, j, visit);
                    res = Math.max(res, area);
                }
            }
        } 
        return res;
    }
    private int bfs(int[][] grid, int row, int col, boolean[][] visit) {
        Queue<int[]> q = new LinkedList<>();
        q.offer(new int[]{row, col});
        visit[row][col] = true;
        int res = 0;
        while (!q.isEmpty()) {
            int[] cur = q.poll();
            res++;
            for (int[] dir : dirs) {
                int x = cur[0] + dir[0], y = cur[1] + dir[1];
                if (x < 0 || x >= grid.length || y < 0 || y >= grid[0].length || grid[x][y] == 0 || visit[x][y]) continue;
                q.offer(new int[]{x, y});
                visit[x][y] = true;
            }
        }
        return res;
    }
}
```
