# Cpp

#### Trivial

```cpp
int INF = Integer.MAX_VALUE;
INT_MAX, INT_MIN.
g++ main.cpp -W -Wall // add W & Wall not to ignore warning
-g // debug版本 vs. release版本
-O2    // release开个优化
```

#### How it works

```cpp
#include <iostream>
// #: preprocessing character
// #include: copy header file.
std::cout << "Hello world!" << std::endl;
// <<: overloaded operator. actually can be seen as function, taking parameter from the right.
std::cin.get();
// expect enter.
```

preprocess: copy .h to .cpp (->.i) 

```cpp
#define INTEGER int
// change name  
#if 0  
//  {blocked}  
#endif  
```

compiler: all .cpp files to .obj one by one  
linker: link .obj files to be .exe, resolve 
symbols  
**entry point checked here, not have to be main**  
**static** keyword: will only used in this file when link. If in struct or class: shared for all instances.  
**extern** int var: declare that the var is outside this file.

#### BASIC KNOWLEDGE

```cpp
1. stdin & stdout;
In C++, you can read a single whitespace-separated token of input using cin, and print output to stdout using cout;
2. basic data types;
Int ("%d"): 32 Bit integer
Long ("%ld"): 64 bit integer
Char ("%c"): Character type
Float ("%f"): 32 bit real value
Double ("%lf"): 64 bit real value

To read a data type, use the following syntax:
scanf("`format_specifier`", &val);

char ch;
double d;
scanf("%c %lf", &ch, &d);

To print a data type, use the following syntax:
printf("`format_specifier`", val);

can use cin and cout but will be faster using scanf and printf especially for large numbers;

cout precison: cout << fixed << setprecision(6) << ans[i] << endl;
```

- auto
  
  The **`auto`** keyword is a simple way to declare a variable that has a complicated type. The **`auto`** keyword is a placeholder for a type, but it is not itself a type.

- inline
  
  节省调用开销，便于编译器和上下文配合做优化

- const
  
  修饰类成员函数，其目的是防止成员函数修改被调用对象的值，如果我们不想修改一个调用对象的值，所有的成员函数都应当声明为 const 成员函数。

#### 命名规范

1. 类名：MyClass

2. 变量一律小写，下划线连接，类中成员变量以下划线结尾：`string table_name, class TableInfo{ private: string table_name_ }`

3. const/constexpr. start with k. `const int kDaysInAWeek = 7;`

## Classes

- OOP: Object-Oriented Programming

- a class is a template for objects, and an object is an instance of a class.

- class members: variables and functions

```cpp
// crete a class
class MyClass {       // The class
  public:             // Access specifier
    int myNum;        // Attribute (int variable)
    void myMethod() {  // Method/function defined inside the class
      cout << "Hello World!";
    }
};
// create obj and access
int main() {
  MyClass myObj;  // Create an object of MyClass
  myObj.myNum = 15; // Access attribute and set value
  myObj.myMethod();  // Call the method
  return 0;
}

//outsie example, declare inside and define with scope resolution :: operator
class MyClass {        // The class
  public:              // Access specifier
    void myMethod();   // Method/function declaration
};
// Method/function definition outside the class
void MyClass::myMethod() {
  cout << "Hello World!";
}

// Constructors, a special method automatically called when an object iscreated.
// use the same name as class followed by parentheses ()
class MyClass {     // The class
  public:           // Access specifier
    int year;
    MyClass(int z) {     // Constructor
      year = z;
      cout << "Hello World!";
    }
};
int main() {
  MyClass myObj(1999);    // Create an object of MyClass (this will call the constructor)
  return 0;
}
```

- `public` - members are accessible from outside the class

- `private` - members cannot be accessed (or viewed) from outside the class

- `protected` - members cannot be accessed from outside the class, however, they can be accessed in inherited classes. 
  
  **Note:** By default, all members of a class are `private` if you don't specify an access specifier. Good practice to keep variables private, and make set & get methods.

```cpp
// static in .h
class Vector3 {
public:
    static double Dot(Vector3 x, Vector3 y);
}
// static in .cpp
double Vector3::Dot(Vector3 x, Vector3 y) {
    return x._x * y._x + x._y * y._y + x._z * y._z;
}
// use in .cpp
auto a = Vector3::Dot(x, y);

//operator in .h
Vector3 operator - (Vector3 &second) {
    Vector3 res;
    res.set(_x - second.x(), _y - second.y(), _z - second.z());
    return res;
}
```

