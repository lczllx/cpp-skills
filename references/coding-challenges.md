# C++ 编码题题库

> 聚焦 C++ 后端高频手写题。按难度分为实习/应届/社招三级。
> 出题时优先选择与 C++ 后端开发实际相关的题目，算法题为补充。

---

## 题目索引

| 编号 | 题目 | 难度 | 适合人群 | 考察重点 |
|------|------|------|---------|---------|
| CP01 | 实现 shared_ptr | ⭐⭐ | 应届/社招 | 引用计数、RAII、线程安全 |
| CP02 | 实现 unique_ptr | ⭐ | 实习/应届 | 移动语义、资源独占 |
| CP03 | 实现简单的 string 类 | ⭐⭐ | 应届/社招 | 拷贝控制、SSO、异常安全 |
| CP04 | 线程安全单例模式 | ⭐⭐ | 应届/社招 | 并发安全、双重检查锁定 |
| CP05 | 实现内存池 | ⭐⭐⭐ | 社招 | 内存管理、对齐、碎片化 |
| CP06 | 无锁 SPSC 队列 | ⭐⭐⭐ | 社招 | 原子操作、内存序、环形缓冲 |
| CP07 | 实现线程池 | ⭐⭐⭐ | 社招 | 并发编程、条件变量、任务队列 |
| CP08 | 手写 LRU Cache | ⭐⭐ | 应届/社招 | 哈希表+双向链表 |
| CP09 | 实现观察者模式 | ⭐ | 实习/应届 | 设计模式、智能指针 |
| CP10 | 实现简单的 vector | ⭐⭐ | 应届 | 动态扩容、迭代器、异常安全 |
| CP11 | 多线程交替打印 | ⭐⭐ | 应届 | 条件变量、mutex、原子变量 |
| CP12 | 环形缓冲区 | ⭐⭐⭐ | 社招 | 生产者消费者、原子操作 |
| CP13 | 手写定时器 | ⭐⭐ | 应届/社招 | 数据结构（堆/时间轮）、时间管理 |
| CP14 | 实现对象池 | ⭐⭐ | 社招 | 资源复用、线程安全 |
| CP15 | LeetCode 算法题 | ⭐~⭐⭐⭐ | 全体 | 数据结构与算法 |

---

## CP01：实现 shared_ptr

**难度**：⭐⭐  
**适合**：应届/社招  
**时间**：15-20 分钟

### 题目描述

实现一个简化版的 `shared_ptr<T>`，要求支持：
1. 引用计数管理，最后一个 shared_ptr 析构时释放资源
2. 拷贝构造、拷贝赋值、移动构造、移动赋值
3. `operator*` 和 `operator->`
4. `use_count()` 返回当前引用计数
5. `reset()` 安全释放
6. 线程安全的引用计数（加分项）

### 输入输出示例

```cpp
// 测试代码
auto sp1 = make_my_shared<int>(42);
assert(*sp1 == 42);
assert(sp1.use_count() == 1);

auto sp2 = sp1;
assert(sp1.use_count() == 2);
assert(sp2.use_count() == 2);

auto sp3 = std::move(sp2);
assert(sp1.use_count() == 2);
// sp2 此时为空

sp1.reset();
assert(sp3.use_count() == 1);
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 核心逻辑 | 40% | 引用计数正确递增/递减，正确释放资源 |
| 拷贝与移动 | 25% | 拷贝构造/赋值正确实现引用计数管理；移动语义正确实现所有权转移 |
| 边界情况 | 20% | 自赋值安全、nullptr 处理、引用计数并发安全 |
| 代码风格 | 15% | const 正确性、noexcept 的使用、现代 C++ 写法 |

### 追问方向

1. 引用计数字段存在哪里？（堆上，多个 shared_ptr 共享）
2. `enable_shared_from_this` 如何实现？
3. `make_shared` 和 `new shared_ptr` 的区别？（make_shared 两次内存分配合并为一次）
4. 为什么 shared_ptr 不支持数组？(C++17 起有 shared_ptr<T[]>)

---

## CP02：实现 unique_ptr

**难度**：⭐  
**适合**：实习/应届  
**时间**：10-15 分钟

### 题目描述

实现简化版 `unique_ptr<T>`：
1. 独占所有权语义
2. 禁用拷贝构造和拷贝赋值
3. 实现移动构造和移动赋值
4. `get()`、`release()`、`reset()`、`operator*`、`operator->`
5. 支持自定义删除器（模板参数，加分项）

```cpp
auto p1 = make_my_unique<int>(100);
// auto p2 = p1;              // 编译错误：不允许拷贝
auto p2 = std::move(p1);      // OK
assert(p1.get() == nullptr);  // 移动后源指针为空
assert(*p2 == 100);
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 核心逻辑 | 35% | 独占所有权、移动语义、资源释放 |
| 禁用拷贝 | 15% | =delete 的正确使用 |
| 移动安全 | 25% | 移动后源对象状态、自移动安全 |
| 边界情况 | 25% | nullptr 处理、reset/release 正确 |

