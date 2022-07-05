# Spiral Matrix

[https://leetcode.com/problems/spiral-matrix/](https://leetcode.com/problems/spiral-matrix/)

> Given an `m x n` `matrix`, return _all elements of the_ `matrix` _in spiral order_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/11/13/spiral1.jpg)
>
> ```
> Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
> Output: [1,2,3,6,9,8,7,4,5]
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2020/11/13/spiral.jpg)
>
> ```
> Input: matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
> Output: [1,2,3,4,8,12,11,10,9,5,6,7]
> ```

```
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> res = new ArrayList<>();
        int rowB = 0;
        int rowE = matrix.length - 1;
        int colB = 0;
        int colE = matrix[0].length - 1;
        
        while(rowB <= rowE && colB <= colE) {
            for(int i = colB; i <= colE; i++) {
                res.add(matrix[rowB][i]);
            }
            rowB++;
            for(int i = rowB; i <= rowE; i++) {
                res.add(matrix[i][colE]);
            }
            colE--;
            
            if(rowB <= rowE) {
                for(int i = colE; i >= colB; i--) {
                    res.add(matrix[rowE][i]);
                }
            }
            rowE--;
            
            if(colB <= colE) {
                for(int i = rowE; i >= rowB; i--) {
                    res.add(matrix[i][colB]);
                }
            }
            colB++;
        }
        return res;
    }
}
```
