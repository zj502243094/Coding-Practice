# N-Queens II

[https://leetcode.com/problems/n-queens-ii/](https://leetcode.com/problems/n-queens-ii/)

```
class Solution {
    int res;
    public int totalNQueens(int n) {
        char[][] board = new char[n][n];
        for (int i = 0; i < n; i++) {
            for(int j = 0; j < n; j++) {
                board[i][j] = '.';
            }
        }
        dfs(board, 0);
        return res;
    }
    private void dfs(char[][] board, int colIndex) {
        if (colIndex == board.length) {
            res++;
            return;
        }
        for (int i = 0; i < board.length; i++) {
            if (isValid(board, i, colIndex)) {
                board[i][colIndex] = 'Q';
                dfs(board, colIndex + 1);
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
}
```