---

## CP03：实现简单的 string 类

**难度**：⭐⭐  
**适合**：应届/社招  
**时间**：20-25 分钟

### 题目描述

实现一个简化版 MyString 类：
1. 支持 C 风格字符串构造：`MyString(const char*)`
2. 拷贝构造、拷贝赋值、移动构造、移动赋值
3. 析构函数正确释放内存
4. `size()`、`c_str()`、`operator[]`
5. `operator+=` 追加字符串
6. SSO(短字符串优化，加分项)

```cpp
MyString s1("hello");
MyString s2 = s1;            // 拷贝
MyString s3 = std::move(s1); // 移动
s3 += " world";
// s3.c_str() == "hello world"
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 内存管理 | 30% | RAII、深拷贝、移动优化 |
| 拷贝控制 | 25% | 拷贝/移动的正确实现，异常安全 |
| 边界情况 | 25% | null/空字符串、追加自身、内存泄漏 |
| SSO（加分）| 20% | 本地缓冲区、strlen 阈值判断 |

---

## CP04：线程安全单例模式

**难度**：⭐⭐  
**适合**：应届/社招  
**时间**：10 分钟

### 题目描述

用 C++ 实现线程安全的单例模式：
1. 懒汉式（第一次使用时创建）
2. 线程安全
3. 考虑析构时机

考察多种实现方式的对比。

```cpp
class Singleton {
public:
    static Singleton& getInstance();
    // 禁用拷贝和移动
    Singleton(const Singleton&) = delete;
    Singleton& operator=(const Singleton&) = delete;

    void doSomething();

private:
    Singleton() = default;
    ~Singleton() = default;
};
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 线程安全 | 40% | C++11 静态局部变量/Meyers Singleton 线程安全 |
| 实现优雅 | 30% | 代码简洁、=delete 使用 |
| 深入理解 | 30% | DCLP 为什么有问题、C++11 对静态局部变量的保证 |

### 追问方向

1. 静态局部变量的线程安全从 C++11 开始保证，原理是什么？（编译器插入锁/原子标志）
2. 双重检查锁定(DCLP)在 C++ 上的问题？（需要 volatile/atomic，否则可能访问未完全构造的对象）
3. 单例的销毁顺序问题？（静态对象析构顺序不确定，可能相互依赖）

---

## CP05：实现内存池

**难度**：⭐⭐⭐  
**适合**：社招  
**时间**：25-30 分钟

### 题目描述

实现一个简单的内存池（固定大小块内存池）：
1. 预分配一块大内存
2. 支持 `allocate()` 和 `deallocate()`
3. 利用空闲链表管理已释放的块
4. 考虑内存对齐（alignas）
5. 线程安全（加分项）

