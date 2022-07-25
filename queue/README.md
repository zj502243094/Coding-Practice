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
