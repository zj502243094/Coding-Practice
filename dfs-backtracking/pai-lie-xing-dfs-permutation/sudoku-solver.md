# Sudoku Solver

[https://leetcode.com/problems/sudoku-solver/](https://leetcode.com/problems/sudoku-solver/)

> Write a program to solve a Sudoku puzzle by filling the empty cells.
>
> A sudoku solution must satisfy **all of the following rules**:
>
> 1. Each of the digits `1-9` must occur exactly once in each row.
> 2. Each of the digits `1-9` must occur exactly once in each column.
> 3. Each of the digits `1-9` must occur exactly once in each of the 9 `3x3` sub-boxes of the grid.
>
> The `'.'` character indicates empty cells.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png)

```
class Solution {
    public void solveSudoku(char[][] board) {
        if(board == null || board.length == 0)
            return;
        solve(board);
    }
    private boolean solve(char[][] board) {
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[0].length; j++) {
                if (board[i][j] == '.') {
                    for (char c = '1'; c <= '9'; c++) {
                        if (isValid(board, i, j, c)) {
                            board[i][j] = c;
                            if(solve(board))
                                return true; 
                            else
                                board[i][j] = '.'; 
                        }
                    }
                    return false;
                }
            }
        }
        return true;
    }
    private boolean isValid(char[][] board, int i, int j, char c) {
        for (int row = 0; row < 9; row++) {
            if (board[row][j] == c) return false;
        }
        for (int col = 0; col < 9; col++) {
            if (board[i][col] == c) return false;
        } 
        for (int row = (i / 3) * 3; row < (i / 3) * 3 + 3; row++) {
            for (int col = (j / 3) * 3; col < (j / 3) * 3 + 3; col++) {
                if (board[row][col] == c) return false;
            }
        }
        return true;
    }
}
```