```cpp
template<typename T>
class MemoryPool {
public:
    MemoryPool(size_t blockCount = 1024);
    ~MemoryPool();

    T* allocate();          // 分配
    void deallocate(T* p);  // 释放
    size_t available() const; // 剩余可用块数

private:
    // 你的实现
    struct Block {
        // 空闲时：存 next 指针
        // 使用时：存 T 对象
    };
    // ...
};
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 内存管理 | 35% | 预分配、空闲链表复用、正确释放 |
| 对齐 | 20% | 内存对齐处理（alignas/alignof） |
| 类型安全 | 20% | placement new、显式调用析构 |
| 性能 | 15% | O(1) 分配/释放、cache 友好 |
| 线程安全 | 10% | 可选加分项：互斥锁或无锁实现 |

---

## CP06：无锁 SPSC 队列

**难度**：⭐⭐⭐  
**适合**：社招  
**时间**：20-25 分钟

### 题目描述

实现一个无锁的单生产者-单消费者(SPSC)环形队列：
1. 基于环形缓冲区(Circular Buffer)
2. 使用原子变量 `std::atomic<size_t>` 管理读写位置
3. `push()`：生产者写入
4. `pop()`：消费者读取
5. 正确处理队列满和队列空的情况

```cpp
template<typename T, size_t Capacity>
class SPSCQueue {
    static_assert((Capacity & (Capacity - 1)) == 0, 
                  "Capacity must be power of 2");

public:
    bool push(const T& item);  // 生产者
    bool pop(T& item);         // 消费者
    bool empty() const;
    bool full() const;

private:
    std::array<T, Capacity> buffer_;
    std::atomic<size_t> write_pos_{0};
    std::atomic<size_t> read_pos_{0};
    // 注意：防止伪共享(cache line padding)
};
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 原子操作 | 35% | 正确的内存序（release/acquire） |
| 环形缓冲 | 25% | 索引取模、容量为2的幂 |
| 伪共享 | 20% | cache line padding 避免 false sharing |
| 边界处理 | 20% | 满/空判断、capacity 必须为2的幂 |

### 追问方向

1. 为什么 Capacity 要是 2 的幂？（位运算取模 fast，不需要除法）
2. 内存序为什么用 release/acquire？（保证写入数据先于 write_pos 更新）
3. 如何扩展为 MPMC？（多写多读需要 CAS 竞争 write_pos/read_pos）

---

## CP07：实现线程池

**难度**：⭐⭐⭐  
**适合**：社招  
**时间**：25-30 分钟

### 题目描述

实现一个简单的 C++ 线程池：
1. 固定数量 worker 线程
2. 任务队列（线程安全）
3. `submit()` 提交任务返回 `std::future<T>`
4. 优雅关闭（等待所有任务完成）
5. 支持可调用对象（函数指针、lambda、std::function）

```cpp
class ThreadPool {
public:
    explicit ThreadPool(size_t numThreads);
    ~ThreadPool();

    template<typename F, typename... Args>
    auto submit(F&& f, Args&&... args) 
        -> std::future<decltype(f(args...))>;

    void shutdown();  // 等待所有任务完成

private:
    std::vector<std::thread> workers_;
    std::queue<std::function<void()>> tasks_;
    std::mutex queue_mutex_;
    std::condition_variable cv_;
    bool stop_ = false;
};
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 并发安全 | 35% | 任务队列的互斥保护、条件变量的正确使用 |
| 任务提交 | 25% | future/packaged_task、可变参数模板完美转发 |
| 生命周期 | 25% | 析构时正确 join、stop 标志的可见性 |
| 性能 | 15% | 避免虚假唤醒、减少锁竞争 |

---

## CP08：手写 LRU Cache

**难度**：⭐⭐  
**适合**：应届/社招  
**时间**：15-20 分钟

### 题目描述

实现 LRU(Least Recently Used) Cache，支持 O(1) 的 get 和 put：
1. `get(key)`：返回 value，并标记为最近使用。不存在返回 -1
2. `put(key, value)`：插入或更新。若容量满，淘汰最久未使用的

```cpp
class LRUCache {
public:
    explicit LRUCache(int capacity);

    int get(int key);
    void put(int key, int value);

private:
    int capacity_;
    std::list<std::pair<int, int>> list_;  // <key, value>
    std::unordered_map<int, std::list<std::pair<int, int>>::iterator> map_;
};
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 数据结构 | 40% | 双向链表 + 哈希表组合 |
| 算法正确性 | 30% | get/put O(1)、淘汰逻辑正确 |
| 边界情况 | 20% | 容量 1、重复 key、空 cache |
| 现代 C++ | 10% | 迭代器稳定性、splice 优化移动操作 |

---

## CP09：实现观察者模式

**难度**：⭐  
**适合**：实习/应届  
**时间**：10-15 分钟

### 题目描述

用现代 C++ 实现观察者模式：
1. Subject（主题）：维护观察者列表，`attach()`/`detach()`/`notify()`
2. Observer（观察者）：定义 `update()` 接口
3. 使用智能指针管理生命周期
4. 被观察者析构时自动通知观察者（得分项）

