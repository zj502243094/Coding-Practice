# 3Sum With Multiplicity

[https://leetcode.com/problems/3sum-with-multiplicity/](https://leetcode.com/problems/3sum-with-multiplicity/)

> Given an integer array `arr`, and an integer `target`, return the number of tuples `i, j, k` such that `i < j < k` and `arr[i] + arr[j] + arr[k] == target`.
>
> As the answer can be very large, return it **modulo** `109 + 7`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: arr = [1,1,2,2,3,3,4,4,5,5], target = 8
> <strong>Output:
> </strong> 20
> <strong>Explanation: 
> </strong>Enumerating by the values (arr[i], arr[j], arr[k]):
> (1, 2, 5) occurs 8 times;
> (1, 3, 4) occurs 8 times;
> (2, 2, 4) occurs 2 times;
> (2, 3, 3) occurs 2 times.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: arr = [1,1,2,2,2,2], target = 5
> <strong>Output:
> </strong> 12
> <strong>Explanation: 
> </strong>arr[i] = 1, arr[j] = arr[k] = 2 occurs 12 times:
> We choose one 1 from [1,1] in 2 ways,
> and two 2s from [2,2,2,2] in 6 ways.</code></pre>

```
class Solution {
    private int mod = 1000000007;
    public int threeSumMulti(int[] arr, int target) {
        long res = 0;
        Map<Integer, Integer> map = new HashMap<>();
        for (int a : arr) map.put(a, map.getOrDefault(a, 0) + 1);
        for (int i : map.keySet()) {
            for (int j : map.keySet()) {
                int k = target - i - j;
                if (map.containsKey(k)) {
                    long cnt1 = map.get(i);
                    long cnt2 = map.get(j);
                    long cnt3 = map.get(k);
                    if (i == j && j == k) {
                        res += cnt1 * (cnt1 - 1) * (cnt1 - 2) / 6;
                    } else if (i == j) {
                        res += cnt1 * (cnt1 - 1) / 2 * cnt3;
                    } else if (i < j && j < k) {
                        res += cnt1 * cnt2 * cnt3;
                    }
                    res %= mod;
                }
            }
        }
        return (int) res;
    }
}
```