- abstract class: pure virtual function in the calss. whose objects can never be created.
- static member: space for the static variable in class is allocated for the lifetime of the program, only one copy. can be accessed by all objects of that class.
- static function: can be accessed without object. call by class name and the scope resolution operator :: 

### Polymorphism

- Compile Time Polymorphism
  - Method Overloading
  - Operator Overloading
- Runtime Polymorphism
  - Virtual Function
  - Function Overloading

### Inheritance

group the "inheritance concept" into two categories:

- **derived class** (child) - the class that inherits from another class
- **base class** (parent) - the class being inherited from

To inherit from a class, use the `:` symbol.

```cpp
// Base class
class Vehicle {
  public:
    string brand = "Ford";
    void honk() {
      cout << "Tuut, tuut! \n" ;
    }
};

// Derived class
class Car: public Vehicle {
  public:
    string model = "Mustang";
};

int main() {
  Car myCar;
  myCar.honk();
  cout << myCar.brand + " " + myCar.model;
  return 0;
}

// Derived class
class MyChildClass: public MyClass, public MyOtherClass {
};
```

- virtual function (虚函数)

```cpp
class Parent  {      
public:  
    char data[20];  
    void Function1();     
    virtual void Function2();   // 这里声明Function2是虚函数  
}parent;  

void Parent::Function1()  {  
    printf("This is parent,function1\n");  
}  

void Parent::Function2()  {  
    printf("This is parent,function2\n");  
}  

class Child:public Parent  {  
    void Function1();  
    void Function2();  
} child;  

void Child::Function1()  {  
    printf("This is child,function1\n");  
}  

void Child::Function2()  {  
    printf("This is child,function2\n");  
}  

int main(int argc, char* argv[])  {  
    Parent *p;  // 定义一个基类指针  
    if(_getch()=='c')     // 如果输入一个小写字母c      
        p=&child;         // 指向继承类对象  
    else      
        p=&parent;       // 否则指向基类对象  
    p->Function1();   // 这里在编译时会直接给出Parent::Function1()的入口地址。      
    p->Function2();    // 注意这里，执行的是哪一个Function2？  
    return 0;  
}  
/*
c: parent function1, child function2
!c: parent function1, parent function2
*/
```

### iostream

In C++ input and output are performed in the form of a sequence of bytes or more commonly known as **streams**.

- **Input Stream:** If the direction of flow of bytes is from the device(for example, Keyboard) to the main memory then this process is called input.
- **Output Stream:** If the direction of flow of bytes is opposite, i.e. from main memory to device( display screen ) then this process is called output.

iostream stands for standard input-output stream. This header file contains definitions of objects like cin, cout, cerr, etc.

- **Standard output stream (cout)**: Usually the standard output device is the display screen. The C++ **cout** statement is the instance of the ostream class. The data needed to be displayed on the screen is inserted in the standard output stream (cout) using the insertion operator(**<<**).
- **standard input stream (cin)**: Usually the input device in a computer is the keyboard. C++ cin statement is the instance of the class **istream**.
  The extraction operator(**>>**) is used along with the object **cin** for reading inputs. The extraction operator extracts the data from the object **cin** which is entered using the keyboard.

```cpp
void write_color(std::ostream &out, Vector3 pixel_color) {
    out << static_cast<int>(255.999 * pixel_color.x()) << ' '
        << static_cast<int>(255.999 * pixel_color.y()) << ' '
        << static_cast<int>(255.999 * pixel_color.z()) << '\n';
}

write_color(std::cout, pixel_color);
```

### header file

Consider the following program:

```cpp
#include <iostream>
int main()
{
    std::cout << "Hello, world!";
    return 0;
}
```

This program prints to the console using *std::cout*. how does the compiler know what *std::cout* is? has been forward declared in the “iostream” header file. When we `#include <iostream>`, we’re requesting that the **preprocessor** copy all of the content (including forward declarations for std::cout) from the file named “iostream” into the file doing the #include.

#### Header guards

Duplicate definitions and a compile error.

Header guards are conditional compilation directives that take the following form:

```cpp
#ifndef SOME_UNIQUE_NAME_HERE
#define SOME_UNIQUE_NAME_HERE

// your declarations (and certain types of definitions) here

#endif

// Or just
#pragma once
```