```cpp
class Observer {
public:
    virtual ~Observer() = default;
    virtual void update(const std::string& message) = 0;
};

class Subject {
public:
    void attach(std::shared_ptr<Observer> observer);
    void detach(std::shared_ptr<Observer> observer);
    void notify(const std::string& message);

private:
    std::vector<std::weak_ptr<Observer>> observers_;
};
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 设计模式 | 35% | 观察者模式结构正确 |
| 智能指针 | 35% | weak_ptr 避免循环引用、自动清理 |
| 解耦 | 20% | Subject 不依赖具体 Observer |
| 代码风格 | 10% | const 正确性、虚析构 |

---

## CP10：实现简单的 vector

**难度**：⭐⭐  
**适合**：应届  
**时间**：15-20 分钟

### 题目描述

实现简化版 `vector<T>`：
1. 动态扩容（2倍或 1.5 倍）
2. `push_back()`、`pop_back()`、`operator[]`、`size()`、`capacity()`
3. 拷贝构造、移动构造、拷贝赋值、移动赋值
4. 基本的迭代器（begin/end）
5. `emplace_back()`（加分项）

```cpp
template<typename T>
class MyVector {
public:
    MyVector();
    ~MyVector();

    void push_back(const T& value);
    void push_back(T&& value);
    void pop_back();
    T& operator[](size_t index);
    const T& operator[](size_t index) const;
    size_t size() const;
    size_t capacity() const;

    T* begin();
    T* end();

private:
    T* data_;           // 数据指针
    size_t size_;       // 当前元素数
    size_t capacity_;   // 当前容量
    // ...
};
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 动态扩容 | 30% | 扩容策略、重新分配+移动元素 |
| 移动语义 | 25% | push_back(T&&)、扩容时优先移动 |
| 异常安全 | 25% | 扩容失败不破坏原数据 |
| 迭代器 | 10% | begin/end 基本实现 |
| emplace | 10% | emplace_back 完美转发实现 |

---

## CP11：多线程交替打印

**难度**：⭐⭐  
**适合**：应届  
**时间**：10-15 分钟

### 题目描述

使用 C++ 多线程实现：
1. 两个线程交替打印奇偶数（1~100）
2. 两个线程交替打印字母和数字（A1B2C3...）

要求分别用 `std::mutex + condition_variable` 和 `std::atomic` 两种方式实现。

```cpp
// 交替打印奇偶数
// Thread 1: 1, 3, 5, ...
// Thread 2: 2, 4, 6, ...
// 最终输出：1 2 3 4 5 ... 100
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| mutex+CV 实现 | 35% | 条件变量使用正确、while 防止虚假唤醒 |
| atomic 实现 | 35% | 自旋等待、无锁实现 |
| 多方案对比 | 20% | 能分析两种方案性能差异和适用场景 |
| 代码规范 | 10% | 线程 join、无未定义行为 |

---

## CP12：环形缓冲区

**难度**：⭐⭐⭐  
**适合**：社招  
**时间**：20 分钟

### 题目描述

实现一个线程安全的环形缓冲区：
1. 固定容量，支持 push/pop
2. 线程安全（带锁版本 + 无锁版本，至少完成一种）
3. 支持批量读写（可选加分）

```cpp
template<typename T, size_t Capacity>
class RingBuffer {
public:
    bool push(const T& item);   // 生产者
    bool pop(T& item);          // 消费者
    bool full() const;
    bool empty() const;
    size_t size() const;

private:
    std::array<T, Capacity> buffer_;
    // ...
};
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 环形逻辑 | 30% | 读写指针管理、取模运算（或用2的幂简化） |
| 线程安全 | 35% | 互斥锁/原子操作选择、条件变量信号 |
| 性能 | 20% | false sharing 避免、锁粒度 |
| 边界 | 15% | 队列满拒绝、队列空阻塞、容量边界 |

---

## CP13：手写定时器

**难度**：⭐⭐  
**适合**：应届/社招  
**时间**：20-25 分钟

### 题目描述

实现一个高效的定时器管理器，支持：
1. `addTimer(delay_ms, callback)` 添加定时任务
2. `tick()` 触发到期任务执行
3. 至少实现基于**最小堆**的方案
4. 基于**时间轮**的方案（加分项）

