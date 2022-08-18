# Number of Islands

[https://leetcode.com/problems/number-of-islands/](https://leetcode.com/problems/number-of-islands/)

> Given an `m x n` 2D binary grid `grid` which represents a map of `'1'`s (land) and `'0'`s (water), return _the number of islands_.
>
> An **island** is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: grid = [
>   ["1","1","1","1","0"],
>   ["1","1","0","1","0"],
>   ["1","1","0","0","0"],
>   ["0","0","0","0","0"]
> ]
> <strong>Output: 1</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: grid = [
>   ["1","1","0","0","0"],
>   ["1","1","0","0","0"],
>   ["0","0","1","0","0"],
>   ["0","0","0","1","1"]
> ]
> <strong>Output:3</strong></code></pre>

```
class Solution {
    int[][] dirs = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};
    public int numIslands(char[][] grid) {
        int m = grid.length, n = grid[0].length;
        int res = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == '1') {
                    res++;
                    bfs(grid, i, j);
                }
            }
        }
        return res;
    }
    private void bfs(char[][] grid, int row, int col) {
        Queue<int[]> q = new LinkedList<>();
        q.offer(new int[]{row, col});
        while (!q.isEmpty()) {
            int[] cur = q.poll();
            int x = cur[0], y = cur[1];
            if (x < 0 || x >= grid.length || y < 0 || y >= grid[0].length || grid[x][y] == '0') continue;
            grid[x][y] = '0';
            for (int[] dir : dirs) q.add(new int[]{x + dir[0], y + dir[1]});
        }
    }
}
```
