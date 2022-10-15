Resources:

- UCB, CS61C

- the Internet

#### Conversion

1KiB=$2^{10}$Byte

1MiB=2^20Byte

1GiB=2^30Byte

M=10^6

G=10^9

n=10^(-9)

1 billion=10^9

milli=10^(-3)

micro=10^(-6)

#### Number Representation

Bases, 进制转换**conversion**

一对多：https://tool.lu/hexconvert/

一对一支持浮点：https://tool.oschina.net/hexconvert/

1. unsigned

2. sign and magnitude
   
   MSB=1->negative

3. one's complement (two 0)
   
   MSB=0->same as 2
   
   MSB=1->flip and get the positive value

4. two's complement (补码)
   
   - 正数和0的补码就是该数字本身再补上最高比特0。负数的补码则是将其对应正数按位取反再加1
   
   - conversion: 正数本身，负数在正数上取反+1
   
   - $-2^{n-1}$~$2^{n-1}-1$

5. Biased
   
   generally -2^(n-1)-1
   
   ![Screen Shot 2022-10-12 at 20.08.24.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-08-26-Screen%20Shot%202022-10-12%20at%2020.08.24.png)

6. floating point
   
   bias=-127
   
   ![Screen Shot 2022-10-12 at 20.09.05.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-09-07-Screen%20Shot%202022-10-12%20at%2020.09.05.png)
   
   ![Screen Shot 2022-10-12 at 20.09.15.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-09-17-Screen%20Shot%202022-10-12%20at%2020.09.15.png)
   
   smallest integer unrepresentable by 23 mantissa:
   
   ![Screen Shot 2022-10-12 at 20.09.27.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-09-29-Screen%20Shot%202022-10-12%20at%2020.09.27.png)

**bit shift:**

![Screen Shot 2022-10-12 at 20.10.16.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-10-19-Screen%20Shot%202022-10-12%20at%2020.10.16.png)

#### C

proof of **prime numbers' infinity** : 

![Screen Shot 2022-10-12 at 20.10.32.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-10-35-Screen%20Shot%202022-10-12%20at%2020.10.32.png)

the order of **dereferences and increments** (and also ++):

![Screen Shot 2022-10-12 at 20.10.44.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-10-48-Screen%20Shot%202022-10-12%20at%2020.10.44.png)

**Extern:** this thing is defined somewhere else

**declaration(1) and definition(1+2):**

1. tell the compiler what kind of the variable; 2. allocate memory for variables

![Screen Shot 2022-10-12 at 20.11.04.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-11-06-Screen%20Shot%202022-10-12%20at%2020.11.04.png)

#### CALL

- Compiler: .c->.s(a)

- Assembler: .s(a)->.o + information tables (symbol table, relocation table: to be handled in linker)
  
  - forward reference problem: two pass = remember position of labels (expend psudo) + use positions to generate code (jump only inside the file)

- Linker: .o + info tables-> .out (executable code)
  
  - go through relocation table and resolves references

- Loader: disk->RAM

#### RISC-V(Reduced Instruction Set Computing)

The basic command to run a given RISC-V file is as follows: 

`java -jar ../tools/venus.jar <FILENAME>`

##### RISC-V Instructions<->Machine Code

The 6 Instruction Formats

![Screen Shot 2022-10-12 at 20.11.24.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-11-26-Screen%20Shot%202022-10-12%20at%2020.11.24.png)

CORE INSTRUCTION FORMATS

![Screen Shot 2022-10-12 at 20.11.36.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-11-39-Screen%20Shot%202022-10-12%20at%2020.11.36.png)

the order of sub

![Screen Shot 2022-10-12 at 20.11.47.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-11-49-Screen%20Shot%202022-10-12%20at%2020.11.47.png)

registers

![Screen Shot 2022-10-12 at 20.11.56.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-12-00-Screen%20Shot%202022-10-12%20at%2020.11.56.png)

calling convention

![Screen Shot 2022-10-12 at 20.13.00.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-13-03-Screen%20Shot%202022-10-12%20at%2020.13.00.png)

