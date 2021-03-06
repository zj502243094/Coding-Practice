# Hash

**Map:**

map.get() get the value mapped by a particular key It returns NULL when the map contains no such mapping for the key.



[`get`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html#get-java.lang.Object-)`(`[`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html) `key)`Returns the value to which the specified key is mapped, or `null` if this map contains no mapping for the key.

[`put`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html#put-K-V-)`(`[`K`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) `key,` [`V`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) `value)`Associates the specified value with the specified key in this map (optional operation).

[`values`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html#values--)`()`Returns a [`Collection`](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html) view of the values contained in this map.

[`containsKey`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html#containsKey-java.lang.Object-)`(`[`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html) `key)`Returns true if this map contains a mapping for the specified key.

[`containsValue`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html#containsValue-java.lang.Object-)`(`[`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html) `value)`Returns true if this map maps one or more keys to the specified value.

[`getOrDefault`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html#getOrDefault-java.lang.Object-V-)`(`[`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html) `key,` [`V`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) `defaultValue)`Returns the value to which the specified key is mapped, or `defaultValue` if this map contains no mapping for the key.    like : map.getOrDefault(c, 0)

[`putIfAbsent`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html#putIfAbsent-K-V-)`(`[`K`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) `key,` [`V`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) `value)`If the specified key is not already associated with a value (or is mapped to `null`) associates it with the given value and returns `null`, else returns the current value. &#x20;

\


**TreeSet**(sorted)&#x20;

The elements are ordered using their natural order(Ascending), or by Comparator when creation

log(n) (add, remove and contains).

floor(E e) ??????????????????????????????**??????**???????????????????????????**??????**???????????????????????????????????????,??????null.

ceiling(E e) ??????????????????????????????**??????**???????????????????????????**??????**???????????????????????????????????????,??????null.
