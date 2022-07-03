# Wood Cut / Koko Eating Bananas

[https://www.lintcode.com/problem/183/](https://www.lintcode.com/problem/183/)

切木头 将几个木头 切成满足最少切出K块木头  找出能切出最长的长度

> Given n pieces of wood with length `L[i]` (integer array). Cut them into small pieces to guarantee you could have equal or more than k pieces with the same length. What is the longest length you can get from the n pieces of wood? Given L & k, return the maximum length of the small pieces.
>
> ***
>
> Example
>
> **Example 1:**
>
> ```
> Input: wood = [5, 9, 7], k = 3
> Output: 5
> Explanation: 
> 5 -> 5
> 9 -> 5 + 4
> 7 -> 5 + 2
> ```
>
> **Example 2:**
>
> ```
> Input: wood = [5, 9, 7], k = 4
> Output: 4
> Explanation: 
> 5 -> 4 + 1
> 9 -> 4 * 2 + 1
> 7 -> 4 + 3
> ```
>
> **Example 3**
>
> ```
> Input:
> L = [232, 124, 456]
> k = 7
> Output: 114
> Explanation: We can cut it into 7 pieces if any piece is 114 long, however we can't cut it into 7 pieces if any piece is 115 long.
> And for the 124 logs, the excess can be discarded and not used in its entirety.
> ```
>
> **Example 4**
>
> ```
> Input:
> L = [1, 2, 3]
> k = 7
> Output: 0 Explanation: It is obvious we can't make it.
> ```

{% hint style="info" %}
找出最大的（最后一个）满足最少能切出K段木材的木材长
{% endhint %}

```
public class Solution {
    /**
     * @param l: Given n pieces of wood with length L[i]
     * @param k: An integer
     * @return: The maximum length of the small pieces
     */
    public int woodCut(int[] woods, int k) {
        if(woods == null || woods.length == 0) return 0;
        int l = 1, r = 0;
        for(int i : woods){
            r = Math.max(r, i);
        }
        while(l + 1 < r){
            int mid = (r - l) / 2 + l;
            if(count(woods, mid) >= k){
                l = mid;
            }else{
                r = mid;
            }
        }
        if(count(woods, r) >= k) return r;
        if(count(woods, l) >= k) return l;
        return 0;
    }
    private int count(int[] woods, int len){
        int num = 0;
        for(int wood : woods){
            num += wood / len;
        }
        return num;
    }
}
```

\
[https://leetcode.com/problems/koko-eating-bananas/](https://leetcode.com/problems/koko-eating-bananas/)\
猴子在管理员离开的H小时内 将香蕉吃完 每次吃最少的数量K

> Koko loves to eat bananas. There are `n` piles of bananas, the `ith` pile has `piles[i]` bananas. The guards have gone and will come back in `h` hours.
>
> Koko can decide her bananas-per-hour eating speed of `k`. Each hour, she chooses some pile of bananas and eats `k` bananas from that pile. If the pile has less than `k` bananas, she eats all of them instead and will not eat any more bananas during this hour.
>
> Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.
>
> Return _the minimum integer_ `k` _such that she can eat all the bananas within_ `h` _hours_.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: piles = [3,6,7,11], h = 8
> Output: 4
> ```
>
> **Example 2:**
>
> ```
> Input: piles = [30,11,23,4,20], h = 5
> Output: 30
> ```
>
> **Example 3:**
>
> ```
> Input: piles = [30,11,23,4,20], h = 6
> Output: 23
> ```

{% hint style="info" %}
找出最小（第一个）吃完的吃K香蕉数量能在不超过H小时吃完  吃不完剩下的香蕉也要用1H吃
{% endhint %}

```
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        if(piles == null || piles.length == 0) return -1;
        int left = 1, right = 0;
        for(int pile : piles){
            right = Math.max(right, pile);
        }
        while(left + 1 < right) {
            int mid = (right - left) / 2 + left;
            if(count(piles, mid) <= h){
                right = mid;
            }else{
                left = mid;
            }
        }
        if(count(piles, left) <= h) return left;
        if(count(piles, right) <= h) return right;
        return -1;
    }
    private int count(int[] piles, int k){
        int hours = 0;
        for(int pile : piles){
            hours += pile / k;
            if(pile % k != 0) hours++;
        }
        return hours;
    }
}
```
