# C++ 后端技术知识库

> 参考面试鸭（mianshiya.com）题库组织模型：标签层级 + 多维度分类 + 高频优先。
> 每个分类下列出面试最常问的问题及答案要点，标 ⭐ 为高频考点，面试官可按候选人背景灵活选题。

---

## 高频考点速查

| 优先级 | 模块 | 实习 | 应届 | 社招 | 高频题代表 |
|--------|------|:----:|:----:|:----:|-----------|
| ⭐⭐⭐ | C++ 基础 | 必考 | 必考 | 必考 | 虚函数实现、智能指针、移动语义 |
| ⭐⭐⭐ | STL | 必考 | 必考 | 必考 | vector扩容、map vs unordered_map |
| ⭐⭐⭐ | 数据结构与算法 | 必考 | 必考 | 常考 | 链表反转、二叉树遍历、排序 |
| ⭐⭐ | 操作系统 | 必考 | 必考 | 常考 | 进程线程、虚拟内存、epoll |
| ⭐⭐ | 计算机网络 | 必考 | 必考 | 常考 | TCP三次握手、四次挥手、IO模型 |
| ⭐⭐ | C++ 并发编程 | 了解 | 常考 | 必考 | mutex、atomic、线程池 |
| ⭐⭐ | MySQL | 了解 | 常考 | 必考 | 索引B+树、MVCC、SQL优化 |
| ⭐⭐ | Redis | 了解 | 常考 | 必考 | 缓存穿透/击穿/雪崩、分布式锁 |
| ⭐ | 编译与调试 | — | 了解 | 常考 | GDB、perf、编译链接过程 |
| ⭐ | 系统设计 | — | 了解 | 必考 | 秒杀系统、短链、高性能日志 |
| ⭐ | C++ 新特性 | 了解 | 常考 | 常考 | C++11/14/17/20 关键特性 |
| ⭐ | 分布式系统 | — | 了解 | 必考 | CAP、一致性、消息队列 |

---

## 目录