For class: put declaration in .h and definition in .cpp (outside with `#include "MyClass.h"` and scope ::)

Notes: 不要在.h头文件中放定义，否则若其被两个或两个以上的.cpp文件包含的话会报错，因为声明可以很多次，但定义只能有一次！除非：

1. const对象默认没有extern的声明，只对当前引用的.cpp文件有效，同理static普通变量和普通函数（不包括static成员函数和成员变量

2. 可以写内联函数（inline）的定义，inline在编译器在遇到的时候根据定义内联展开，因此把inline定义放在头文件比较明智

3. 可以写class的定义，要求与inline基本一致。数据成员是要等到具体的对象被创建时才会被定义（分配空间），但函数成员是在一开始就被定义的。一般做法是把类的定义放在头文件中，把函数成员的实现放在cpp中。C++中类的实现：函数成员在类的定义体中被定义，会被编译器视为inline。注意：把函数成员写在头文件但没写在类定义中不合法，因为非inline了

#### Lambda 表达式

Lambda 表达式的基本语法如下：

```cpp
[capture list] (parameter list) mutable(optional) exception attribute -> return type {
    //function body
}
```

capture list can be understood as a type of parameter and can can serve to transfer external data. The internal function body of a lambda expression cannot use variables outside the body of the function by default. 

1. **Value capture**

the variable can be copied, except that the captured variable **is copied when the lambda expression is created**, not when it is called:

```cpp
void lambda_value_capture() {  
 int value = 1;  
 auto copy_value = [value] {  
     return value;  
 };  
 value = 100;  
 auto stored_value = copy_value();  
 std::cout << "stored_value = " << stored_value << std::endl;  
 // At this moment, stored_value == 1, and value == 100.  
 // Because copy_value has copied when it was created.  
}
```

2. **Reference capture**

Similar to a reference pass, the reference capture saves the reference and the value will change.

```cpp
void lambda_reference_capture() {  
 int value = 1;  
 auto copy_value = [&value] {  
 return value;  
 };  
 value = 100;  
 auto stored_value = copy_value();  
 std::cout << "stored_value = " << stored_value << std::endl;  
 // At this moment, stored_value == 100, value == 100.  
 // Because copy_value stores reference  
}
```

3. **Implicit capture**

Manually writing a capture list is sometimes very complicated. This mechanical work can be handled by the compiler. At this point, you can write a `&` (ampersand) or `=` to the compiler to declare the reference or value capture.

The four most common forms of capture lists can be:

- [] empty capture list
- [name1, name2, ...] captures a series of variables
- [&] reference capture, let the compiler deduce the reference list by itself
- [=] value capture, let the compiler deduce the value list by itself
4. **Expression capture**

```cpp
#include <iostream>  
#include <memory> // std::make_unique  
#include <utility> // std::move

void lambda_expression_capture() {  
 auto important = std::make_unique<int>(1);  
 auto add = [v1 = 1, v2 = std::move(important)](int x, int y) -> int {  
     return x+y+v1+(*v2);  
 };  
 std::cout << add(3,4) << std::endl;  
}
```

前几个都是捕获左值，通过允许捕获的成员用任意的表达式进行初始化，就允许了右值的捕获。

In the above code, `important` is an exclusive pointer that cannot be caught by value capture using `=`. At this time we need to transfer it to the rvalue and initialize it in the expression.

#### 二分

```c++
// 本质： 两段性质的划分（两个边界点）
** 如果用到left = mid， 则mid需要加一！！
```

#### 排序

```C++
// 1. 冒泡排序
// 2. 快速排序——分治, 确定pivot是O(n), T(n)=2*T(n/2)+O(n), O(nlogn), 要求左右比较均匀; 最坏O(n^2)

// 3. 归并排序
```

#### operator 运算符

```c++
a=++i；    //i=i+1; a=i;
b=j++;    //b=j; j=j+1;
a[index--]='0';    //1. 赋0 2. index--

//magic code
static const auto __=[](){
  std::ios::sync_with_stdio(false);
  std::cin.tie(nullptr);
  return nullptr;
}();
```

#### class

