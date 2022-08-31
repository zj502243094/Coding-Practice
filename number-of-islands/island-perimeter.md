# Island Perimeter

[https://leetcode.com/problems/island-perimeter/](https://leetcode.com/problems/island-perimeter/)

> You are given `row x col` `grid` representing a map where `grid[i][j] = 1` represents land and `grid[i][j] = 0` represents water.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2018/10/12/island.png)
>
> <pre><code>Input: grid = [[0,1,0,0],[1,1,1,0],[0,1,0,0],[1,1,0,0]]
> <strong>Output: 16
> </strong><strong>Explanation:
> </strong> The perimeter is the 16 yellow stripes in the image above.</code></pre>

```
class Solution {
    public int islandPerimeter(int[][] grid) {
        int res = 0;
        for (int i = 0; i < grid.length; i++) {
            for (int j = 0; j < grid[0].length; j++) {
                if (grid[i][j] == 1) {
                    res = dfs(grid, i, j);
                }
            } 
        }
        return res;
    }
    private int dfs(int[][] grid, int x, int y) {
        if (x < 0 || x >= grid.length || y < 0 || y >= grid[0].length || grid[x][y] == 0) return 1;
        if (grid[x][y] == -1) return 0;
        grid[x][y] = -1;
        int res = 0;
        res += dfs(grid, x + 1, y);
        res += dfs(grid, x - 1, y);
        res += dfs(grid, x, y + 1);
        res += dfs(grid, x, y - 1);
        return res;
    }
}
```

```
class Solution {
    public int islandPerimeter(int[][] grid) {
        int res = 0, neighbor = 0;
        for (int i = 0; i < grid.length; i++) {
            for (int j = 0; j < grid[0].length; j++) {
                if (grid[i][j] == 1) {
                    res += 4;
                    if (i < grid.length - 1 && grid[i + 1][j] == 1) res -= 2;
                    if (j < grid[i].length - 1 && grid[i][j + 1] == 1) res -= 2;
                }
            } 
        }
        return res;
    }
}
```