```cpp
class TimerManager {
public:
    // 添加定时器，delay_ms 毫秒后执行 callback
    uint64_t addTimer(uint64_t delay_ms, std::function<void()> callback);
    // 取消定时器
    void cancelTimer(uint64_t timerId);
    // 驱动定时器，执行所有到期回调
    void tick();

private:
    struct Timer {
        uint64_t id;
        uint64_t expire_time;  // 毫秒时间戳
        std::function<void()> callback;

        bool operator>(const Timer& other) const {
            return expire_time > other.expire_time;
        }
    };
    std::priority_queue<Timer, std::vector<Timer>, std::greater<Timer>> heap_;
    // 时间轮：std::vector<std::list<Timer>> wheel_ + size_t current_slot_
};
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 堆实现 | 40% | 最小堆管理到期时间、O(logN)插入/O(1)取最小 |
| 时间轮 | 35% | slot 划分、指针移动、timer 可能跨轮 |
| 取消处理 | 15% | 惰性取消标记、共享状态管理 |
| 精度 | 10% | 毫秒级精度、tick 粒度讨论 |

---

## CP14：实现对象池

**难度**：⭐⭐  
**适合**：社招  
**时间**：15-20 分钟

### 题目描述

实现一个线程安全的对象池(Object Pool)：
1. 预创建若干对象供复用
2. `acquire()` 获取对象，`release()` 归还对象
3. 对象用完后自动归还（使用 RAII 包装）
4. 线程安全（加分项）

```cpp
template<typename T>
class ObjectPool {
public:
    explicit ObjectPool(size_t initialSize = 10);
    ~ObjectPool();

    // 获取一个对象（可能阻塞等待）
    std::shared_ptr<T> acquire();
    // 对象用完后通过自定义删除器自动归还

private:
    std::vector<std::unique_ptr<T>> pool_;
    std::queue<T*> available_;
    std::mutex mutex_;
    std::condition_variable cv_;
};
```

### 评分要点

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 对象重用 | 30% | 对象获取/归还逻辑正确 |
| RAII 封装 | 25% | shared_ptr 自定义删除器自动归还 |
| 线程安全 | 25% | 互斥锁/条件变量正确使用 |
| 扩展 | 20% | pool 耗尽时扩容、空闲回收 |

---

## CP15：LeetCode 算法题

作为编码题的补充，可从 LeetCode 中选题。
以下题目特别适合 C++ 面试，因为它们考察了 C++ 特有的数据结构或思维：

### 推荐 C++ 关联算法题

| 编号 | 题目 | 难度 | C++ 考察点 |
|------|------|------|-----------|
| 146 | LRU Cache | ⭐⭐ | list + unordered_map |
| 460 | LFU Cache | ⭐⭐⭐ | 数据结构组合 |
| 155 | Min Stack | ⭐ | 栈与辅助栈 |
| 232 | 用栈实现队列 | ⭐ | 两个栈 |
| 20 | 有效的括号 | ⭐ | stack |
| 215 | 数组第K大元素 | ⭐⭐ | 快排 partition / priority_queue |
| 239 | 滑动窗口最大值 | ⭐⭐⭐ | deque 单调队列 |
| 295 | 数据流中位数 | ⭐⭐⭐ | 两个堆 |
| 707 | 设计链表 | ⭐⭐ | 链表操作 |
| 622 | 设计循环队列 | ⭐⭐ | 环形缓冲区 |
| 200 | 岛屿数量 | ⭐⭐ | DFS/BFS |
| 21 | 合并两个有序链表 | ⭐ | 链表、递归 |
| 206 | 反转链表 | ⭐ | 链表 |
| 102 | 二叉树的层序遍历 | ⭐⭐ | BFS / queue |
| 470 | 用 Rand7() 实现 Rand10() | ⭐⭐ | 拒绝采样、概率 |

### 编码题评分通用标准

| 维度 | 权重 | 考察点 |
|------|------|--------|
| 算法正确性 | 40% | 核心逻辑正确、通过所有测试用例 |
| 边界与异常安全 | 25% | 空输入、溢出、资源泄漏、异常路径 |
| 时间复杂度分析 | 15% | 能准确分析并优化到最优方案 |
| C++ 特性运用 | 10% | 现代 C++ 特性、STL 合理使用 |
| 代码风格 | 10% | 命名规范、const正确性、RAII |
