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
    
    ```cpp
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
# current loaded modules
module list
# modules available
module avail
module use /projects/comp422/modulefiles
module load cilkplus
```

### Speedup Demo

```bash
[fib]$ make runp
use make runp W=nworkers N=fibonacci_number
./fib 44
calculated fibonacci(44) = 701408733 with 8 workers in 4.223 seconds
# approximate linear speedup
[fib]$ make runp W=4
use make runp W=nworkers N=fibonacci_number
CILK_NWORKERS=4 ./fib 44
calculated fibonacci(44) = 701408733 with 4 workers in 8.163 seconds
# serial faster, granularity too small
# add -cilk-serialize option for fib.cpp
[fib]$ make runs
use make runs N=fibonacci_number
./fib-serial 44
calculated fibonacci(44) = 701408733 with 1 workers in 3.039 seconds
```

### Granularity Demo

increasing the granularity of parallel work in fib improves performance (by reducing c1)

```bash
[fib]$ make runt
use make runt W=nworkers N=fibonacci_number H=serial_levels
./fib-trunc 44 2
calculated fibonacci(44) = 701408733 with 8 workers in 4.383 seconds
[fib]$ make runt H=4
use make runt W=nworkers N=fibonacci_number H=serial_levels
./fib-trunc 44 4
calculated fibonacci(44) = 701408733 with 8 workers in 1.858 seconds
[fib]$ make runt H=8
use make runt W=nworkers N=fibonacci_number H=serial_levels
./fib-trunc 44 8
calculated fibonacci(44) = 701408733 with 8 workers in 0.606 seconds
[fib]$ make runt H=16
use make runt W=nworkers N=fibonacci_number H=serial_levels
./fib-trunc 44 16
calculated fibonacci(44) = 701408733 with 8 workers in 0.374 seconds
```

Core: enough parallelism and granularity

### cilk_for

```cpp
// implicit silk_sync at the end of a cilk_for
cilk_for (T v = begin; v < end; v++) {
    statement_1;
    statement_2;
    ...
}
```

#### cilk-spawn vs. cilk_for

![Screen Shot 2022-09-12 at 15.32.52.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-15-32-56-Screen%20Shot%202022-09-12%20at%2015.32.52.png)

![Screen Shot 2022-09-12 at 15.36.15.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-15-36-19-Screen%20Shot%202022-09-12%20at%2015.36.15.png)

##### cilk_for grain size

![Screen Shot 2022-09-12 at 15.37.18.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-15-37-23-Screen%20Shot%202022-09-12%20at%2015.37.18.png)

### Data Race

![Screen Shot 2022-09-12 at 15.58.10.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-15-58-15-Screen%20Shot%202022-09-12%20at%2015.58.10.png)

![Screen Shot 2022-09-12 at 16.00.52.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-16-00-55-Screen%20Shot%202022-09-12%20at%2016.00.52.png)

![Screen Shot 2022-09-12 at 16.01.18.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-16-01-21-Screen%20Shot%202022-09-12%20at%2016.01.18.png)

![Screen Shot 2022-09-12 at 16.02.03.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-16-02-06-Screen%20Shot%202022-09-12%20at%2016.02.03.png)

![Screen Shot 2022-09-12 at 16.04.15.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-16-04-19-Screen%20Shot%202022-09-12%20at%2016.04.15.png)

![Screen Shot 2022-09-12 at 16.09.05.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-16-09-09-Screen%20Shot%202022-09-12%20at%2016.09.05.png)

- two nodes: spawn + sync

- The continuation gets an identity value $x_1$

![Screen Shot 2022-09-12 at 16.09.57.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-16-10-01-Screen%20Shot%202022-09-12%20at%2016.09.57.png)

![Screen Shot 2022-09-12 at 16.12.50.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-16-12-52-Screen%20Shot%202022-09-12%20at%2016.12.50.png)

![Screen Shot 2022-09-12 at 16.13.30.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-16-13-35-Screen%20Shot%202022-09-12%20at%2016.13.30.png)

![Screen Shot 2022-09-12 at 16.16.15.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-16-16-18-Screen%20Shot%202022-09-12%20at%2016.16.15.png)

### Reducer Demo

