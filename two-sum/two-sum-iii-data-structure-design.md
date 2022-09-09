# Two Sum III - Data structure design

[https://leetcode.com/problems/two-sum-iii-data-structure-design/](https://leetcode.com/problems/two-sum-iii-data-structure-design/)

> Design a data structure that accepts a stream of integers and checks if it has a pair of integers that sum up to a particular value.
>
> Implement the `TwoSum` class:
>
> * `TwoSum()` Initializes the `TwoSum` object, with an empty array initially.
> * `void add(int number)` Adds `number` to the data structure.
> * `boolean find(int value)` Returns `true` if there exists any pair of numbers whose sum is equal to `value`, otherwise, it returns `false`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input
> ["TwoSum", "add", "add", "add", "find", "find"]
> [[], [1], [3], [5], [4], [7]]
> <strong>Output
> </strong>[null, null, null, null, true, false]
> <strong>Explanation
> </strong>TwoSum twoSum = new TwoSum();
> twoSum.add(1);   // [] --> [1]
> twoSum.add(3);   // [1] --> [1,3]
> twoSum.add(5);   // [1,3] --> [1,3,5]
> twoSum.find(4);  // 1 + 3 = 4, return true
> twoSum.find(7);  // No two integers sum up to 7, return false</code></pre>

{% hint style="info" %}
add O(1) find O(n)
{% endhint %}

```
class TwoSum {
    
    Map<Integer, Integer> map;
    public TwoSum() {
        map = new HashMap<>();
    }
    
    public void add(int number) {
        map.put(number, map.getOrDefault(number, 0) + 1);
    }
    
    public boolean find(int value) {
        if (map.size() == 0) return false;
        for (int key : map.keySet()) {
            int diff = value - key;
            if (diff == key && map.get(key) > 1) return true;
            if (diff != key && map.containsKey(diff)) return true;
        }
        return false;
    }
}
```

{% hint style="info" %}
如果大多数是 find 操作&#x20;

add O(n2) find O(1)
{% endhint %}

```
class TwoSum {

    Set<Integer> nums;
    Set<Integer> sums;
    public TwoSum() {
        nums = new HashSet<>();
        sums = new HashSet<>();
    }
    
    public void add(int number) {
        for (int n : nums) sums.add(number + n);
        nums.add(number);
    }
    
    public boolean find(int value) {
        return sums.contains(value);
    }
}
```