```c++
class MyLinkedList {
public:
    // 定义链表节点结构体
    struct LinkedNode {
        int val;
        LinkedNode* next;
        LinkedNode(int val):val(val), next(nullptr){}
    };

    // 初始化链表
    MyLinkedList() {
        _dummyHead = new LinkedNode(0); // 这里定义的头结点 是一个虚拟头结点，而不是真正的链表头结点
        _size = 0;
    }
    // 在链表最前面插入一个节点，插入完成后，新插入的节点为链表的新的头结点
    void addAtHead(int val) {
        LinkedNode* newNode = new LinkedNode(val);
        newNode->next = _dummyHead->next;
        _dummyHead->next = newNode;
        _size++;
    }
private:
    int _size;
    LinkedNode* _dummyHead;
};

// 带值初始化
NumArray(vector<int>& nums){}
NumArray* obj=new NumArray(nums);
obj->update(index, val);
```

## 智能指针与内存管理

引用计数：增加一次对同一个对象的引用，引用对象的引用计数+1， 每删除一次引用，引用计数-1，引用计数减为零时，就自动删除指向的堆内存。

C++11 引入了智能指针的概念，使用了引用计数的想法，不再需要关心手动释放内存。 这些智能指针就包括 `std::shared_ptr`/`std::unique_ptr`/`std::weak_ptr`，使用它们需要包含头文件 `<memory>`。

### shared_ptr

`std::shared_ptr` 是一种智能指针，它能够记录多少个 `shared_ptr` 共同指向一个对象，从而消除显式的调用 `delete`，当引用计数变为零的时候就会将对象自动删除。

但还不够，因为使用 `std::shared_ptr` 仍然需要使用 `new` 来调用，这使得代码出现了某种程度上的不对称。

`std::make_shared` 就能够用来消除显式的使用 `new`，所以`std::make_shared` 会分配创建传入参数中的对象， 并返回这个对象类型的`std::shared_ptr`指针。

```cpp
#include <iostream>
#include <memory>
void foo(std::shared_ptr<int> i) {
    (*i)++;
}
int main() {
    // Constructed a std::shared_ptr
    auto pointer = std::make_shared<int>(10);
    foo(pointer);
    std::cout << *pointer << std::endl; // 11
    // The shared_ptr will be destructed before leaving the scope
    return 0;
}
```

`std::shared_ptr` 可以通过 `get()` 方法来获取原始指针，通过 `reset()` 来减少一个引用计数， 并通过`use_count()`来查看一个对象的引用计数。例如：

```cpp
auto pointer = std::make_shared<int>(10);
auto pointer2 = pointer; // 引用计数+1
auto pointer3 = pointer; // 引用计数+1
int *p = pointer.get(); // 这样不会增加引用计数
std::cout << "pointer.use_count() = " << pointer.use_count() << std::endl; // 3
std::cout << "pointer2.use_count() = " << pointer2.use_count() << std::endl; // 3
std::cout << "pointer3.use_count() = " << pointer3.use_count() << std::endl; // 3

pointer2.reset();
std::cout << "reset pointer2:" << std::endl;
std::cout << "pointer.use_count() = " << pointer.use_count() << std::endl; // 2
std::cout << "pointer2.use_count() = " << pointer2.use_count() << std::endl; // 0, pointer2 已 reset
std::cout << "pointer3.use_count() = " << pointer3.use_count() << std::endl; // 2
pointer3.reset();
std::cout << "reset pointer3:" << std::endl;
std::cout << "pointer.use_count() = " << pointer.use_count() << std::endl; // 1
std::cout << "pointer2.use_count() = " << pointer2.use_count() << std::endl; // 0
std::cout << "pointer3.use_count() = " << pointer3.use_count() << std::endl; // 0, pointer3 已 reset
```

### queue

```cpp
queue<TreeNode*> que;
while (!que.empty())
int num = que.size();
q.push(i);
int u=q.front();
q.pop();

//priority_queue 优先队列 703. topK
class KthLargest {
public:
    priority_queue<int, vector<int>, greater<int>> pq;
    int k;
    KthLargest(int k, vector<int>& nums) {
        this->k = k;
        for (auto& x: nums) {
            add(x);
        }
    }
    int add(int val) {
        q.push(val);
        if (q.size() > k) {
            q.pop();
        }
        return q.top();
    }
};
```

#### regex

Consider a regular expression that matches an MS-DOS filename as shown below.

