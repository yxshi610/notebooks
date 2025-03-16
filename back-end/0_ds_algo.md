# 数据结构与算法
## 数组
```java
boolean[] isPrime = new boolean[n];
Arrays.fill(isPrime, true);
```
## 列表

```java
LinkedList<Integer> linkedList = new LinkedList<>();
linkedList.addLast(i);
linkedList.pollLast();
linkedList.pollFirst();
linkedList.getFirst();
```
## 堆
完全二叉树
### 堆排序
https://www.bilibili.com/video/BV1HYtseiEQ8
1. 建堆O(N): 从最后一个非叶节点开始一次向下调整.  
2. 排序O(NlogN): 每轮堆顶换到最后, 向下调整新的堆顶.  

## 队列
Java常用Queue

```java
Queue<Integer> q = new LinkedList<>();
q.offer(t);
q.poll();
q.peek();
```
Java常用PriorityQueue:  
```java
PriorityQueue<ListNode> pq = new PriorityQueue<>(((o1, o2) -> o1.val - o2.val));
pq.offer(t);
```

## 栈
Java常用Stack

```java
Stack<Integer> stk = new Stack();
stk.push(t);
stk.pop();
stk.peep();
```