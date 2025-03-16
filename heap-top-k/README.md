# Heap / Top K

## Heap Definition

(Binary) **Heap** is a special case of \[**complete** binary tree] (**balanced** **binary** **tree)** data structure where the **root-node key** is compared with its **children** and arranged accordingly.

**Min-Heap** − Where the value of the root node is less than or equal to either of its children.

**Max-Heap** − Where the value of the root node is greater than or equal to either of its children.

[https://www.tutorialspoint.com/data\_structures\_algorithms/heap\_data\_structure.htm](https://www.tutorialspoint.com/data_structures_algorithms/heap_data_structure.htm)\


* **插入 :** 数组最后增加一个元素，然后对这个元素做上移操作（Shift Up）
  * 将新元素放到`heap[size+1]`的位置每次比较它的它父亲元素，如果小于它的父亲，证明现在不满 足堆的性质，然后向上**Shift Up**
* **删除 :**  最后一个元素和根交换，然后对新的根做下移操作&#x20;
  * 将根节点和最后一个节点进行交换如果该节点大于其中一个儿子，那么将其与其较小的儿子进行交换做**Shift Down，**&#x76F4;到该节点的儿子均大于它的值，或者它的儿子为空

![](<../.gitbook/assets/image (11) (4).png>)

**Interface 接口**\
• O(logN) Push -> Sift Up\
• O(logN) Pop -> Sift Down • O(1) Top\
• O(N) Delete\
\
Heap Application

> Priority Queue: Priority queues can be efficiently implemented using Binary Heap because it supports insert(), delete() and extractmax(), decreaseKey() operations in O(logn) time.

[https://www.geeksforgeeks.org/binary-heap/](https://www.geeksforgeeks.org/binary-heap/)

![](<../.gitbook/assets/image (14) (1).png>)
