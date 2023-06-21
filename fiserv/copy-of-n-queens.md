# Copy of N-Queens

[https://leetcode.com/problems/n-queens/](https://leetcode.com/problems/n-queens/)

> The **n-queens** puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.
>
> Given an integer `n`, return _all distinct solutions to the **n-queens puzzle**_. You may return the answer in **any order**.
>
> Each solution contains a distinct board configuration of the n-queens' placement, where `'Q'` and `'.'` both indicate a queen and an empty space, respectively.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/11/13/queens.jpg)
>
> <pre><code>Input: n = 4
> <strong>Output: [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
> </strong><strong>Explanation:
> </strong> There exist two distinct solutions to the 4-queens puzzle as shown above
> </code></pre>
>
> **Example 2:**
>
> <pre><code>Input: n = 1
> <strong>Output: [["Q"]]
> </strong></code></pre>

```
class Solution {
    public List<List<String>> solveNQueens(int n) {
        char[][] board = new char[n][n];
        for (int i = 0; i < n; i++) {
            for(int j = 0; j < n; j++) {
                board[i][j] = '.';
            }
        }
        List<List<String>> res = new ArrayList<>();
        dfs(board, 0, res);
        return res;
    }
    private void dfs(char[][] board, int colIndex, List<List<String>> res) {
        if (colIndex == board.length) {
            res.add(construct(board));
            return;
        }
        for (int i = 0; i < board.length; i++) {
            if (isValid(board, i, colIndex)) {
                board[i][colIndex] = 'Q';
                dfs(board, colIndex + 1, res);
                board[i][colIndex] = '.';
            }
        }
    }
    private boolean isValid(char[][] board, int x, int y) {
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < y; j++) {
                if (board[i][j] == 'Q' && (x + y == i + j || x - y == i - j || x == i)) {
                    return false;
                }
            }
        }
        return true;
    }
    private List<String> construct(char[][] board) {
        List<String> res = new ArrayList<>();
        for (int i = 0; i < board.length; i++) {
            res.add(new String(board[i]));
        }
        return res;
    }
}
```