```cpp
char regex_filename[] = 
“[a-zA-Z_] [a-zA-Z_0-9]*\\.[a-zA-Z0-9]+”;
```

**The above regex can be interpreted as follows:**

Match a letter (lowercase and then uppercase) or an underscore. Then match zero or more characters, in which each may be a letter, or an underscore or a digit. Then match a literal dot (.). After the dot, match one or more characters, in which each may be a letter or digit indicating file extension.

### STL  
container + iterator + algorithm + functor (仿函数) + allocator  

#### vector
sizeof(vector) = 24 = 3 ptrs  
memory on heap -> end addr -> very original size. = vec.capacity()
- copy: void TryChange(vector<int> a, vector<int> &b);
- RAII (Resource acquistion is initialization) 避免内存泄露，离开作用域自动调用析构函数
- 扩容(*2)的时候内存地址变了，注意之前的指针引用
```cpp
int *p = a.data();  // get first address = &a[0]
vec.push_back(i);    //在表尾添加元素
// O(1)操作，但触发扩容就是O(N)
vec.pop_back();    //在表尾删除元素, return void
vec.erase(vec.begin() + 1); //index = 1
vector<bool> vec(x, false);    //初始化x个元素的bool向量
vector<int> vec={x1,x2,x3};    //初始化vector数组
vec.resize(2);  // resize vec = {x1, x2}
vec.resize(3);  // resize vec = {x1, x2, 0}
vec.resize(4, 1); // resize vec = {x1, x2, 0, 1}
vec.clear();  // size = 0, capacity not changed.
vector<vector<int>> ans(r, vector<int>(c)); //初始化r*c二维数组
sums.resize(m + 1, vector<int>(n + 1));        //resize二维数组
fill(visited.begin(), visited.end(), false); //重新赋值
res.push_back(vector<int>(i+1,1));    //也可以直接用
ret.insert(ret.end(),temp.begin(),temp.end());    //数组后面插入数组
sort(nums.begin(), nums.end());    //排序
int x = nums.back(); //最后一个

// 迭代器插入, begin()是0号元素, begin()+2, 插在第3位
vector<int> ivec;
auto it=ivec.begin()+2;
ivec.insert(it, 100); // insert 插在迭代器前一位

bool comp(const int &a, const int &b){return a>b;}
sort(v.begin(), v.end(), comp);        //条件排序
sort(v.begin(), v.end(), [](vector<int> a, vector<int> b){
  return a[1]>b[1];
});    //lambda表达式

for (int e:nums) sum+=e;    //一个快速的求和

//另一种访问方式, 区别是越界会抛出异常
int x = ivec.at(0);

// iota, fill will ascending.
iota(index.begin(), index.end(), 0);
sort(index.begin(), index.end(), [&](int x, int y){
    return g[x] > g[y];
});

vector<char> v(s.begin(), s.end());    //vector to set

// lower_bound & upper_bound
std::vector <int> v = {10, 10, 10, 20, 20, 20, 20, 30, 30};
std::vector<int>::iterator low,up;
low=std::lower_bound (v.begin(), v.end(), 20);
up= std::upper_bound (v.begin(), v.end(), 20);

std::cout << "lower_bound at position " << (low- v.begin()) << '\n';// 3
std::cout << "upper_bound at position " << (up - v.begin()) << '\n';// 7

// min index
int minPosition = min_element(v.begin(),v.end()) - v.begin();

a.reserve(size);  //预先扩容
a.shrink_to_fit(); // 释放多余容量重新分配到其他内存
```

- `emplace_back()`和`push_back()`的区别

push_back() 在底层实现时，会优先选择调用移动构造函数，如果没有才会调用拷贝构造函数。emplace_back() 的执行效率比 push_back() 高。

#### 单链表

用e[N]和ne[N]开数组来模拟，head表示头节点的下标，idx存储当前已经用到哪个节点。用数组模拟静态链表会比new快很多。

#### string

