# Permutations II

[https://leetcode.com/problems/permutations-ii/](https://leetcode.com/problems/permutations-ii/)

> Given a collection of numbers, `nums`, that might contain duplicates, return _all possible unique permutations **in any order**._
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [1,1,2]
> <strong>Output:
> </strong>[[1,1,2],
>  [1,2,1],
>  [2,1,1]]</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [1,2,3]
> <strong>Output:
> </strong> [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]</code></pre>

{% hint style="info" %}
就是在于当判断出现重复元素时，如何处理。

when a number has the same value with its previous, we can use this number only if his previous is used

```java
if(i>0 &&nums[i-1]==nums[i] && !used[i-1]) continue;
```

简单一点的理解就是因为在循环中，如果nums\[i - 1]用过了，那么在backtracking的时候其实是会把used\[i - 1]重新设成false的，used\[ i - 1]为false，其实是说明nums\[ i - 1]在i - 1的时候被使用过了。
{% endhint %}

```
// Some code
```
