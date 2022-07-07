# Recursion

递归就是在函数里调用自身  在使用递归策略时，必须有一个递归结束条件

![](<.gitbook/assets/image (6).png>)

递归只用写一个函数，自己调用自己 – 不用写多个函数 factorial5(), factorial4(), …, factorial1()&#x20;

递归进行过程中，每一层的变量值都被Java语言自动存进栈stack里，不用自己处理

递归中最容易出错的地方就是忘记停止条件 – 如果没有停止条件，递归会无限进行下去，直到系统的栈空间被撑爆，即 Stack Overflow