```bash
[sum]$ ./race 10000
program ./race
Computing the sum from 1 to 10000 [serial]
The sum from 1 to 10000 [serial] in 0.000 seconds is 50005000
# cilk_spawn
Computing the sum from 1 to 10000 [parallel: recursive tasks, 8 workers]
The sum from 1 to 10000 [parallel: recursive tasks, 8 workers] in 0.001 seconds is 30213708
# cilk_for, correct for small data for default grain size
Computing the sum from 1 to 10000 [parallel: loop, 8 workers]
The sum from 1 to 10000 [parallel: loop, 8 workers] in 0.000 seconds is 1709160


# race version
[sum]$ time ./race 100000000
program ./race
Computing the sum from 1 to 100000000 [serial]
The sum from 1 to 100000000 [serial] in 0.027 seconds is 5000000050000000
Computing the sum from 1 to 100000000 [parallel: recursive tasks, 8 workers]
The sum from 1 to 100000000 [parallel: recursive tasks, 8 workers] in 8.747 seconds is 985944456618861
Computing the sum from 1 to 100000000 [parallel: loop, 8 workers]
The sum from 1 to 100000000 [parallel: loop, 8 workers] in 0.012 seconds is 3913299751757

real    0m8.794s
user    1m9.970s
sys    0m0.005s


# lock version
[sum]$ time ./lock 100000000
program ./lock
Computing the sum from 1 to 100000000 [serial]
The sum from 1 to 100000000 [serial] in 0.027 seconds is 5000000050000000
Computing the sum from 1 to 100000000 [parallel: recursive tasks, lock, 8 workers]
The sum from 1 to 100000000 [parallel: recursive tasks, lock, 8 workers] in 21.639 seconds is 5000000050000000
Computing the sum from 1 to 100000000 [parallel: loop, lock, 8 workers]
The sum from 1 to 100000000 [parallel: loop, lock, 8 workers] in 10.849 seconds is 5000000050000000

real    0m32.524s
user    0m33.814s
sys    3m26.855s


# reducer version
cilk::reducer_opadd<long> global_sum(0);

[sum]$ time ./reducer 100000000
program ./reducer
Computing the sum from 1 to 100000000 [serial]
The sum from 1 to 100000000 [serial] in 0.027 seconds is 5000000050000000
Computing the sum from 1 to 100000000 [parallel: recursive tasks, reducer, 8 workers]
The sum from 1 to 100000000 [parallel: recursive tasks, reducer, 8 workers] in 0.446 seconds is 5000000050000000
The sum from 1 to 100000000 [parallel: loop, reducer, 8 workers] in 0.005 seconds is 5000000050000000

real    0m0.483s
user    0m3.630s
sys    0m0.004s
```

- Reducer is much faster than serialize: when doing serialize, every thread is hitting on the same cache line, doing the read and write. Reducer: every thread work on different copies.

- reducer demo II:
  
  - one where iterations race to write output  
  - one where iterations write output using an ostream reducer

```cpp
// keep in order, only cilk_for does not guarantee.
cilk::reducer_ostream rcout(cout);
cilk_for(int i = 1; i <= n; i++) {
    if (i % emit == 0) rcout << "In iteration " << i << endl;
}
```

### cilkscreen

![Screen Shot 2022-09-12 at 16.42.29.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-16-42-31-Screen%20Shot%202022-09-12%20at%2016.42.29.png)

![Screen Shot 2022-09-12 at 16.43.39.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-16-43-42-Screen%20Shot%202022-09-12%20at%2016.43.39.png)

![Screen Shot 2022-09-12 at 16.49.04.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-16-49-08-Screen%20Shot%202022-09-12%20at%2016.49.04.png)

```cpp
line 22: if (u == 1) { LOCK; sum += 1; UNLOCK; }
```

```bash
[races]$ cilkscreen ./race 1000
Cilkscreen Race Detector V2.0.0, Build 4501
summing integers from 0 to 1000

Race condition on location 0x602084
  write access at 0x40102a: (/projects/comp422/cilkplus-examples/races/race.c:22, do_accum+0x1f0)
  read access at 0x401024: (/projects/comp422/cilkplus-examples/races/race.c:22, do_accum+0x1ea)
    called by 0x4011a6: (/projects/comp422/cilkplus-examples/races/race.c:26, do_accum+0x36c)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x401355: (/projects/comp422/cilkplus-examples/races/race.c:35, main+0x85)

Race condition on location 0x602084
  write access at 0x40102a: (/projects/comp422/cilkplus-examples/races/race.c:22, do_accum+0x1f0)
  write access at 0x40102a: (/projects/comp422/cilkplus-examples/races/race.c:22, do_accum+0x1f0)
    called by 0x4011a6: (/projects/comp422/cilkplus-examples/races/race.c:26, do_accum+0x36c)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x4010be: (/projects/comp422/cilkplus-examples/races/race.c:25, do_accum+0x284)
    called by 0x401355: (/projects/comp422/cilkplus-examples/races/race.c:35, main+0x85)
sum = 500500
serial sum = 500500
2 errors found by Cilkscreen
Cilkscreen suppressed 2998 duplicate error messages

# -DSYNCH
[races]$ cilkscreen ./races 1000
Cilkscreen Race Detector V2.0.0, Build 4501
summing integers from 0 to 1000
sum = 500500
serial sum = 500500
No errors found by Cilkscreen
```

### cilkview

![Screen Shot 2022-09-12 at 17.00.49.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/09/12-17-00-59-Screen%20Shot%202022-09-12%20at%2017.00.49.png)
```bash
Cilk Parallel Region(s) Statistics - Elapsed time: 0.043 seconds
1) Parallelism Profile
   Work :					 25,857,125 instructions
   Span :					 4,925 instructions
   Burdened span :				 594,925 instructions
   Parallelism :				 5250.18
   Burdened parallelism :			 43.46
   Number of spawns/syncs:			 121,392
   Average instructions / strand :		 71
   Strands along span :				 24
   Average instructions / strand on span :	 205
   Total number of atomic instructions : 	 121,395
   Frame count :				 364,176
   Entries to parallel region :			 1

2) Speedup Estimate
     2 processors:	 1.90 - 2.00
     4 processors:	 3.58 - 4.00
     8 processors:	 6.28 - 8.00
    16 processors:	 10.08 - 16.00
    32 processors:	 14.46 - 32.00
    64 processors:	 18.47 - 64.00
   128 processors:	 21.45 - 128.00
   256 processors:	 23.33 - 256.00
```

### HPCToolkit
