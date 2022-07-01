# Guess Number Higher or Lower/Search in a Big Sorted Array

[https://leetcode.com/problems/guess-number-higher-or-lower/](https://leetcode.com/problems/guess-number-higher-or-lower/)

> We are playing the Guess Game. The game is as follows:
>
> I pick a number from `1` to `n`. You have to guess which number I picked.
>
> Every time you guess wrong, I will tell you whether the number I picked is higher or lower than your guess.
>
> You call a pre-defined API `int guess(int num)`, which returns three possible results:
>
> * `-1`: Your guess is higher than the number I picked (i.e. `num > pick`).
> * `1`: Your guess is lower than the number I picked (i.e. `num < pick`).
> * `0`: your guess is equal to the number I picked (i.e. `num == pick`).
>
> Return _the number that I picked_.

```
/** 
 * Forward declaration of guess API.
 * @param  num   your guess
 * @return 	     -1 if num is higher than the picked number
 *			      1 if num is lower than the picked number
 *               otherwise return 0
 * int guess(int num);
 */

public class Solution extends GuessGame {
    public int guessNumber(int n) {
        int left = 1, right = n;
        while(left + 1 < right){
            int mid = (right - left) / 2 + left;
            if(guess(mid) == 0){
                return mid;
            } 
            if(guess(mid) == -1) right = mid;
            if(guess(mid) == 1) left = mid;
        }
        if(guess(left) == 0) return left;
        return right;
    }
}
```



[https://www.lintcode.com/problem/447/](https://www.lintcode.com/problem/447/)

> Given a big sorted array with non-negative integers sorted by non-decreasing order. The array is so big so that you can not get the length of the whole array directly, and you can only access the kth number by `ArrayReader.get(k)`&#x20;
>
> Find the first index of a target number. Your algorithm should be in O(log k), where k is the first index of the target number.
>
> Return -1, if the number doesn't exist in the array.
>
> If you accessed an inaccessible index (outside of the array), ArrayReader.get will return `2,147,483,647`.
>
> Example
>
> **Example 1:**
>
> ```
> Input: [1, 3, 6, 9, 21, ...], target = 3
> Output: 1
> ```
>
> **Example 2:**
>
> ```
> Input: [1, 3, 6, 9, 21, ...], target = 4
> Output: -1
> ```
>
>

{% hint style="info" %}
因为是非常大的数组 即使每次减半还是很慢 所以需要用每次右端点指数 X2 与target比较


{% endhint %}

```
public class Solution {
    /*
     * @param reader: An instance of ArrayReader.
     * @param target: An integer
     * @return: An integer which is the first index of target.
     */
    public int searchBigSortedArray(ArrayReader reader, int target) {
        int right = 1;
        while(reader.get(right) < target) {
            right *= 2;
        }
        
        int left = right / 2;
        while(left + 1 < right){
            int mid = (right - left) / 2 + left;
            if(reader.get(mid) < target){
                left = mid;
            }else{
                right = mid;
            }
        }
        
        if(reader.get(left) == target){
            return left;
        }
        if(reader.get(right) == target){
            return right;
        }
        return -1;
    }
}
```