function calls: jal & jalr

![Screen Shot 2022-10-12 at 20.13.13.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-13-16-Screen%20Shot%202022-10-12%20at%2020.13.13.png)

#### Truth Table to Boolean Expression

![Screen Shot 2022-10-12 at 20.13.37.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-13-40-Screen%20Shot%202022-10-12%20at%2020.13.37.png)

#### FSM

![Screen Shot 2022-10-12 at 20.13.48.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-13-50-Screen%20Shot%202022-10-12%20at%2020.13.48.png)

#### The Critical Path

the longest delay between any two registers in a circuit

![Screen Shot 2022-10-12 at 20.14.00.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-14-05-Screen%20Shot%202022-10-12%20at%2020.14.00.png)

#### Maximum Clock Frequncy

![Screen Shot 2022-10-12 at 20.14.13.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-14-15-Screen%20Shot%202022-10-12%20at%2020.14.13.png)

#### Timing Rules

![Screen Shot 2022-10-12 at 20.14.41.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-14-44-Screen%20Shot%202022-10-12%20at%2020.14.41.png)

Note that A and B are driven by registers

#### Datapath

![Screen Shot 2022-10-12 at 20.15.08.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-15-11-Screen%20Shot%202022-10-12%20at%2020.15.08.png)

#### Performance Analysis

Latency: time for one instruction to finish

Throughput: number of instructions processed per time unit

Pipeline: not decrease latency of single task but increase throughput of entire workload

### Pipeline Hazrds
- Structural Hazard
   ![Screen Shot 2022-10-12 at 20.15.33.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-15-36-Screen%20Shot%202022-10-12%20at%2020.15.33.png)

- Data Hazard-ALU/Load
   ![Screen Shot 2022-10-12 at 20.15.45.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-15-48-Screen%20Shot%202022-10-12%20at%2020.15.45.png)

- Control Hazard-Branching
   ![Screen Shot 2022-10-12 at 20.16.01.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-16-05-Screen%20Shot%202022-10-12%20at%2020.16.01.png)


#### cache

Locality

![Screen Shot 2022-10-13 at 10.34.53.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/13-10-34-56-Screen%20Shot%202022-10-13%20at%2010.34.53.png)

4 policies: weite hits and write allocate

![Screen Shot 2022-10-12 at 20.16.17.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-16-19-Screen%20Shot%202022-10-12%20at%2020.16.17.png)

Direct-Mapped Caches

![Screen Shot 2022-10-12 at 20.16.35.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-16-37-Screen%20Shot%202022-10-12%20at%2020.16.35.png)

Fully Associative Cache: one set, no index, lots of compares

N-Way Set Associative

![Screen Shot 2022-10-12 at 20.16.49.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-16-52-Screen%20Shot%202022-10-12%20at%2020.16.49.png)

#### Cache Misses

![Screen Shot 2022-10-12 at 20.17.12.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-17-15-Screen%20Shot%202022-10-12%20at%2020.17.12.png)

#### Multi-Level

![Screen Shot 2022-10-12 at 20.17.33.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-17-37-Screen%20Shot%202022-10-12%20at%2020.17.33.png)

#### Average Memory Access Time(AMAT)

![Screen Shot 2022-10-12 at 20.17.52.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-17-55-Screen%20Shot%202022-10-12%20at%2020.17.52.png)

#### VM

![Screen Shot 2022-10-12 at 20.18.22.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-18-26-Screen%20Shot%202022-10-12%20at%2020.18.22.png)

Paged Memory

![Screen Shot 2022-10-12 at 20.18.38.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-18-41-Screen%20Shot%202022-10-12%20at%2020.18.38.png)

Virtual Addr=VPN+Offset

Physical Addr=PPN+Offset

#### Accessing Pages

![Screen Shot 2022-10-12 at 20.18.51.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/10/12-20-18-53-Screen%20Shot%202022-10-12%20at%2020.18.51.png)

TLB: Translation Lookaside Buffer

- Cache for VM
- Fully associative
- TLB->PT

#### Data Race
