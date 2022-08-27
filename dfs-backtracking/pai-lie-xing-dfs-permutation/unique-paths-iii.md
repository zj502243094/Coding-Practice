# Unique Paths III

[https://leetcode.com/problems/unique-paths-iii/](https://leetcode.com/problems/unique-paths-iii/)

> You are given an `m x n` integer array `grid` where `grid[i][j]` could be:
>
> * `1` representing the starting square. There is exactly one starting square.
> * `2` representing the ending square. There is exactly one ending square.
> * `0` representing empty squares we can walk over.
> * `-1` representing obstacles that we cannot walk over.
>
> Return _the number of 4-directional walks from the starting square to the ending square, that walk over every non-obstacle square exactly once_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/08/02/lc-unique1.jpg)
>
> <pre><code>Input: grid = [[1,0,0,0],[0,0,0,0],[0,0,2,-1]]
> <strong>Output: 2
> </strong><strong>Explanation:
> </strong> We have the following two paths: 
> 1. (0,0),(0,1),(0,2),(0,3),(1,3),(1,2),(1,1),(1,0),(2,0),(2,1),(2,2)
> 2. (0,0),(1,0),(2,0),(2,1),(1,1),(0,1),(0,2),(0,3),(1,3),(1,2),(2,2)</code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/08/02/lc-unique2.jpg)
>
> <pre><code>Input: grid = [[1,0,0,0],[0,0,0,0],[0,0,0,2]]
> <strong>Output: 4
> </strong><strong>Explanation:
> </strong> We have the following four paths: 
> 1. (0,0),(0,1),(0,2),(0,3),(1,3),(1,2),(1,1),(1,0),(2,0),(2,1),(2,2),(2,3)
> 2. (0,0),(0,1),(1,1),(1,0),(2,0),(2,1),(2,2),(1,2),(0,2),(0,3),(1,3),(2,3)
> 3. (0,0),(1,0),(2,0),(2,1),(2,2),(1,2),(1,1),(0,1),(0,2),(0,3),(1,3),(2,3)
> 4. (0,0),(1,0),(2,0),(2,1),(1,1),(0,1),(0,2),(0,3),(1,3),(1,2),(2,2),(2,3)</code></pre>

```
class Solution {
    int res;
    public int uniquePathsIII(int[][] grid) {
        int m = grid.length, n = grid[0].length;
        int empty = 1, sx = 0, sy = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 0) empty++;
                if (grid[i][j] == 1) {
                    sx = i;
                    sy = j;
                }
            }
        }
        dfs(grid, sx, sy, empty);
        return res;
    }
    private void dfs(int[][] grid, int x, int y, int empty) {
        if (x < 0 || x >= grid.length || y < 0 || y >= grid[0].length || grid[x][y] < 0) {
            return;
        }
        if (grid[x][y] == 2) {
            if (empty == 0) res++;
            return;
        }
        grid[x][y] = -1;
        empty--;
        dfs(grid, x + 1, y, empty);
        dfs(grid, x - 1, y, empty);
        dfs(grid, x, y + 1, empty);
        dfs(grid, x, y - 1, empty);
        grid[x][y] = 0;
        empty++;
    }
}
```