- [1. C++ 语言基础](#1-c-语言基础)
  - [1.1 面向对象](#11-面向对象)
  - [1.2 内存管理](#12-内存管理)
  - [1.3 模板与泛型](#13-模板与泛型)
  - [1.4 const 与类型系统](#14-const-与类型系统)
  - [1.5 关键字与语法深度](#15-关键字与语法深度)
- [2. C++ 新特性（C++11/14/17/20）](#2-c-新特性c11141720)
  - [2.1 C++11 核心特性](#21-c11-核心特性)
  - [2.2 C++14 增强](#22-c14-增强)
  - [2.3 C++17 核心特性](#23-c17-核心特性)
  - [2.4 C++20 关键特性](#24-c20-关键特性)
- [3. STL 标准库](#3-stl-标准库)
  - [3.1 序列容器](#31-序列容器)
  - [3.2 关联容器](#32-关联容器)
  - [3.3 容器适配器](#33-容器适配器)
  - [3.4 迭代器与算法](#34-迭代器与算法)
  - [3.5 空间配置器](#35-空间配置器)
  - [3.6 智能指针](#36-智能指针)
- [4. 数据结构与算法](#4-数据结构与算法)
  - [4.1 线性结构](#41-线性结构)
  - [4.2 树结构](#42-树结构)
  - [4.3 哈希表](#43-哈希表)
  - [4.4 排序算法](#44-排序算法)
  - [4.5 查找算法](#45-查找算法)
  - [4.6 动态规划](#46-动态规划)
  - [4.7 海量数据处理](#47-海量数据处理)
- [5. 并发编程](#5-并发编程)
  - [5.1 线程基础](#51-线程基础)
  - [5.2 互斥与同步](#52-互斥与同步)
  - [5.3 原子操作与内存序](#53-原子操作与内存序)
  - [5.4 线程池与异步](#54-线程池与异步)
  - [5.5 无锁编程](#55-无锁编程)
  - [5.6 死锁与排查](#56-死锁与排查)
- [6. 操作系统](#6-操作系统)
  - [6.1 进程与线程](#61-进程与线程)
  - [6.2 内存管理](#62-内存管理)
  - [6.3 文件系统与IO](#63-文件系统与io)
  - [6.4 IPC](#64-ipc)
  - [6.5 信号与异常](#65-信号与异常)
- [7. 计算机网络](#7-计算机网络)
  - [7.1 TCP/IP 协议栈](#71-tcpip-协议栈)
  - [7.2 HTTP/HTTPS](#72-httphttps)
  - [7.3 IO 模型与高性能服务](#73-io-模型与高性能服务)
  - [7.4 序列化协议](#74-序列化协议)
- [8. 编译链接与调试](#8-编译链接与调试)
  - [8.1 编译链接过程](#81-编译链接过程)
  - [8.2 GDB 调试](#82-gdb-调试)
  - [8.3 性能分析工具](#83-性能分析工具)
  - [8.4 构建系统](#84-构建系统)
- [9. MySQL](#9-mysql)
  - [9.1 索引](#91-索引)
  - [9.2 事务与锁](#92-事务与锁)
  - [9.3 SQL 优化](#93-sql-优化)
  - [9.4 C++ 数据库连接](#94-c-数据库连接)
- [10. Redis](#10-redis)
  - [10.1 数据结构与原理](#101-数据结构与原理)
  - [10.2 缓存问题](#102-缓存问题)
  - [10.3 分布式与持久化](#103-分布式与持久化)
  - [10.4 C++ Redis 客户端](#104-c-redis-客户端)
- [11. 分布式系统](#11-分布式系统)
  - [11.1 分布式基础理论](#111-分布式基础理论)
  - [11.2 消息队列](#112-消息队列)
  - [11.3 分布式一致性](#113-分布式一致性)
- [12. 系统设计与场景题](#12-系统设计与场景题)
  - [12.1 设计方法论](#121-设计方法论)
  - [12.2 经典系统设计题](#122-经典系统设计题)
  - [12.3 线上排查场景](#123-线上排查场景)
- [13. 性能优化](#13-性能优化)
  - [13.1 CPU 优化](#131-cpu-优化)
  - [13.2 内存优化](#132-内存优化)
  - [13.3 系统级优化](#133-系统级优化)

---

## 1. C++ 语言基础

### 1.1 面向对象

**C++ 的多态是如何实现的？** ⭐⭐⭐

虚函数表（vtable）机制：每个含虚函数的类有 vtable（存放在只读数据段），对象头部存 vptr 指向 vtable。调用虚函数通过 vptr→vtable 间接跳转，多一次间接寻址。单继承一个 vtable，多继承多个 vtable，虚继承额外存储 vbase offset。

追问链：
1. vtable 里存了什么？（函数指针数组，以及 type_info、虚基类偏移）
2. 构造函数中调用虚函数会发生什么？（调用当前类的版本，派生类尚未构造）
3. devirtualization 是什么优化？（编译器可证明具体类型时消除间接调用，final 类/编译期可见类型触发）

**虚析构函数为什么必要？** ⭐⭐⭐

基类指针 delete 派生类对象时，若非虚析构只调基类析构，派生类资源泄漏。追问：哪些情况不需要虚析构？（非多态基类，如 std::string 继承的 char_traits）

**重载(Overload)、重写(Override)、隐藏(Hide)的区别？** ⭐⭐

- 重载：同一作用域，函数名同参数不同
- 重写：派生类覆盖基类虚函数，签名相同，必须 virtual
- 隐藏：派生类定义同名函数（非虚/不同参数），基类函数被隐藏

追问：如何让隐藏的函数仍可调用？（using Base::func）

**final 和 override 的作用？** ⭐⭐

override 编译期检查是否真正覆盖基类虚函数（防止签名写错）；final 禁止派生类覆盖或禁止类被继承。无运行时开销。追问：什么时候用 final 修饰类？（不需要被继承的工具类、安全考虑防止篡改行为）

**静态成员变量和静态成员函数的特点？** ⭐

静态成员变量：类内声明类外定义（C++17 inline static 可类内初始化），所有对象共享。静态成员函数：无 this 指针，不能访问非静态成员，不能是虚函数。追问：C++17 inline static 解决了什么痛点？（无需在 .cpp 中再定义）

**C++ struct 和 class 的区别？** ⭐

唯一区别：默认访问权限（struct public，class private）和默认继承权限（struct public，class private）。追问：什么时候选 struct？（主要是数据聚合，如 POD、trivially copyable 类型）

---

### 1.2 内存管理

**RAII 是什么？为什么重要？** ⭐⭐⭐

Resource Acquisition Is Initialization — 资源生命周期绑定到对象生命周期：构造获取，析构释放。保证异常安全、防止资源泄漏。C++ 核心惯用法：智能指针、lock_guard、文件句柄。追问：RAII 替代方案？（GC 语言用 try-finally/defer，但有忘记的风险）

**new/delete 和 malloc/free 的核心区别？** ⭐⭐⭐

| 对比维度 | new/delete | malloc/free |
|---------|-----------|-------------|
| 类型安全 | 返回正确类型指针 | 返回 void*，需强转 |
| 构造/析构 | 调用 | 不调用 |
| 大小计算 | 编译器自动 | 手动 sizeof |
| 可重载 | operator new 可重载 | 不可重载 |
| 失败返回 | 抛 std::bad_alloc | 返回 NULL |
| 与 realloc | 无等价物 | realloc 可原地扩容 |

追问：delete 一个 void* 指针会怎样？（不会调析构函数，资源泄漏，未定义行为）

**new 的三种形式？** ⭐⭐

operator new（只分配内存，可重载）、new operator（分配+构造，即常规 new 表达式）、placement new（在已有内存构造对象）。追问：如何用 placement new + operator delete 实现内存池？（预分配大块，placement new 构造，显式析构，归还到空闲链表）

**C++ 内存对齐原理？** ⭐⭐

alignof 查对齐要求，alignas 指定对齐。对齐原因：CPU 访存效率（不对齐可能跨 cache line 两次访问）、某些指令要求（SSE 16 字节、AVX 32 字节）。追问：struct 内存布局怎么算？（成员按声明顺序排列，每个成员 offset 是自身对齐值的倍数，整体大小是最大对齐值的倍数）

**内存泄漏如何排查？** ⭐⭐

工具链：Valgrind Memcheck（动态翻译，慢但无需重编译）、AddressSanitizer（编译插桩，2x 延迟开销）、tcmalloc/jemalloc heap profiler、自定义 operator new/delete 追踪。追问：ASan 能检测哪些错误？（heap/memory/stack buffer overflow、use-after-free、double-free、memory leak）

**拷贝控制：三/五/零法则？** ⭐⭐

三法则：若需要自定义析构/拷贝构造/拷贝赋值之一，通常三者都需要。五法则（C++11+）：加移动构造和移动赋值。零法则：尽量让编译器生成，用 RAII 类型管理资源。追问：=default 和 =delete 的使用场景？

---

### 1.3 模板与泛型

**模板实例化过程是怎样的？** ⭐⭐⭐

编译期生成，分显式实例化和隐式实例化：隐式实例化发生在第一次使用时（ODR 规则每个翻译单元生成一份，链接器去重）；显式实例化 `template class Foo<int>` 控制生成位置。代码膨胀是代价。追问：extern template 的作用？（阻止隐式实例化，减少编译时间）

**模板特化与偏特化的区别？** ⭐⭐

全特化：所有模板参数指定具体类型。偏特化：仅部分参数或参数的模式特化（如 `T*`、`vector<T>`）。函数模板不支持偏特化，但可用重载替代。追问：偏特化与重载的选择顺序？（重载优先于特化，更具体的特化优先）

**SFINAE 是什么？C++20 有什么替代？** ⭐⭐

Substitution Failure Is Not An Error — 模板参数替换失败不报错，从候选集移除。用于编译期条件判断（enable_if、void_t）。C++20 Concepts 替代：语法更清晰、错误信息更可读。追问：enable_if 的实现原理？（偏特化 + SFINAE）

**变参模板如何展开？** ⭐⭐

C++11 递归展开（重载空参数终止），C++17 折叠表达式 `(args + ...)` 简洁展开。追问：`sizeof...(Args)` 的用途？（编译期获取参数包大小）

**typename 和 class 在模板中的区别？** ⭐

声明模板参数时完全等价。但在依赖类型前必须用 typename（如 `typename T::value_type`），class 不可。追问：template template parameter 怎么写？（`template<template<typename> class Container>`）

---

### 1.4 const 与类型系统

**const 正确性的含义？** ⭐⭐⭐

const 成员函数承诺不修改成员（本质是 `const T* this`）。const 对象只能调用 const 成员函数。mutable 成员可在 const 函数中修改（常见场景：互斥锁、缓存、引用计数）。追问：const 成员函数中改一个非 const 成员合法吗？（不合法，const this 保证所有成员是顶层 const）

**顶层 const 和底层 const 的区别？** ⭐⭐

顶层 const：指针本身是常量 `int* const p`。底层 const：所指对象是常量 `const int* p`。引用没有顶层 const（引用不可重绑定）。追问：auto 推导如何处理 const？（auto 剥除顶层 const 和引用，auto& 保留底层 const）

**static_cast/dynamic_cast/const_cast/reinterpret_cast 的区别和使用场景？** ⭐⭐⭐

- static_cast：编译期类型转换（相关类型间，如 int/long、向上转型），不检查运行时类型
- dynamic_cast：运行期类型转换（向下转型），必须用于多态类型，失败返回 nullptr 或抛 std::bad_cast
- const_cast：添加或去除 const/volatile。去除 const 修改原 const 对象是 UB
- reinterpret_cast：无关类型间重新解释位模式，最危险

追问：dynamic_cast 内部如何实现？（遍历继承树，比较 type_info，开销较大）

**类型萃取(type_traits)的用途？** ⭐⭐

编译期获取类型信息：`is_integral`、`is_same`、`is_trivially_copyable`、`enable_if` 等。用于条件编译、SFINAE、优化选择。追问：`is_trivially_copyable` 对优化有什么意义？（可用 memcpy 代替逐元素拷贝）

---

### 1.5 关键字与语法深度

**static 关键字的四种含义？** ⭐⭐

1. 静态局部变量：第一次调用初始化，生命周期到程序结束（C++11 起线程安全）
2. 静态成员变量：类属，所有对象共享
3. 静态成员函数：无 this 指针，不能 virtual
4. 静态全局变量/函数：内部链接，仅当前翻译单元可见

**extern "C" 的作用？** ⭐⭐

告知编译器按 C 语言规则处理函数名（禁止 name mangling），使 C++ 代码可调 C 库，C 代码可调 C++ 库。常用于 JNI、跨语言 FFI。追问：能重载 extern "C" 的函数吗？（不能，C 不支持重载）

**inline 关键字的现代含义？** ⭐

C++17 前：建议编译器内联 + 允许函数在多个翻译单元定义而不违反 ODR。C++17 后：inline 变量允许头文件中定义变量。追问：编译器一定 inline 吗？（不一定，编译器自行决定，递归/虚函数/过大函数不会内联）

---

## 2. C++ 新特性（C++11/14/17/20）

### 2.1 C++11 核心特性

**左值、右值、将亡值是什么？** ⭐⭐⭐

- 左值(lvalue)：有标识、可取地址、不可移动的表达式
- 纯右值(prvalue)：临时对象、字面量、不关联对象的表达式
- 将亡值(xvalue)：std::move 转换左值或返回右值引用函数的结果
- 泛左值(glvalue) = 左值 + 将亡值；右值(rvalue) = 纯右值 + 将亡值

追问：为什么要分左值和右值？（优化：右值可安全转移资源，触发移动语义）

**移动语义解决了什么问题？** ⭐⭐⭐

避免不必要的深拷贝。移动构造/赋值参数是非 const 右值引用，将源对象资源"窃取"后置为"有效但未指定"状态。追问：移动后源对象析构安全吗？（安全，源对象必须处于可安全析构的状态）

**std::move 到底做了什么？** ⭐⭐⭐

本质就是 `static_cast<T&&>`，不移动任何数据。真正的移动由移动构造/赋值函数完成。追问：如果目标类型没有移动构造，调用 std::move 后会发生什么？（退化为拷贝构造）

**完美转发的原理？** ⭐⭐

std::forward 保持参数的值类别：当 T 是左值引用时转发为左值，当 T 是右值引用时转发为右值。依赖引用折叠规则（两个 && 折叠成 &&）。追问：为什么不用 std::move 做转发？（std::move 无条件转右值，会丢失左值性）

**lambda 表达式的底层实现？** ⭐⭐

编译器生成匿名函数对象类，重载 operator()。捕获列表是成员变量：值捕获 = 成员值拷贝；引用捕获 = 成员引用。无捕获的 lambda 可转为函数指针。追问：mutable lambda 和普通 lambda 的区别？（mutable 允许修改值捕获的成员）

**auto 类型推导规则？** ⭐⭐

行为与模板参数推导一致。auto 剥除顶层 const 和引用（与模板参数行为相同），auto& 不剥除，auto&& 是转发引用（可绑左值或右值）。追问：`auto x = {1,2,3}` 的类型？（initializer_list<int>，这是 auto 与模板推导的唯一区别）

---

### 2.2 C++14 增强

**C++14 对 C++11 的关键增强？** ⭐

- lambda 支持 auto 参数（泛型 lambda）：`[](auto a, auto b) { return a + b; }`
- 返回类型推导（auto 可做函数返回类型，编译器推导）
- constexpr 函数放宽（可多条语句、循环、分支）
- make_unique 标准化
- 变量模板（`template<class T> constexpr T pi = T(3.14159);`）

---

### 2.3 C++17 核心特性

**C++17 最重要的新增特性？** ⭐⭐

- 结构化绑定：`auto [x, y] = pair`、`auto [it, ok] = map.insert(...)`
- if constexpr：编译期条件分支，不满足条件的分支不会被实例化
- 折叠表达式：`(args + ...)` 简化变参模板
- string_view：轻量级字符串视图，不拥有数据
- optional/variant/any：标准化的代数数据类型
- 内联变量(inline variable)：头文件中定义变量无需 .cpp 再定义
- 并行算法：`std::sort(std::execution::par, v.begin(), v.end())`
- 类模板参数推导(CTAD)：`std::pair p(1, 2.0)` 无需指定模板参数

追问：optional 和 nullptr 有什么区别？（optional<T> 表示"可能有 T"，nullptr 表示空指针）

---

### 2.4 C++20 关键特性

**C++20 最值得关注的四大特性？** ⭐⭐

- Concepts：约束模板参数，`template<std::integral T>`。比 SFINAE 更清晰，错误信息更友好
- Coroutines：无栈协程，co_await/co_yield/co_return，编译器生成状态机
- Ranges：管道风格操作数据，`v \| filter(...) \| transform(...)`，惰性求值
- Modules：替代头文件，#include 的现代化，减少编译时间
- 三路比较(spaceship operator `<=>`)：自动生成比较运算符
- span：轻量级数组视图，不拥有数据
- format：类型安全的字符串格式化

追问：C++20 协程和 Go goroutine 的区别？（无栈 vs 有栈，编译器静态转换 vs 运行时动态调度）

---

## 3. STL 标准库

### 3.1 序列容器

**vector 扩容机制是怎样的？** ⭐⭐⭐

size == capacity 时触发：新容量通常是 1.5 倍（GCC）或 2 倍（MSVC）。步骤：分配新内存→移动/拷贝元素→释放旧内存→更新指针。追问：为什么 GCC 选 1.5 而不是 2？（1.5 倍扩容后释放的内存可被下一次分配复用，减少碎片）

**vector 迭代器什么时候失效？** ⭐⭐⭐

- 插入/删除：当前位置及之后所有迭代器失效
- 扩容：所有迭代器失效（内部存储地址变了）
- push_back：若触发扩容则全部失效
- clear：全部失效

追问：如何安全地在遍历中删除元素？（`it = v.erase(it)` 或 erase-remove 惯用法）

**deque 的底层实现？** ⭐⭐

分段连续空间：中控器（指针数组，指向每个连续缓冲区）+ 多个大小相同的缓冲区。首尾插入 O(1)，中间插入 O(N)。与 vector 相比：不要求连续存储、不会因扩容导致大量拷贝。追问：deque 的随机访问怎么实现？（先定位中控器中的缓冲区，再定位缓冲区中的元素，两次间接访问）

**list 什么时候选它？** ⭐⭐

双向循环链表。O(1) 任意位置插入删除，迭代器稳定（不因其他操作失效）。但 cache 不友好（内存碎片化）、每个节点额外两个指针开销。选用场景：频繁中间插入/删除 + 不需要随机访问 + 需要迭代器稳定。追问：C++11 引入的 forward_list 和 list 的区别？（单向链表 vs 双向链表，更省内存）

---

### 3.2 关联容器

**map 和 unordered_map 底层对比？** ⭐⭐⭐

| 对比维度 | map | unordered_map |
|---------|-----|--------------|
| 底层结构 | 红黑树 | 哈希表（拉链法） |
| 时间复杂度 | O(logN) | 平均 O(1)，最坏 O(N) |
| 有序性 | 按 key 升序 | 无序 |
| 迭代器 | 双向，稳定 | 前向，rehash 失效 |
| 内存占用 | 小（三指针+颜色） | 大（bucket 数组+节点指针） |
| key 要求 | operator< | hash + operator== |

追问：unordered_map 的负载因子(load factor)是什么？（size / bucket_count，超过 max_load_factor 触发 rehash）

**set 和 multiset 的区别？** ⭐

set 不允许重复元素，insert 返回 `pair<iterator, bool>`。multiset 允许重复，insert 返回 iterator。追问：如何用 set 实现去重排序？（直接 insert，自动去重且有序）

---

### 3.3 容器适配器

**stack 和 queue 的默认底层容器？** ⭐

stack 默认用 deque，也可用 vector/list。queue 默认用 deque，也可用 list。追问：priority_queue 底层是什么？（默认 vector + 堆算法，可指定底层容器和比较器）

---

### 3.4 迭代器与算法

**五种迭代器类别？** ⭐⭐

输入/输出/前向/双向/随机访问。能力依次增强。list::iterator 是双向，vector::iterator 是随机访问。追问：如何判断迭代器类型？（iterator_traits<I>::iterator_category）

**erase-remove 惯用法是什么？** ⭐⭐

`v.erase(remove(v.begin(), v.end(), val), v.end())`。remove 不改变容器大小，只把保留元素前移，返回新逻辑结尾。erase 真正删除。追问：为什么 remove 不直接删除元素？（remove 只拿到迭代器，没有容器引用，无法调用 erase）

**sort 底层实现？** ⭐⭐

Introsort：快排为主，递归深度 > logN 时转堆排序（防止退化到 O(N²)），小区间转插入排序（减少递归开销）。追问：为什么小数据量用插入排序？（常量小、无递归调用开销、cache 友好）

**lower_bound 和 upper_bound 区别？** ⭐

lower_bound：第一个 >= value 的位置。upper_bound：第一个 > value 的位置。都要求有序。追问：[lower_bound, upper_bound) 表示的区间是什么？（所有等于 value 的元素）

---

### 3.5 空间配置器

**SGI STL 双级配置器原理？** ⭐⭐

SGI STL（GCC libstdc++ 的基础）使用两级分配器：
- 一级：直接封装 malloc/free，处理内存不足时的 OOM 回调
- 二级：内存池管理，维护 16 个自由链表（8/16/24/.../128 字节），小于 128 字节从对应链表取，大于 128 字节走一级

追问：空间配置器解决了什么核心问题？（减少小块内存 malloc/free 的内核调用开销和碎片问题）

**allocator 和 allocator_traits 的关系？** ⭐

C++11 引入 allocator_traits 统一自定义 allocator 的接口，提供默认实现。简化了自定义 allocator 的开发（无需提供所有成员类型和函数）。

---

### 3.6 智能指针

**unique_ptr 和 shared_ptr 的适用场景？** ⭐⭐⭐

- unique_ptr：独占所有权，轻量（大小等同裸指针），适合局部动态对象、工厂函数、PIMPL
- shared_ptr：共享所有权，引用计数（原子操作有开销），适合多个所有者场景、异步回调
- weak_ptr：不增加计数，解决循环引用，需 lock() 转为 shared_ptr 访问

追问：shared_ptr 是线程安全的吗？（引用计数操作是线程安全的，但对象本身访问不是）

**shared_ptr 的引用计数存在哪？为什么？** ⭐⭐

存在堆上（控制块），多个 shared_ptr 共享同一控制块。控制块包含：引用计数、弱引用计数、删除器、分配器。追问：make_shared 相比 new shared_ptr 的优势？（一次分配对象+控制块，减少分配次数和内存碎片；但 weak_ptr 存在时可能延迟释放对象内存）

**enable_shared_from_this 的原理和使用场景？** ⭐⭐

从对象内部安全地生成 shared_ptr。原理：内部持有 weak_ptr，调用 shared_from_this() 时转为 shared_ptr。使用场景：异步回调中需要延长对象生命周期。追问：为什么不能在构造函数中调用 shared_from_this()？（此时 weak_ptr 尚未被外部 shared_ptr 初始化，会抛 bad_weak_ptr）

**weak_ptr 如何解决循环引用？** ⭐⭐⭐

经典场景：A 持有 B 的 shared_ptr，B 持有 A 的 shared_ptr → 双方无法释放。B 持有 A 的 weak_ptr 打破循环：weak_ptr 不增加引用计数，A 可以正常释放。追问：lock() 返回空时怎么处理？（对象已释放，忽略或做清理）

---

## 4. 数据结构与算法

> C++ 面试中数据结构和算法通常不单独考察，而是隐含在场景题和编码题中。
> 以下聚焦高频问题，每个数据结构都以面试官常问的方式进行组织。

### 4.1 线性结构

**数组和链表的区别及适用场景？** ⭐⭐⭐

| 维度 | 数组(vector) | 链表(list) |
|------|-------------|-----------|
| 内存 | 连续，cache 友好 | 分散，cache 不友好 |
| 随机访问 | O(1) | O(N) |
| 插入删除 | O(N)（移动元素） | O(1)（已定位到位置） |
| 内存开销 | 仅数据 | 额外指针 |
| 扩容 | 需要整体重新分配 | 不需要 |

追问：什么时候必须选链表？（频繁中间插入删除 + 不需要随机访问 + 迭代器要求稳定）

**如何实现一个 LRU Cache？** ⭐⭐⭐

哈希表 + 双向链表（或直接用 std::list + unordered_map）。get 时将节点移到链表头部，put 时若满则淘汰链表尾部。全部 O(1)。追问：为什么不用单向链表？（删除节点需要找前驱，单向 O(N)）

**如何判断链表有环？** ⭐⭐

快慢指针：慢指针每次走 1 步，快指针每次走 2 步。若快慢相遇则有环；快指针到 null 则无环。追问：如何找环入口？（相遇后慢指针回到头，两指针同速走，再次相遇点即入口）

**栈和队列的典型应用场景？** ⭐

栈：函数调用栈、括号匹配、DFS 非递归、表达式求值。队列：BFS、生产者消费者、任务排队、消息缓冲。追问：如何用两个栈实现队列？（栈1入队，栈2出队；栈2空时将栈1全倒入栈2）

---

### 4.2 树结构

**二叉树三种遍历的递归与非递归实现？** ⭐⭐⭐

前序（根左右）、中序（左根右）、后序（左右根）。非递归：用栈模拟递归过程。前序：入栈右子再左子。中序：一路向左入栈，出栈访问后转向右子。后序：前序（根右左）的反序，或标记法。追问：Morris 遍历的原理？（利用空闲指针，O(1) 额外空间，通过线索二叉树避免栈）

**二叉搜索树(BST)的特点？** ⭐⭐

左子树 < 根 < 右子树。查找/插入/删除 O(logN) ~ O(N)（退化为链表）。追问：为什么实际中不用 BST 而用红黑树？（BST 无自平衡，插入顺序不好时退化为链表）

**红黑树和 AVL 树的区别？** ⭐⭐

| 维度 | AVL 树 | 红黑树 |
|------|--------|--------|
| 平衡条件 | 严格平衡（高度差 ≤ 1） | 宽松平衡（最长 ≤ 2×最短）|
| 查找 | 更快（严格平衡） | 稍慢 |
| 插入删除 | 旋转次数多 | 旋转次数少（≤ 3 次）|
| 应用 | 查找密集型 | 插入删除密集型（如 std::map、Java TreeMap） |

追问：红黑树的五条性质？（1. 节点红或黑 2. 根黑 3. 叶子(NIL)黑 4. 红节点两子黑 5. 任意节点到叶子黑节点数相同）

**B 树和 B+ 树的区别？为什么 MySQL 用 B+ 树？** ⭐⭐⭐

| 区别 | B 树 | B+ 树 |
|------|------|------|
| 数据存放 | 所有节点 | 仅叶子节点 |
| 叶子节点 | 无链表 | 双向链表相连 |
| 范围查询 | 需中序遍历 | 顺序遍历叶子链表 |
| 非叶开销 | 存数据，扇出小 | 仅存键，扇出大 |

MySQL 选 B+ 树原因：范围查询高效（叶子链表）、树高低、IO 次数少、查询稳定

---

### 4.3 哈希表

**哈希冲突的解决方法？** ⭐⭐⭐

1. 链地址法（拉链法）：每个桶存链表/红黑树。STL unordered_map 用此法
2. 开放地址法：线性探测、二次探测、双重哈希。成功查找需特殊标记删除位
3. 再哈希法：多个哈希函数，冲突时换函数

追问：为什么 Java HashMap 的链表长度 > 8 转红黑树？（防止哈希碰撞攻击导致退化到 O(N)）

**一个好的哈希函数需要什么特性？** ⭐⭐

均匀分布、雪崩效应(输入微小变化→输出巨大变化)、计算快。追问：std::hash 的默认实现有什么问题？（对整数通常就是恒等映射，需要自己特化复杂类型）

---

### 4.4 排序算法

**各类排序算法的时间复杂度和稳定性？** ⭐⭐⭐

| 算法 | 最好 | 平均 | 最坏 | 空间 | 稳定 |
|------|------|------|------|------|:----:|
| 冒泡 | O(N) | O(N²) | O(N²) | O(1) | ✓ |
| 选择 | O(N²) | O(N²) | O(N²) | O(1) | ✗ |
| 插入 | O(N) | O(N²) | O(N²) | O(1) | ✓ |
| 希尔 | O(N) | O(N^1.3) | O(N²) | O(1) | ✗ |
| 归并 | O(NlogN) | O(NlogN) | O(NlogN) | O(N) | ✓ |
| 快速 | O(NlogN) | O(NlogN) | O(N²) | O(logN) | ✗ |
| 堆 | O(NlogN) | O(NlogN) | O(NlogN) | O(1) | ✗ |
| 计数 | O(N+K) | O(N+K) | O(N+K) | O(K) | ✓ |
| 基数 | O(N×K) | O(N×K) | O(N×K) | O(N+K) | ✓ |

追问：为什么快排比归并排序更常用？（内存局部性更好、常数因子小、可原地排序）

**快排如何避免退化到 O(N²)？** ⭐⭐

随机选 pivot、三数取中、小数组转插入排序、递归深度监控转堆排序（Introsort）。追问：partition 的两种实现方式？（Lomuto：简单但交换多、Hoare：交换少但边界复杂）

---

### 4.5 查找算法

**二分查找的实现要点？** ⭐⭐

`mid = left + (right - left) / 2` 防溢出；while 条件 left <= right 或 left < right。追问：查找第一个 >= target 的元素？（lower_bound 的变体，收缩右边界）

---

### 4.6 动态规划

**动态规划的核心思想？** ⭐⭐

最优子结构 + 重叠子问题。状态定义 → 状态转移方程 → 边界条件 → 计算顺序（自顶向下带 memo 或自底向上递推）。追问：DP 和贪心的区别？（DP 考虑全局最优，贪心只做局部最优选择；DP 可以回溯所有选择）

**经典 DP 问题 3 选 1 快速过：** ⭐

- 背包问题（0-1 背包：`dp[i][w] = max(dp[i-1][w], dp[i-1][w-w_i] + v_i)`）
- 最长公共子序列 LCS：`dp[i][j] = dp[i-1][j-1]+1 (if x_i==y_j) else max(dp[i-1][j], dp[i][j-1])`
- 编辑距离：插入/删除/替换的最小代价

---

### 4.7 海量数据处理

**TopK 问题如何解决？** ⭐⭐⭐

小数据：快速选择（partition 法，O(N)）或大小为 K 的小顶堆（O(NlogK)）。海量数据：内存放不下 → 分治 + 哈希分桶：分到多个小文件各自求 TopK，再合并求最终 TopK。追问：堆排和快选的 TopK 怎么选？（K 小用堆，K 接近 N 用快选）

**海量数据去重/统计频率？** ⭐⭐

- 内存够：unordered_map/HashMap
- 内存不够：分治到小文件 + 各自统计后合并
- 允许误差：布隆过滤器（去重，判断不存在一定准确）、HyperLogLog（基数统计，误差 0.81%）、Count-Min Sketch（频率估计）

---

## 5. 并发编程

### 5.1 线程基础

**std::thread 的生命周期管理？** ⭐⭐

构造后线程立即启动。析构前必须 join（等待完成）或 detach（分离），否则 std::terminate。C++20 jthread 析构时自动 join + 支持中断。追问：detach 后如何安全地通知线程退出？（原子 flag + 条件变量，或 jthread 的 stop_token）

**thread_local 的用途？** ⭐

每个线程独立一份变量副本，线程退出时按构造逆序析构。常见用途：线程特有的上下文（如日志 trace_id）、errno。追问：thread_local 和函数内 static 有什么区别？（thread_local 每线程一份，static 全局一份）

---

### 5.2 互斥与同步

**std::mutex 的底层实现？** ⭐⭐

Linux 基于 futex（fast userspace mutex）。无竞争时用户态原子操作直接加锁（零系统调用），有竞争时通过 futex 系统调用在内核等待。追问：futex 比纯内核 mutex 好在哪？（大部分情况无竞争，避免昂贵的内核切换）

**lock_guard 和 unique_lock 的区别？** ⭐⭐

| 维度 | lock_guard | unique_lock |
|------|-----------|-------------|
| 灵活性 | 最低 | 最高 |
| 开销 | 最小 | 有额外 bool 标志 |
| 手动 unlock | 不支持 | 支持 |
| 延迟加锁 | 不支持 | 支持（defer_lock） |
| 转移所有权 | 不可移动 | 可移动 |
| 配合条件变量 | 不支持 | 支持 |

追问：condition_variable::wait 为什么需要 unique_lock？（wait 内部需要解锁→等待→重新加锁，需要灵活的锁控制）

**条件变量的正确使用方式？** ⭐⭐

```cpp
std::unique_lock<std::mutex> lock(mtx);
cv.wait(lock, [&]{ return condition; });  // 带谓词，防止虚假唤醒
```
虚假唤醒：OS 调度原因，线程可能被意外唤醒。必须用 while 或 wait 的 lambda 形式判断条件。

**读写锁(shared_mutex)的使用场景？** ⭐

C++14 shared_timed_mutex，C++17 shared_mutex。多读少写场景：多个 shared_lock(读) 共享、一个 unique_lock(写) 独占。追问：读写锁可能饥饿吗？（写者饥饿：大量读者时写者永远获取不到，实现通常给写者优先级）

---

### 5.3 原子操作与内存序

**原子操作如何保证线程安全？** ⭐⭐⭐

依赖 CPU 原子指令（如 x86 lock 前缀、CAS）。std::atomic 保证读取和写入的原子性，但要配合内存序保证可见性和顺序性。追问：atomic 的操作一定是 lock-free 的吗？（不一定，大对象可能用内部锁，is_lock_free() 检测）

**六种内存序的含义？** ⭐⭐

- memory_order_relaxed：只保证原子性，不保证顺序
- memory_order_acquire：读操作，确保后续读写不重排到之前
- memory_order_release：写操作，确保之前读写不重排到之后
- memory_order_acq_rel：acquire + release
- memory_order_seq_cst：全局顺序一致性（默认，性能开销最大）
- memory_order_consume：类似 acquire 但只依赖数据依赖（很少用）

追问：release-acquire 如何建立 happens-before 关系？（release 写 store + acquire 读 load 同一原子变量 → 写线程之前的所有写对读线程之后的所有读可见）

**CAS 的 ABA 问题如何解决？** ⭐⭐

值从 A→B→A，CAS 误判未变化。解决：带版本号（tagged pointer）、double-width CAS（cmpxchg16b）、使用 `compare_exchange_strong`（保证只在值确实相等时成功）。追问：compare_exchange_strong 和 weak 的区别？（weak 允许伪失败，多用于循环；strong 保证只在实际值不同时才失败）

---

### 5.4 线程池与异步

**如何设计一个 C++ 线程池？** ⭐⭐⭐

核心要素：
1. 固定数量 worker 线程 + 任务队列（std::function<void()>）
2. submit 返回 std::future<T>（通过 packaged_task 实现）
3. 条件变量通知 + mutex 保护队列
4. 优雅关闭：设置 stop flag → 唤醒所有线程 → join
5. 可选：work stealing、饱和策略（丢弃/阻塞调用者/抛异常）

追问：线程池的任务队列选无界还是有界？（有界队列可控内存，配合拒绝策略；无界队列可能导致 OOM）

**std::async 的使用陷阱？** ⭐⭐

返回的 future 如果不存变量（临时对象），析构时会阻塞等待任务完成 → 失去异步意义。追问：std::async 默认的执行策略？（launch::async \| launch::deferred，允许实现选择惰性或异步执行，这很坑）

---

### 5.5 无锁编程

**如何实现一个无锁 SPSC 队列？** ⭐⭐⭐

环形缓冲区 + 两个原子索引（write_pos / read_pos）。生产者只写 write_pos，消费者只读 read_pos。满/空判断：write_pos == read_pos + capacity（满）、write_pos == read_pos（空）。注意 cache line padding 防伪共享。追问：如何扩展为 MPMC？（多写者 CAS 抢 write_pos，但会降低吞吐）

**无锁栈(Treiber Stack)的实现和问题？** ⭐

基于 CAS 的单链表栈。核心问题是内存回收：pop 时 release 了节点但可能有其他线程还在读 → 用 Hazard Pointer 或 Epoch-based GC 解决。追问：C++ 标准库中有无锁数据结构吗？（std::atomic 可构建无锁结构，但标准库中的容器都不是 lock-free 的）

---

### 5.6 死锁与排查

**死锁的四个必要条件？** ⭐⭐

互斥、请求保持、不可剥夺、循环等待。破坏任一即可预防：按固定顺序加锁、用 std::lock 同时加锁、try_lock 超时机制。追问：如何用 GDB 排查死锁？（查看线程栈：`info threads` + `thread apply all bt`，找 blocked/futex_wait）

---

## 6. 操作系统

### 6.1 进程与线程

**进程和线程的本质区别？** ⭐⭐⭐

进程是资源分配的基本单位（独立地址空间），线程是 CPU 调度的基本单位（共享地址空间）。Linux 内核中线程就是轻量级进程(LWP)，clone 系统调用不同标志位实现。追问：进程切换和线程切换的开销差异？（进程切换需要切换地址空间/页表/刷新 TLB，线程切换只需切换栈和寄存器，开销小得多）

**线程共享进程的哪些资源？哪些是独享的？** ⭐⭐

共享：地址空间（堆、全局变量、静态变量）、文件描述符表、信号处理函数、当前目录。独享：栈、寄存器、线程局部存储(TLS)、errno。追问：两个线程同时 malloc 安全吗？（glibc 的 malloc 是线程安全的，内部有 arena 锁机制）

**孤儿进程和僵尸进程？** ⭐⭐

孤儿进程：父进程先退出，子进程被 init(PID=1) 收养。僵尸进程：子进程退出但父进程未 wait，保留 task_struct 占用 PID。大量僵尸 → PID 耗尽，无法创建新进程。解决：父进程调用 wait/waitpid，或显式忽略 SIGCHLD。追问：kill -9 能杀死僵尸进程吗？（不能，僵尸已死，只是没被回收）

---

### 6.2 内存管理

**虚拟内存的作用？** ⭐⭐⭐

让每个进程有独立的地址空间 → 隔离性/安全性；物理内存不连续也能映射为连续虚拟内存 → 减少碎片；交换到磁盘 → 突破物理内存限制。追问：64 位系统用户空间虚拟地址范围？（0x0 ~ 0x00007FFFFFFFFFFF，47 位地址空间）

**缺页中断(Page Fault)的处理流程？** ⭐⭐

MMU 发现页面不在物理内存 → 触发缺页异常 → 内核检查地址合法性 → 不合法则 SIGSEGV → 合法：Minor fault（在内存但未映射）直接映射，Major fault（在磁盘）调度 IO 读取。追问：fork 后的 COW 什么时候触发 major fault？（写入共享页面时触发 minor fault 拷贝页面）

**malloc 底层是如何分配内存的？** ⭐⭐

小于 128KB：从 arena 的 bins 中分配（brk 扩展数据段），先找 tcache(线程缓存)，再找 fastbins/smallbins/largebins，都没有则从 top chunk 切。大于 128KB：mmap 匿名映射。追问：为什么大块内存用 mmap 而不是 brk？（mmap 可独立释放，brk 只能从高地址往低释放，顶部有碎片无法还给 OS）

**Linux 常用内存分配器对比？** ⭐

ptmalloc（glibc 默认，多 arena 减少锁竞争）、tcmalloc（Google，线程缓存 + 中央堆）、jemalloc（Facebook，多 arena + 细粒度控制，对碎片控制更好）。追问：什么时候需要换掉默认 allocator？（多线程高并发大量小对象分配 → 换 jemalloc/tcmalloc 减少锁竞争）

**大页(Huge Page)的优势与风险？** ⭐

默认 4KB 页面，大页 2MB/1GB 减少 TLB miss、提高内存访问性能。风险：内部碎片、需要大块连续物理内存、预分配。透明大页(THP) 静默合并但可能造成延迟尖刺。追问：什么时候应该关掉 THP？（Redis、数据库等延迟敏感型应用）

---

### 6.3 文件系统与IO

**Linux 五种 IO 模型？** ⭐⭐⭐

1. 阻塞 IO：线程挂起等待数据
2. 非阻塞 IO：立即返回 EAGAIN，轮询
3. IO 多路复用：select/poll/epoll 监听多个 fd
4. 信号驱动 IO：SIGIO 通知数据就绪
5. 异步 IO：内核完成全部操作后通知（io_uring 是真异步）

追问：IO 多路复用本质是同步还是异步？（同步，需要用户态主动 read/write 数据）

**零拷贝技术 sendfile 和 mmap？** ⭐⭐

传统路径：disk→内核缓冲区→用户缓冲区→socket 缓冲区→网卡，共 4 次拷贝 4 次上下文切换。sendfile：disk→内核缓冲区→socket 缓冲区→网卡（DMA gather），2 次拷贝 2 次切换。mmap+write：disk→内核缓冲区(与用户映射) → socket 缓冲区→网卡，3 次拷贝 4 次切换。追问：sendfile 的限制？（只能文件→socket，需要 DMA scatter-gather 硬件支持）

---

### 6.4 IPC

**进程间通信方式对比？** ⭐⭐

| IPC 方式 | 速度 | 数据量 | 是否需要同步 | 跨网络 |
|---------|------|--------|:----------:|:-----:|
| 管道(pipe) | 中 | 小 | 否 | 否 |
| FIFO | 中 | 中 | 否 | 否 |
| 消息队列 | 中 | 中 | 否 | 否 |
| 共享内存 | 极快 | 大 | 是 | 否 |
| Socket | 慢 | 大 | 否 | 是 |
| 信号(Signal) | 快 | 极小 | 否 | 否 |

追问：共享内存为什么最快？（数据不经过内核中转，只需一次拷贝或零拷贝映射）

---

### 6.5 信号与异常

**Linux 信号处理函数的限制？** ⭐⭐

信号处理函数（signal handler）中只能调用 async-signal-safe 函数。不可调用 malloc（内部有锁，可能死锁）、printf（内部有锁）、pthread_mutex_lock。追问：SIGPIPE 怎么处理？（忽略 SIGPIPE 或用 MSG_NOSIGNAL；向已关闭 socket 写数据触发 SIGPIPE，默认行为终止进程）

**core dump 是什么？怎么分析？** ⭐⭐

进程异常终止（SIGSEGV/SIGABRT 等）时 OS 将进程内存镜像写入 core 文件。设置 `ulimit -c unlimited`。GDB 加载：`gdb ./binary core` → bt 查看崩溃栈。追问：core dump 太慢/太大怎么办？（设置 filter 只 dump 关键内存段，或用 minidump）

---

## 7. 计算机网络

### 7.1 TCP/IP 协议栈

**TCP 三次握手过程与状态转换？** ⭐⭐⭐

C→S SYN(seq=x) → SYN_SENT
S→C SYN+ACK(seq=y, ack=x+1) → SYN_RCVD
C→S ACK(ack=y+1) → ESTABLISHED
追问：为什么是三次不是两次？（防止旧重复 SYN 建立无效连接、确认双方收发能力正常）

**TCP 四次挥手与 TIME_WAIT？** ⭐⭐⭐

主动关闭方进入 TIME_WAIT 持续 2MSL（约 60s）：确保最后的 ACK 能重传、让旧连接报文在网络中消失。追问：大量 TIME_WAIT 怎么处理？（tcp_tw_reuse、长连接、调整内核参数）

**TCP 和 UDP 的区别？** ⭐⭐

| 维度 | TCP | UDP |
|------|-----|-----|
| 连接 | 面向连接 | 无连接 |
| 可靠性 | 可靠（确认+重传） | 不可靠 |
| 顺序 | 有序 | 无序 |
| 头部大小 | 20 字节 | 8 字节 |
| 场景 | HTTP、SSH、DB | DNS、游戏、直播 |

**TCP 拥塞控制算法演进？** ⭐⭐

Reno（基于丢包）→ CUBIC（Linux 默认，优化高带宽）→ BBR（Google，基于带宽和 RTT 探测，适合高延迟有损网络）。追问：BBR 的核心改进？（不依赖丢包信号，通过探测链路带宽和 RTT 控制发送速率）

---

### 7.2 HTTP/HTTPS

**HTTP 各版本的区别？** ⭐⭐

HTTP/1.0：短连接，每次请求新建 TCP。HTTP/1.1：持久连接 + 管线化（队头阻塞）。HTTP/2：多路复用 + 头部压缩 + 二进制帧 + 服务器推送。HTTP/3：基于 QUIC(UDP)，零 RTT 握手，彻底解决队头阻塞。追问：HTTP/2 的多路复用如何实现？（一个 TCP 连接中多个 stream 并发传输，二进制分帧层）

**HTTPS 的 TLS 握手过程？** ⭐⭐

TLS 1.2（2-RTT）：ClientHello → ServerHello+证书+ServerKeyExchange → ClientKeyExchange+Finished → Finished。TLS 1.3（1-RTT）：减少了一个 RTT，废弃 RSA 密钥交换只保留前向安全的 ECDHE。追问：证书链的验证过程？（逐级验证签名直到根证书，校验证书有效期、域名、吊销状态）

---

### 7.3 IO 模型与高性能服务

**epoll 的原理？** ⭐⭐⭐

底层：红黑树（快速增删 fd）+ 就绪链表（就绪事件排队）。epoll_create 创建 eventpoll 对象，epoll_ctl 在红黑树中增删 fd，epoll_wait 直接从就绪链表取事件（O(1) 返回）。追问：epoll 的红黑树 key 是什么？（文件描述符 fd）

**epoll LT(水平触发) vs ET(边缘触发) 的区别与选择？** ⭐⭐⭐

LT(默认)：只要 fd 就绪就持续通知，编程简单但可能重复通知。ET：只在状态变化时通知一次，性能更高但要求非阻塞 IO + 循环读到 EAGAIN，否则事件丢失。追问：ET 模式为什么必须配合非阻塞 IO？（一次通知后 read 可能阻塞，错过后续事件）

**select/poll/epoll 三者对比？** ⭐⭐

| 维度 | select | poll | epoll |
|------|--------|------|-------|
| fd 数量限制 | 默认 1024 | 无限制 | 无限制 |
| 扫描方式 | O(N) 遍历 | O(N) 遍历 | O(1) 就绪列表 |
| 内核-用户拷贝 | 每次传入全量 | 每次传入全量 | 事件驱动 |
| 触发方式 | 水平 | 水平 | 水平+边缘 |
| 适用场景 | 少量连接 | 中等连接 | 大量连接 |

**Reactor 和 Proactor 模式的区别？** ⭐⭐

Reactor：IO 多路复用 + 非阻塞 IO，事件分离器通知就绪，应用自己读写（同步 IO）。Proactor：异步 IO，OS 完成读写后通知应用，应用直接处理结果（真异步，如 IOCP、io_uring）。追问：Redis 用的是什么模式？（单线程 Reactor）

---

### 7.4 序列化协议

**Protobuf 的原理和优势？** ⭐⭐

二进制序列化，基于 .proto 文件编译生成代码。Varint 编码：每字节最高位是终止位，剩余 7 bit 组成结果（小数字=少字节）。优势：体积极小、快、跨语言、前后兼容。追问：Protobuf 和 FlatBuffers 的区别？（Protobuf 需要序列化/反序列化，FlatBuffers 零反序列化直接访问）

**JSON 和二进制序列化如何选择？** ⭐

JSON：可读性高、调试方便、无 schema 依赖。二进制：性能好、体积小。内部 RPC 选 Protobuf，对外 API 选 JSON。追问：MessagePack 适合什么场景？（不需要 schema 又想比 JSON 更快更小，如嵌入式/移动端）

---

## 8. 编译链接与调试

### 8.1 编译链接过程

**C++ 程序从源码到可执行文件的四个阶段？** ⭐⭐

预处理（宏展开、#include 粘贴）→ 编译（C++→汇编）→ 汇编（汇编→目标文件 .o）→ 链接（多目标文件+库→可执行文件）。追问：预处理阶段 #include 发生了什么？（把被包含文件内容直接复制到当前文件）

**静态库和动态库的区别？** ⭐⭐

| 维度 | 静态库(.a) | 动态库(.so) |
|------|----------|-----------|
| 链接时机 | 编译时 | 运行时（或加载时） |
| 可执行文件大小 | 大（包含库代码） | 小 |
| 更新 | 需重新编译 | 替换 .so 即可 |
| 运行时依赖 | 无 | 需要对应版本 .so |

追问：动态库的 PLT/GOT 延迟绑定原理？（PLT 表项默认指向动态链接器，第一次调用时解析真实地址写入 GOT，后续调用直接通过 GOT 跳转）

**C++ name mangling 是什么？为什么需要？** ⭐

函数重载、命名空间、模板等导致相同函数名需要区分 → 编译器生成包含签名信息的修饰名。nm 查看，c++filt 反解析。extern "C" 禁止 mangling。追问：C 和 C++ 混合编程的关键？（头文件中用 `#ifdef __cplusplus extern "C" {}`，确保符号表兼容）

---

### 8.2 GDB 调试

**GDB 常用命令清单？** ⭐⭐

| 场景 | 命令 |
|------|------|
| 启动调试 | `gdb ./prog`、`gdb ./prog core` |
| 设置断点 | `break func`、`break file.cpp:42`、`break *0xaddr` |
| 单步 | `next`(不进入函数)、`step`(进入)、`finish`(跑完函数)、`until` |
| 查看变量 | `print var`、`info locals`、`display var`(每次停自动显示) |
| 栈回溯 | `backtrace`/`bt`、`frame N`(切换栈帧) |
| 内存 | `x/10x addr`(10 个 16 进制)、`info registers` |
| 多线程 | `info threads`、`thread N`、`thread apply all bt` |
| 条件断点 | `break func if x > 100` |

追问：release 模式下 GDB 调试有什么限制？（优化导致变量被消除/乱序，断点可能打在非预期位置，需要 -Og 做折中）

**core dump 分析流程？** ⭐⭐

1. `ulimit -c unlimited` 放开限制
2. 复现崩溃得到 core 文件
3. `gdb ./binary core` 加载
4. `bt` 查看崩溃栈 ← 最常用的第一步
5. `frame N` 切换到关键帧，`info locals` 查看局部变量
6. `print ptr`、`x/10x addr` 查看内存

---

### 8.3 性能分析工具

**perf 的使用方法和火焰图解读？** ⭐⭐

perf top：实时看 CPU 热点函数。perf record + perf report：采样生成报告。火焰图：宽度 = CPU 占比，高度 = 调用深度。追问：perf 采样的原理？（基于 PMU 硬件计数器的事件采样，定时中断记录当前 IP）

**内存错误检测工具对比？** ⭐⭐

| 工具 | 原理 | 特点 |
|------|------|------|
| Valgrind Memcheck | 动态二进制翻译 | 慢(10-50x)、无需重编译 |
| AddressSanitizer | 编译插桩 | 快(2x)、需重编译 |
| MemorySanitizer | LLVM 插桩 | 检测未初始化内存读取 |

---

### 8.4 构建系统

**CMake 基本工作流？** ⭐

CMakeLists.txt → cmake 生成 Makefile/ninja → make/ninja 编译。Modern CMake 推荐 target-based 写法（target_link_libraries 传递依赖），避免全局 include_directories。追问：PUBLIC/PRIVATE/INTERFACE 在 target_link_libraries 中的含义？

---

## 9. MySQL

### 9.1 索引

**B+ Tree 的结构特点和优势？** ⭐⭐⭐

多路平衡查找树。非叶子节点只存索引键（更高扇出、更矮），叶子节点存完整数据并用双向链表相连（范围查询友好）。相比 B 树：IO 次数更少、查询更稳定、范围查询更快。追问：为什么不用跳表？（跳表随机 IO 多，B+ 树叶子节点顺序存储，磁盘预读友好）

**聚簇索引和非聚簇索引的区别？** ⭐⭐⭐

聚簇索引（InnoDB 主键）：叶子节点存整行数据。非聚簇索引（二级索引）：叶子节点存主键值，需要回表。追问：覆盖索引是什么？（查询字段都在索引中，无需回表，通过 EXPLAIN 的 Extra: Using index 确认）

**最左前缀原则及索引失效场景？** ⭐⭐⭐

从最左列开始匹配，遇到范围查询中止。失效：`LIKE '%abc'`、跳过最左列、索引列做计算/函数、OR 一侧无索引、隐式类型转换、!=/<>、NOT IN。追问：联合索引 (a, b, c) 哪些查询能用索引？（`WHERE a=1 AND b>2` 用到 a,b；`WHERE b=1` 用不到）

---

### 9.2 事务与锁

**MySQL 事务隔离级别各自解决了什么问题？** ⭐⭐⭐

| 隔离级别 | 脏读 | 不可重复读 | 幻读 |
|---------|:---:|:--------:|:---:|
| READ UNCOMMITTED | ✗ | ✗ | ✗ |
| READ COMMITTED | ✓ | ✗ | ✗ |
| REPEATABLE READ(默认) | ✓ | ✓ | ✓(MVCC+Next-Key Lock) |
| SERIALIZABLE | ✓ | ✓ | ✓ |

追问：RR 级别如何解决幻读？（InnoDB 通过 MVCC 快照读 + Next-Key Lock 当前读结合）

**MVCC 的原理？** ⭐⭐⭐

隐藏字段（trx_id、roll_pointer）+ undo log 版本链 + ReadView（活跃事务列表）。RC：每次快照读生成新 ReadView，读到已提交的最新版本。RR：只在第一次快照读时生成 ReadView，后续复用，保证可重复读。追问：undo log 什么时候回收？（purge 线程在确认无事务需要历史版本后清理）

**InnoDB 的三类行锁？** ⭐⭐

记录锁(Record Lock)：锁单行。间隙锁(Gap Lock)：锁索引记录间的间隙（不含记录），防止插入。临键锁(Next-Key Lock)：记录锁 + 间隙锁，左开右闭，InnoDB 默认。追问：为什么唯一索引等值查询时 Next-Key Lock 降级为 Record Lock？（不需要防止插入重复值）

---

### 9.3 SQL 优化

**如何定位和优化慢 SQL？** ⭐⭐⭐

1. 开启慢查询日志（slow_query_log + long_query_time）
2. EXPLAIN 分析执行计划：type(扫描方式)、key(使用的索引)、rows(预估扫描行数)、Extra(Using filesort/Using temporary 是告警信号)
3. 优化：加索引、避免 SELECT *、用覆盖索引、JOIN 代替子查询、EXISTS 代替 IN
追问：EXPLAIN 中 type 从好到差的排序？（system > const > eq_ref > ref > range > index > ALL）

---

### 9.4 C++ 数据库连接

**C++ 项目如何连接 MySQL？** ⭐

MySQL Connector/C++(官方)、libmysqlclient(C API)、ODBC。高并发场景需要连接池（减少频繁建立连接的开销）。追问：C++ 连接池的实现要点？（固定数量连接、互斥锁保护获取/归还、健康检查、超时回收）

---

## 10. Redis

### 10.1 数据结构与原理

**Redis 为什么快？** ⭐⭐⭐

纯内存操作、单线程(避免锁和上下文切换) + IO 多路复用(epoll)、简洁的 RESP 协议、优化的内部数据结构(SDS/跳表/listpack/quicklist)。追问：Redis 6.0 的多线程是什么？（仅网络 IO 多线程读/写 socket 缓冲区，命令执行仍是单线程保证原子性）

**ZSet 为什么用跳表不用红黑树？** ⭐⭐

跳表实现更简单、范围查询更高效、概率平衡无需旋转。ZSet 底层：跳表 + 字典（跳表支持范围操作，字典支持 O(1) 查找）。追问：跳表的插入时间复杂度？（平均 O(logN)，最坏 O(N) 但概率极低）

---

### 10.2 缓存问题

**缓存穿透/击穿/雪崩的区别和解决方案？** ⭐⭐⭐

| 问题 | 定义 | 解决方案 |
|------|------|---------|
| 穿透 | 请求缓存和数据库都没有的数据 | 布隆过滤器 + 缓存空值 + 接口限流 |
| 击穿 | 热点 key 过期，大量请求打到 DB | 互斥锁重建 + 永不过期+异步刷新 + 逻辑过期 |
| 雪崩 | 大量 key 同时过期或 Redis 宕机 | 随机过期时间 + Redis 集群 + 多级缓存 + 限流降级 |

追问：布隆过滤器判断"不存在"一定是准确的吗？（是。但判断"存在"可能有 1% 误判率，因为哈希冲突）

**缓存和数据库一致性怎么保证？** ⭐⭐

Cache Aside：先更新数据库再删缓存（不是更新缓存）。失败用消息队列异步重试。延迟双删：先删缓存 → 更新数据库 → 延迟再删缓存，防止并发读写入脏数据。追问：为什么要删缓存而不是更新缓存？（缓存可能是计算/聚合结果，直接更新困难；删缓存更简单、惰性加载保证最新）

---

### 10.3 分布式与持久化

**Redis 分布式锁怎么实现？** ⭐⭐⭐

`SET key value EX 10 NX`（原子加锁，value 用 UUID 防误删），释放用 Lua 脚本保证原子性（先比较 value 再删除）。Redisson 看门狗自动续期：每 10s 检测持锁线程存活，异步续期 30s。追问：Redis 分布式锁靠谱吗？（主从切换可能丢锁，RedLock 算法增加副本投票，但业界有争议）

**RDB 和 AOF 的区别与选择？** ⭐⭐

RDB：定时快照，fork 子进程 COW，恢复快但可能丢数据。AOF：追加写命令，everysec 策略最多丢 1s，文件大需 rewrite。Redis 4.0+ 混合持久化：RDB 头部 + AOF 增量，兼顾速度和安全。追问：fork 子进程时 COW 会导致内存翻倍吗？（通常不会翻倍，只有被修改的页才会拷贝）

---

### 10.4 C++ Redis 客户端

**hiredis 和 redis-plus-plus 的选择？** ⭐

hiredis：C 语言最小依赖库，同步/异步 API，需要自己管理连接。redis-plus-plus：C++ 封装 hiredis，STL 友好、连接池、pipeline、cluster 支持、RAII。追问：hiredis 异步模式怎么集成到事件循环中？（通过 redisAsyncSetConnectCallback/redisAsyncSetDisconnectCallback 注册 libevent/libuv 回调）

---

## 11. 分布式系统

### 11.1 分布式基础理论

**CAP 理论和实际系统选择？** ⭐⭐⭐

C(一致性)、A(可用性)、P(分区容错性)。分布式系统 P 必须满足，只能在 CA 间权衡。实例：ZooKeeper 选 CP（选主期间不可用）、Eureka 选 AP（优先可用，数据可能不一致）。追问：C++ RPC 框架怎么处理 CAP？（brpc/srpc 关注 P + 性能和扩展性，一致性交给上层）

**BASE 理论？** ⭐⭐

Basically Available（基本可用）、Soft State（软状态，允许多副本的中间状态）、Eventually Consistent（最终一致性）。ACID 的反面，适用于大多数互联网场景。追问：最终一致性的实现手段？（消息队列异步同步、定时对账、读修复）

**一致性哈希的原理？** ⭐⭐

哈希环（0~2^32-1）+ 虚拟节点。节点增减时只影响相邻节点数据，减少大规模迁移。用于分布式缓存和数据分片。追问：虚拟节点的作用？（解决环上节点分布不均导致的"数据倾斜"问题）

---

### 11.2 消息队列

**Kafka/RocketMQ/RabbitMQ 如何选型？** ⭐⭐

| 维度 | Kafka | RocketMQ | RabbitMQ |
|------|-------|----------|----------|
| 吞吐 | 百万级 QPS | 十万级 QPS | 万级 QPS |
| 延迟 | 毫秒级 | 毫秒级 | 微秒级 |
| 可靠性 | 高（ISR） | 高（同步刷盘） | 高 |
| 事务消息 | 支持 | 原生支持 | 插件 |
| C++ 客户端 | librdkafka | rocketmq-client-cpp | amqpcpp |

追问：librdkafka 如何保证消息不丢？（enable.idempotence + acks=all + 手动 commit offset）

**如何保证消息不丢？** ⭐⭐⭐

生产者：同步发送 + ACK 确认 + 重试。Broker：多副本(ISR) + 同步刷盘。消费者：处理完后手动提交 offset，保证幂等性。追问：幂等性怎么实现？（唯一业务 ID 去重 + 数据库唯一约束/Redis 记录已处理 ID）

---

### 11.3 分布式一致性

**Raft 协议的核心机制？** ⭐⭐

Leader 选举（随机超时避免分裂）、日志复制（多数派确认）、安全性保证（Leader 的日志一定包含所有已提交的日志）。C++ 实现：braft、etcd 的 raft。追问：Raft 如何处理网络分区？（少数派的 Leader 发现无法提交日志会自动退位）

**分布式事务方案对比？** ⭐⭐

2PC（两阶段提交）：Prepare→Commit，同步阻塞、单点故障。TCC（补偿事务）：Try→Confirm/Cancel，业务层实现，需要处理空回滚/悬挂。可靠消息最终一致性：本地事务 + 消息表 + 异步确认。追问：TCC 的空回滚问题是什么？（Cancel 被调用时 Try 还未执行过，需记录 Try 状态判断是否要空回滚）

---

## 12. 系统设计与场景题

### 12.1 设计方法论

**系统设计的通用分析框架？** ⭐⭐

1. 需求澄清：功能需求、非功能需求（QPS/延迟/可用性）
2. 量级估算：DAU→QPS→存储→带宽
3. 高层设计：模块划分、技术选型、数据流
4. 数据结构与存储：选 SQL/NoSQL/缓存/文件
5. 详细设计：接口定义、数据库 schema、核心算法
6. 瓶颈分析与扩展：单点、热点、数据倾斜

---

### 12.2 经典系统设计题

**秒杀系统怎么设计？** ⭐⭐⭐

静态化 + CDN → 网关限流（令牌桶） → Redis 库存预扣减（DECR 原子操作） → MQ 异步下单 → DB 最终落单。关键：防超卖（Redis DECR 返回负值则秒杀结束）、防刷（验证码+频率限制+用户资格校验）、削峰（MQ 缓冲）。追问：Redis 预扣减失败如何回滚？（用 Lua 脚本原子 INCR 回滚库存）

**短链系统怎么设计？** ⭐⭐

长 URL → 发号器生成唯一 ID → base62 编码 → 短链。302 重定向到原 URL。Redis 缓存热点短链。追问：哈希冲突怎么处理？（MurmurHash + 冲突时重新生成，或直接用自增 ID 避免冲突）

**高性能日志系统？** ⭐⭐

异步日志（双缓冲/spdlog 异步 sink） → 本地磁盘 → 采集 agent → Kafka → 消费端（ES/CK）。关键：低延迟（异步写入不阻塞业务）、可靠（agent 保证 at-least-once）、可检索。追问：spdlog 的异步原理？（环形队列 + 后台线程消费，生产者只做内存拷贝）

---

### 12.3 线上排查场景

**服务 CPU 突然飙升怎么排查？** ⭐⭐⭐

1. `top -H -p <pid>` 找到 CPU 占满的线程
2. 线程 TID 转十六进制 → `jstack <pid> | grep -A 20 <hex_tid>`（Java）或 `pstack <pid>`（C++）
3. 或用 `perf top` 直接看热点函数 → 火焰图分析调用链
4. 可能原因：死循环、full GC、正则回溯、自旋锁（lock-free 的忙等）
追问：perf top 看到热点在 epoll_wait → 正常吗？（正常，IO 密集型服务大部分时间在等待事件）

**内存持续上涨（疑似内存泄漏）怎么排查？** ⭐⭐⭐

1. `top/htop` 确认内存增长趋势
2. `pmap -x <pid>` 查看内存段分布 → 定位哪个区域在涨
3. `valgrind --tool=memcheck --leak-check=full`（开发环境）或 gperftools heap profiler（生产）
4. 对比不同时间点的 heap dump 看哪些对象/分配在持续增长
5. C++ 重点排查：未释放 new、循环引用 shared_ptr、容器未 clear
追问：生产环境不能用 valgrind 怎么排查？（用 tcmalloc/jemalloc 的 heap profiling 动态开启）

**服务响应延迟突然变大怎么排查？** ⭐⭐

1. 确认是整体还是个别接口变慢
2. 检查依赖：DB 慢查询（slow log）、Redis 慢日志、下游服务延迟
3. 检查资源：CPU（perf）、内存（是否 swap）、磁盘 IO（iostat）
4. 检查锁竞争：高并发下 mutex 阻塞、条件变量的信号丢失
5. 检查 GC 停顿（Java）/ 内存分配器锁竞争（C++ malloc arena）

---

## 13. 性能优化

### 13.1 CPU 优化

**Cache Line 与伪共享？** ⭐⭐⭐

Cache line 通常 64 字节。两个线程修改不同变量但处于同一 cache line → 频繁 invalidate → 性能暴跌。解决：`alignas(64)` 让变量独占 cache line，或加 padding。典型场景：无锁队列的读写指针需要分别跨 cache line。追问：你怎么发现生产环境的伪共享问题？（perf stat 查看 cache-misses 异常高，perf c2c 分析）

**分支预测与 `[[likely]]`/`[[unlikely]]`？** ⭐⭐

CPU 预测分支方向（正确无开销，错误 20+ 周期）。C++20 `[[likely]]`/`[[unlikely]]` 提示编译器调整代码布局（热路径放在一起）。追问：PGO(Profile Guided Optimization) 怎么优化分支？（先运行收集分支频率，重编译时据此优化布局、内联决策）

**SIMD 的应用场景？** ⭐

SSE/AVX 单指令多数据：一次处理 4/8/16 个数据。编译器自动向量化（-O3 -march=native）或手写 intrinsic。适用场景：批量数据处理（向量加法、图像处理、字符串比较）。追问：编译器自动向量化的条件？（无数据依赖、简单循环计数器、连续内存访问）

---

### 13.2 内存优化

**如何减少 malloc/free 开销？** ⭐⭐

- 对象池/内存池：预分配固定块，避免频繁分配释放
- Arena：一次分配大块，所有小对象从中分配，整体释放
- 自定义 allocator：替换默认 allocator，如 Protobuf Arena
- 避免热点路径分配：函数参数用引用/string_view 代替 string 拷贝
追问：对象池的分配和归还怎么做到 O(1)？（空闲链表，分配取头节点，归还插入头节点）

**AoS vs SoA（数据结构布局优化）？** ⭐⭐

AoS(Array of Structs)：`struct Entity { float x,y,z; int id; }; vector<Entity>` — 适合访问单个对象全部属性
SoA(Struct of Arrays)：`struct Entities { vector<float> x,y,z; vector<int> id; };` — 适合批量处理单个属性（SIMD 友好）
追问：什么场景选 SoA？（游戏物理更新只批量改坐标、数据库列式存储、SIMD 向量化批量操作）

---

### 13.3 系统级优化

**如何减少系统调用？** ⭐⭐

批量读写(readv/writev)、buffer IO、io_uring 批处理提交、mmap 替换 read/write。追问：系统调用为什么慢？（用户态-内核态切换：保存/恢复寄存器、刷新 TLB、上下文切换开销约数百 cycle）

**NUMA 和 CPU 亲和性？** ⭐⭐

NUMA 架构下访问本地节点内存比远端快。优化：绑核 + 绑内存（numactl/taskset），确保线程使用的内存分配在本地节点。追问：你的多线程程序有什么 NUMA 导致的性能问题？（无感知地跨节点访问共享数据结构导致延迟不稳定）

---

**📚 推荐书单**
- 《Effective Modern C++》— Scott Meyers，C++11/14 最佳实践
- 《C++ Concurrency in Action》— Anthony Williams，并发编程权威
- 《Linux 高性能服务器编程》— 游双，C++ 后端实战
- 《STL 源码剖析》— 侯捷，深入 STL 实现细节
- 《深入理解计算机系统》(CSAPP) — 系统编程基础
- 《高性能 MySQL》— 数据库优化
- 《Redis 设计与实现》— 黄健宏
- 《Linux/Unix 系统编程手册》— Kerrisk，Linux API 大全
