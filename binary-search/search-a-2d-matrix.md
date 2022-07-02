# Search a 2D Matrix

[https://leetcode.com/problems/search-a-2d-matrix/](https://leetcode.com/problems/search-a-2d-matrix/)

一个从前到后排好序的Matrix找target

> Write an efficient algorithm that searches for a value `target` in an `m x n` integer matrix `matrix`. This matrix has the following properties:
>
> * Integers in each row are sorted from left to right.
> * The first integer of each row is greater than the last integer of the previous row.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/10/05/mat.jpg)
>
> ```
> Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
> Output: true
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2020/10/05/mat2.jpg)
>
> ```
> Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
> Output: false
> ```

{% hint style="info" %}
单纯的Binary Search问题 只需记住 如何用当前位置找到行和列的位置\
mid / col = row    mid % col = col
{% endhint %}

```
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if(matrix == null || matrix.length == 0 || matrix[0].length == 0) return false;
        int row = matrix.length, col = matrix[0].length;
        int left = 0, right = row * col - 1;
        
        while(left + 1 < right){
            int mid = (right - left) / 2 + left;
            int num = matrix[mid / col][mid % col];
            if(num == target) {
                return true;
            }else if(num < target){
                left = mid;
            }else{
                right = mid;
            }
        }
        if(matrix[left / col][left % col] == target || matrix[right / col][right % col] == target){
            return true;
        }
        return false;
    }
}
```
