# Queue

Queue 是一种先进先出(FIFO)的数据结构



**队列操作 Operations of Queue:**

`enqueue` and `dequeue`

> The **insert** operation is also called **enqueue** and the new element is always `added at the end of the queue`.
>
> The **delete** operation is called **dequeue**. You are only allowed to `remove the first element`.



**Queue Usage Example**

Java - `peek()`, `offer()`, `poll()`, `size()`

```java
// "static void main" must be defined in a public class.
public class Main {
    public static void main(String[] args) {
        // 1. Initialize a queue.
        Queue<Integer> q = new LinkedList();
        // 2. Get the first element - return null if queue is empty.
        System.out.println("The first element is: " + q.peek());
        // 3. Push new element.
        q.offer(5);
        q.offer(13);
        q.offer(8);
        q.offer(6);
        // 4. Pop an element.
        q.poll();
        // 5. Get the first element.
        System.out.println("The first element is: " + q.peek());
        // 7. Get the size of the queue.
        System.out.println("The size is: " + q.size());
    }
}
```

In Java, **Queue** interface, with a couple of implementation e.g. **BlockingQueue**, **LinkedList**, and **PriorityQueue**.

### Queue Implementation

### Queue Using Array

Use a **fixed-size array** and **two pointers** to indicate the starting position and the ending position. And the goal is to **reuse** the **wasted** **storage** we mentioned previously.

```
class ArrayQueue {
    private int front,back;
    private Object[] array;
    public static final int MAX=100;

    public ArrayQueue() {
        front=0;
        back=0;
        array = new Object[MAX];
    }

    public Object first() {
        return array[front];
    }

    public void leave(){
        front++;
        if(front==MAX)
        front=0;
    }

    public void join(Object obj) {
        array[back++]=obj;
        if(back==MAX)
            back=0;
    }

    public boolean isEmpty() {
        return front==back;
    }
}
```

## Deque&#x20;

The Deque is related to the double-ended queue that supports the addition or removal of elements from either end of the data structure. It can either be used as a [queue(first-in-first-out/FIFO)](https://www.geeksforgeeks.org/queue/) or as a [stack(last-in-first-out/LIFO)](https://www.geeksforgeeks.org/stack/).

```
 Deque<Integer> dq = new ArrayDeque<>();
```

![](<../.gitbook/assets/image (2) (1) (2).png>)

对于添加元素到队尾的操作，`Queue`提供了`add()`/`offer()`方法，而`Deque`提供了`addLast()`/`offerLast()`方法。添加元素到对首、取队尾元素的操作在`Queue`中不存在，在`Deque`中由`addFirst()`/`removeLast()`等方法提供。
