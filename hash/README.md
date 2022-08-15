# Hash

**Map:**

[`getOrDefault`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html#getOrDefault-java.lang.Object-V-)`(`[`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html) `key,` [`V`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) `defaultValue)`Returns the value to which the specified key is mapped, or `defaultValue` if this map contains no mapping for the key.    like : map.getOrDefault(c, 0)

[`putIfAbsent`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html#putIfAbsent-K-V-)`(`[`K`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) `key,` [`V`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) `value)`If the specified key is not already associated with a value (or is mapped to `null`) associates it with the given value and returns `null`, else returns the current value. &#x20;

[`computeIfAbsent`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html#computeIfAbsent-K-java.util.function.Function-)`(`[`K`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) `key,` [`Function`](https://docs.oracle.com/javase/8/docs/api/java/util/function/Function.html)`<? super` [`K`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html)`,? extends` [`V`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html)`> mappingFunction)`If the specified key is not already associated with a value (or is mapped to `null`), attempts to compute its value using the given mapping function and enters it into this map unless `null`

[`keySet`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html#keySet--)`()`Returns a [`Set`](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html) view of the keys contained in this map.

[`entrySet`](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html#entrySet--)`()`Returns a [`Set`](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html) view of the mappings contained in this map.

| [clear()](https://www.runoob.com/java/java-hashmap-clear.html)                       | 删除 hashMap 中的所有键/值对                                  |
| ------------------------------------------------------------------------------------ | ---------------------------------------------------- |
| [clone()](https://www.runoob.com/java/java-hashmap-clone.html)                       | 复制一份 hashMap                                         |
| [isEmpty()](https://www.runoob.com/java/java-hashmap-isempty.html)                   | 判断 hashMap 是否为空                                      |
| [size()](https://www.runoob.com/java/java-hashmap-size.html)                         | 计算 hashMap 中键/值对的数量                                  |
| [put()](https://www.runoob.com/java/java-hashmap-put.html)                           | 将键/值对添加到 hashMap 中                                   |
| [putAll()](https://www.runoob.com/java/java-hashmap-putall.html)                     | 将所有键/值对添加到 hashMap 中                                 |
| [putIfAbsent()](https://www.runoob.com/java/java-hashmap-putifabsent.html)           | 如果 hashMap 中不存在指定的键，则将指定的键/值对插入到 hashMap 中。          |
| [remove()](https://www.runoob.com/java/java-hashmap-remove.html)                     | 删除 hashMap 中指定键 key 的映射关系                            |
| [containsKey()](https://www.runoob.com/java/java-hashmap-containskey.html)           | 检查 hashMap 中是否存在指定的 key 对应的映射关系。                     |
| [containsValue()](https://www.runoob.com/java/java-hashmap-containsvalue.html)       | 检查 hashMap 中是否存在指定的 value 对应的映射关系。                   |
| [replace()](https://www.runoob.com/java/java-hashmap-replace.html)                   | 替换 hashMap 中是指定的 key 对应的 value。                      |
| [replaceAll()](https://www.runoob.com/java/java-hashmap-replaceall.html)             | 将 hashMap 中的所有映射关系替换成给定的函数所执行的结果。                    |
| [get()](https://www.runoob.com/java/java-hashmap-get.html)                           | 获取指定 key 对应对 value                                   |
| [getOrDefault()](https://www.runoob.com/java/java-hashmap-getordefault.html)         | 获取指定 key 对应对 value，如果找不到 key ，则返回设置的默认值              |
| [forEach()](https://www.runoob.com/java/java-hashmap-foreach.html)                   | 对 hashMap 中的每个映射执行指定的操作。                             |
| [entrySet()](https://www.runoob.com/java/java-hashmap-entryset.html)                 | 返回 hashMap 中所有映射项的集合集合视图。                            |
| [keySet](https://www.runoob.com/java/java-hashmap-keyset.html)()                     | 返回 hashMap 中所有 key 组成的集合视图。                          |
| [values()](https://www.runoob.com/java/java-hashmap-values.html)                     | 返回 hashMap 中存在的所有 value 值。                           |
| [merge()](https://www.runoob.com/java/java-hashmap-merge.html)                       | 添加键值对到 hashMap 中                                     |
| [compute()](https://www.runoob.com/java/java-hashmap-compute.html)                   | 对 hashMap 中指定 key 的值进行重新计算                           |
| [computeIfAbsent()](https://www.runoob.com/java/java-hashmap-computeifabsent.html)   | 对 hashMap 中指定 key 的值进行重新计算，如果不存在这个 key，则添加到 hasMap 中 |
| [computeIfPresent()](https://www.runoob.com/java/java-hashmap-computeifpresent.html) | 对 hashMap 中指定 key 的值进行重新计算，前提是该 key 存在于 hashMap 中。   |



**TreeSet**(sorted)&#x20;

The elements are ordered using their natural order(Ascending), or by Comparator when creation

log(n) (add, remove and contains).

floor(E e) 方法返回在这个集合中**小于**或者等于给定元素的**最大**元素，如果不存在这样的元素,返回null.

ceiling(E e) 方法返回在这个集合中**大于**或者等于给定元素的**最小**元素，如果不存在这样的元素,返回null.
