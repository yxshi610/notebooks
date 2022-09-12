# Resources

- Rice COMP534: Parrallel Computing
- MIT 6.895 Theory of Parallel Systems
- the Internet

# Thread

shared-memory parallel system

Thread: an independent flow of control

- software entity that executes a sequence of instructions  

Thread requires

- program counter
- a set of registers
- an area in memory, including a call stack
- a thread id

A process consists of one or more threads that share

- address space 
- attributes including user id, open files, working dir, ...

![](https://ask.qcloudimg.com/http-save/yehe-1346475/1ouurs2116.png?imageView2/2/w/1620)
所属线程的栈区、程序计数器、栈指针以及函数运行使用的寄存器是线程私有的, 就是线程上下文, thread context. 线程共享进程地址空间中除线程上下文信息中的所有内容。e.g.数据区：全局变量，堆区：malloc/new出来的数据，只要知道地址线程就可以访问。同样的，尽管栈区是线程的私有数据，但没有保护机制，所以只要传入地址也可以修改任何一个线程的栈区。

# Cilk Plus

Mapping techniques for load balancing

- static mapping
- dynamic mappings
  - centralized
    - *slaves* request from *master* (may become bottleneck)
  - distributed
    - all *peers*

## Clik Plus Programming Model

- A simple and powerful model for writing multithreaded programs

- extends C/C++ with three new keywords
  
  - cilk_spawn: invoke a function (potentially) in parallel
  - cilk_sync: wailt for a procedures's spawned functions to finish
  - cilk_for: execute a loop in parallel

- Cilk Plus programs specify logical parallelism
  
  - not mapping of work to threads or cores
  
  - do not explicitly state which tasks are assigned to which processors.  It is the ***scheduler***'s job to determine how to map dynamically unfolding execution onto a set of processors
    
    ```c
    unsigned int fib(unsigned int n) {
    if (n < 2) return n;
    else {
        unsigned int n1, n2;
        n1 = cilk_spawn fib(n-1);
        n2 = cilk_spawn fib(n-2);
        cilk_sync;
        return (n1 + n1);
    }
    }
    ```

## Algorithmic Complexity Measures

$T_p=$ execution time on $P$ processors.  
$T_1=$ work.  
$T_\infty =$ span, also called *critical-path length*  
*parallelism* (or ideal speedup): $T_1/T_\infty$  
*parallel slackness*: $(T_1/T_\infty)/P$

- model the instruction stream of a program as a **computation directed acyclic graph (DAG)**. Vertices are ***threads*** which is a maximal sequence of instructions not containing parallel control.

- We have three threads/strands.

![Screen Shot 2022-09-11 at 23.17.57.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/11-23-18-00-Screen%20Shot%202022-09-11%20at%2023.17.57.png)

![Screen Shot 2022-09-11 at 23.21.50.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/11-23-21-53-Screen%20Shot%202022-09-11%20at%2023.21.50.png)

![Screen Shot 2022-09-11 at 21.45.49.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/11-21-45-52-Screen%20Shot%202022-09-11%20at%2021.45.49.png)

## Task Scheduling

- work-sharing: task scheduled to run in parallel at every spawn
- work-stealing: processor looks for work when it becomes idle

### Cilk's Work-Stealing Scheduler

![Screen Shot 2022-09-11 at 21.49.54.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/11-21-49-56-Screen%20Shot%202022-09-11%20at%2021.49.54.png)

![Screen Shot 2022-09-11 at 21.50.04.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/11-21-50-07-Screen%20Shot%202022-09-11%20at%2021.50.04.png)

![Screen Shot 2022-09-11 at 21.50.51.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/11-21-50-53-Screen%20Shot%202022-09-11%20at%2021.50.51.png)

Theorem: achieves an expected running time of $T_P<=T_1/P+O(T_\infty)$ on $P$ processors.  

![Screen Shot 2022-09-11 at 22.58.03.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/11-22-58-06-Screen%20Shot%202022-09-11%20at%2022.58.03.png)

![Screen Shot 2022-09-11 at 23.00.52.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/11-23-00-54-Screen%20Shot%202022-09-11%20at%2023.00.52.png)

![Screen Shot 2022-09-11 at 23.01.37.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/11-23-01-42-Screen%20Shot%202022-09-11%20at%2023.01.37.png)

- not only a few large chunks
  - may not be enough parallelism to keep all the cores busy
- not too many very small chunks
  - scheduling overhead may overwhelm the benefit of parallelism

![Screen Shot 2022-09-11 at 23.03.06.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/11-23-03-10-Screen%20Shot%202022-09-11%20at%2023.03.06.png)

```bash
module use /projects/comp422/modulefiles
module load cilkplus
```