```cpp
string str=bitset<32>(n).to_string();    //把n转换成32位字符串
int x=stoi(s);    //string_to_integer
string s = to_string(int/long/...);

if (n[0]=='0') {n=n.substr(1);}    //去掉先导0
n.substr(1,5);    //从1开始截取5位
n.insert(0,1,'1');    //在第0位插入一个'1'
reverse(s.begin(), s.end());            //反转字符串

for (char ch : s){}    //遍历

//string 的stack用法
string stk;
stk.empty();
(char)stk.back();    // end char
stk.pop_back();
stk.push_back(ch);

// 删去末尾空格
while (res.size() and res.back() == ' '){
    res.pop_back();
}

//delimeter example
while ((pos = s.find(delimiter)) != std::string::npos) {
    token = s.substr(0, pos);
    std::cout << token << std::endl;
    s.erase(0, pos + delimiter.length());
}
```

#### stack

```cpp
stack<char> stk;
stk.size();
stk.top();
stk.pop();
stk.push();
stk.empty();
```

#### 单调栈

问题类型：下一个更大元素. 从右往左遍历.

![Screen Shot 2022-01-05 at 23.41.37.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/01/05-23-41-39-Screen%20Shot%202022-01-05%20at%2023.41.37.png)

#### Tree

```cpp
//层次遍历分层思路：外循环层次+内循环节点
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(NULL), right(NULL) {}
};

// height-balanced tree: a binary tree in which the left and right subtrees of every node differ in height by no more than 1.
```

基环树：树加一条边成环，本质是个图

基环内向树：有向图，每个点都有且只有一个出度，且环外节点方向指向环内。

<img title="" src="https://raw.githubusercontent.com/yxshi610/images/main/2022/01/02-20-44-14-Screen%20Shot%202022-01-02%20at%2020.44.12.png" alt="Screen Shot 2022-01-02 at 20.44.12.png" width="238" data-align="inline">

基环外向树：同上但环上节点指向环外。

#### unordered associative container

sometimes need to provide own hasher to work. especially when key is vector. use map directly.

#### unordered_set

```cpp
//哈希集合
unordered_set<char> ooc;
occ.erase(s[i]);
occ.insert(s[i]);
occ.find('a');    //查找元素，返回对应元素或/occ.end()
occ.count('a');    //查找元素个数（0/1）
//存路径常用
vector<unordered_set<int>> g(n);    //n是点数
g[u].insert(v);
if (g[i].count(j)){}    //有直接相连的边
```

#### map & unordered_map

```cpp
// map: 内部实现红黑树，自动排序(by key)，空间占用率高, map中存的是pair: first, second(key->value)
1. mp.size();
2. mp.insert(pair);
3. mp.find(key);   m.count(key); ?==1;
4. mp.erase(key);
5**. mp[key] = value;
for (auto it = mp.begin(); it != mp.end(); it++) {
  cout << it->first << " " << it->second<<endl;
}

map.rbegin();  // reverse begin in C++ STL, throws a reverse iterator

//哈希表：key->value, O(1), 5 ops as above
unordered_map<string,int>mem;
mem.size();        //key的数量
if (mem.find(n)!=mem.end){return mem[n]}    //已经计算过
// important!!
if (hash.count(t)){}    //不加可能会超时
//一个思路：边找边加入而非全部加入再找
hash.clear();

//key->set 实现存储多个变量
unordered_map<int, vector<int>> mp;
//遍历哈希表
for (auto& [_, vec] : mp){}
for (auto it : freq) {
    if (it.second == k) res.emplace_back(it.first);
}
```

#### Topological Sort (拓扑排序)

有向图的拓扑排序是其顶点的线性排序，使得对于从顶点u到顶点v的每个有向边uv，u在排序中都在v之前
有向无环图（DAG）=》拓扑排序
eg. 是否能排课

1. BFS
   用数组记录先修课程，入度为0加入队列，时空O(m+n)

#### cmath

```C++
//下面都是弧度要*180/M_PI
double atan2(double y, double x);    //涉及角度相关，值域为[-PI,PI]
double atan(double x);
```

#### Gray Code (格雷码)

在一组数的编码中，若任意两个相邻的代码只有一位二进制数不同，则称这种编码为格雷码(Gray Code). 另外,格雷码的最大数与最小数之间也仅一位数不同，即“首尾相连”，因此又称循环码或反射码.

#### 并发问题

```c++
//信号量
# include <semaphore.h>
sem_t x;
sem_init(&x, 0, 0);
sem_post(&x);
sem_wait(&x);
```

#### 动态规划(Dynamic Programming)

