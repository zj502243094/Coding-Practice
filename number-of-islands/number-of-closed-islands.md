# Number of Closed Islands

[https://leetcode.com/problems/number-of-closed-islands/](https://leetcode.com/problems/number-of-closed-islands/)

> Given a 2D `grid` consists of `0s` (land) and `1s` (water).  An _island_ is a maximal 4-directionally connected group of `0s` and a _closed island_ is an island **totally** (all left, top, right, bottom) surrounded by `1s.`
>
> Return the number of _closed islands_.
>
> &#x20;
>
> **Example 1:**
>
> <img src="https://assets.leetcode.com/uploads/2019/10/31/sample_3_1610.png" alt="" data-size="original">
>
> <pre><code>Input: grid = [[1,1,1,1,1,1,1,0],[1,0,0,0,0,1,1,0],[1,0,1,0,1,1,1,0],[1,0,0,0,0,1,0,1],[1,1,1,1,1,1,1,0]]
> <strong>Output:
> </strong> 2
> <strong>Explanation:
> </strong> 
> Islands in gray are closed because they are completely surrounded by water (group of 1s).</code></pre>
>
> **Example 2:**
>
> <img src="https://assets.leetcode.com/uploads/2019/10/31/sample_4_1610.png" alt="" data-size="original">
>
> <pre><code>Input: grid = [[0,0,1,0,0],[0,1,0,1,0],[0,1,1,1,0]]
> <strong>Output:
> </strong> 1</code></pre>

```
class Solution {
    public int closedIsland(int[][] grid) {
        int res = 0;
        for (int i = 0; i < grid.length; i++) {
            for (int j = 0; j < grid[0].length; j++) {
                if (grid[i][j] == 0 && dfs(grid, i, j)) 
                    res++;
            }
        }
        return res;
    }
    private boolean dfs(int[][] grid, int x, int y) {
        if (x < 0 || x >= grid.length || y < 0 || y >= grid[0].length) return false;
        if (grid[x][y] == 1) return true;
        grid[x][y] = 1;
        boolean up = dfs(grid, x - 1, y);
        boolean down = dfs(grid, x + 1, y);
        boolean left = dfs(grid, x, y - 1);
        boolean right = dfs(grid, x, y + 1);
        return up && down && left && right;
    }
}
```
