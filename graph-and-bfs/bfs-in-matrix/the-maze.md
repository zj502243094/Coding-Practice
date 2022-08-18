# The Maze

[https://leetcode.com/problems/the-maze/](https://leetcode.com/problems/the-maze/)

> There is a ball in a `maze` with empty spaces (represented as `0`) and walls (represented as `1`). The ball can go through the empty spaces by rolling **up, down, left or right**, but it won't stop rolling until hitting a wall. When the ball stops, it could choose the next direction.
>
> Given the `m x n` `maze`, the ball's `start` position and the `destination`, where `start = [startrow, startcol]` and `destination = [destinationrow, destinationcol]`, return `true` if the ball can stop at the destination, otherwise return `false`.
>
> You may assume that **the borders of the maze are all walls** (see examples).
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/31/maze1-1-grid.jpg)
>
> <pre><code>Input: maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [4,4]
> <strong>Output: true
> </strong><strong>Explanation:One possible way is : left -> down -> left -> down -> right -> down -> right.</strong></code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/31/maze1-2-grid.jpg)
>
> <pre><code>Input: maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [3,2]
> <strong>Output:false</strong></code></pre>

{% hint style="info" %}
int\[]\[] dirs = \{{1, 0}, {-1, 0}, {0, 1}, {0, -1\}};&#x20;

方向对应 右左上下
{% endhint %}

```
class Solution {
    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        int[][] dirs = {{1, 0}, {0, 1}, {-1, 0}, {0, -1}};
        int m = maze.length, n = maze[0].length;
        boolean[][] visit = new boolean[m][n];
        Queue<int[]> q = new LinkedList<>();
        q.offer(start);
        visit[start[0]][start[1]] = true;
        while (!q.isEmpty()) {
            int[] cur = q.poll();
            if (cur[0] == destination[0] && cur[1] == destination[1]) return true;
            for (int[] dir : dirs) {
                int x = cur[0] + dir[0], y = cur[1] + dir[1];
                while (x >= 0 && y >= 0 && x < m && y < n && maze[x][y] == 0) {
                    x += dir[0];
                    y += dir[1];
                }
                x -= dir[0];
                y -= dir[1];
                if (!visit[x][y]) {
                    q.offer(new int[]{x, y});
                    visit[x][y] = true;
                }
            }
        }
        return false;
    }
}
```