```c++
/*
e.g. 玩家拿数
dp[i][j] 表示nums的[i,j]子序列时，先手最多分数
最终答案: dp[0][n-1]*2>=SUM
状态转移方程：
dp[i][j]=max(
nums[i]+sum(i+1,j)-dp[i+1][j]
nums[j]+sum(i,j-1)-dp[i][j-1]
)
*/
// 动规要谨记：循环顺序！
1. 确定状态：（最优策略的）最后一步->子问题
2. 转移方程
3. 初始条件和边界情况
4. 计算顺序

dp的状态函数中间，一个重要的下标是target
dp的第二个下标一般是状态，分情况讨论转移

  1. 背包问题: 2 variables = weight and values, so to get max(dp[N][0-V])
```

#### 并查集：三个操作

```c++
// 初始化
int *p=new int[n];
for (int i=0; i<n; i++){
  p[i]=i;
}
// find
int getf(vector<int>& f, int x) {
    if (f[x] == x) {return x;}
    int newf = getf(f, f[x]);
  f[x] = newf;
  return newf;
}
// union
void add(vector<int>& f, int x, int y) {
  int fx = getf(f, x);
  int fy = getf(f, y);
  f[fx] = fy;
}
// eg. 连通分量: how many p[x]==x;
```

#### 堆

```c++
// 从vector生成最大堆
make_heap(piles.begin(), piles.end());
for (int i = 0; i < k; ++i){
    // 单次操作：记录并弹出最大值，修改后重新添加进堆
    pop_heap(piles.begin(), piles.end());
    piles.back() -= piles.back() / 2;
    push_heap(piles.begin(), piles.end());
}
return accumulate(piles.begin(), piles.end(), 0);
时间复杂度：O(n+klogn)，其中 n 为 piles 的长度。建堆与计算结果的复杂度为 O(n)；每次弹出最大值与添加新值的时间复杂度为 O(logn)，共需进行 k 次。
```

#### 位运算

```c++
A[i]^=1;    //异或（翻转）
int u = (bs[bucket] | (1 << loc));    //或者，移位
```

#### 线段树

```C++
// 对数时间从数组中找到max、min、sum、最大公约数、最小公倍数
```

#### 多线程多进程

```c
// 进程：分配系统资源的实体，struct task_struct结构体描述，即进程控制块PCB——标识符，状态，优先级，程序计数器（PC，下条指令地址），内存指针，上下文数据（Reg），I/O状态信息，记账信息，其他
// linux创建子进程：子进程拷贝父进程PCB以及页表等结构，创建完成后具有自己的进程虚地址空间和页表结构，返回0子进程，>0父进程
#include <unistd.h>
pid_t fork(void);
// 线程：轻量级进程
#include <pthread.h>
int pthread_create(pthread_t *thread, const pthread_attr_t *attr, void* (*start_routine)(void *), void *arg);
```

## C

```c
// typedef is a language construct that associates a name to a type
typedef int myinteger;
typedef char *mystring;
// a function pointer stores the address of a function
typedef void (*myfunc)();
myinteger i;   // is equivalent to    int i;
mystring s;    // is the same as      char *s;
myfunc f;      // compile equally as  void (*f)();
```

## CMake
GNU Make: write dependencies, Makefile
- re-compile only changed files
- make -j, compile in parallel
- 通配符批量生成构建规则  

CMake:
- CMakeLists.txt: multi-platform
- auto-dependencies
- ...(总之就是比较智能？) 

1. 读取CMakeLists.txt，并在build下生成build/Makefile  
   ```cmake -B build```
2. make 读取build/Makefile，开始构建a.out  
   ```make -C build``` 或者更跨平台 ```cmake --build build```
3. 执行  
   ```build/a.out```

CMake 中的静态库和动态库  
```
// 静态库 (libtest.a文件，直接把实现搬到a.out)
add_library(test STATIC src1.cpp src2.cpp)
// 动态库 (libtest.so文件，运行时查找)
add_library(test SHARED src1.cpp src2.cpp)

cmake_minimum_required(VERSION 3.12)
project(hellocmake LANGUAGES CXX)
add_library(hellolib STATIC hello.cpp)
// 生成可执行文件
add_executable(a.out main.cpp)
// 为myexec链接库文件
target_link_libraries(a.out PUBLIC hellolib)
```

```
"hello.h" 搜索当前文件夹  
<cstdio>  优先搜索/usr/include/
#pragma once 加在h头文件前面
```