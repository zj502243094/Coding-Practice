# Number of Distinct Islands

[https://leetcode.com/problems/number-of-distinct-islands/](https://leetcode.com/problems/number-of-distinct-islands/)

> You are given an `m x n` binary matrix `grid`. An island is a group of `1`'s (representing land) connected **4-directionally** (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.
>
> An island is considered to be the same as another if and only if one island can be translated (and not rotated or reflected) to equal the other.
>
> Return _the number of **distinct** islands_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/05/01/distinctisland1-1-grid.jpg)
>
> <pre><code>Input: grid = [[1,1,0,0,0],[1,1,0,0,0],[0,0,0,1,1],[0,0,0,1,1]]
> <strong>Output: 1</strong></code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/05/01/distinctisland1-2-grid.jpg)
>
> <pre><code>Input: grid = [[1,1,0,1,1],[1,0,0,0,0],[0,0,0,0,1],[1,1,0,1,1]]
> <strong>Output: 3</strong></code></pre>

```
class Solution {
    public int numDistinctIslands(int[][] grid) {
        Set<String> set = new HashSet<>();
        for (int i = 0; i < grid.length; i++) {
            for (int j = 0; j < grid[0].length; j++) {
                if (grid[i][j] == 1) {
                    StringBuilder sb = new StringBuilder();
                    dfs(grid, i, j, sb, "s");
                    set.add(sb.toString());
                }
            }
        }
        return set.size();
    }
    private void dfs(int[][] grid, int x, int y, StringBuilder sb, String dir) {
        if (x < 0 || x >= grid.length || y < 0 || y >= grid[0].length || grid[x][y] == 0) return;
        sb.append(dir);
        grid[x][y] = 0;
        dfs(grid, x - 1, y, sb, "u");
        dfs(grid, x + 1, y, sb, "d");
        dfs(grid, x, y - 1, sb, "l");
        dfs(grid, x, y + 1, sb, "r");
        sb.append("e");
    }
}
```
