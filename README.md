# C++ 后端面试模拟器

模拟中国大厂（字节、腾讯、阿里、美团、快手）C++ 后端开发技术面试的 Claude Code Skill。

## 功能

- 支持四种求职者身份：找实习 / 找暑期实习 / 应届校招 / 社招1-3年
- 六种面试官风格：严厉拷打型 / 温和鼓励型 / 专业高效型 / 深挖学术型 / 工程实践型 / 综合平衡型
- 可选的编码题环节（C++ 高频手写题）
- 简历解析与追问链预判
- 目标岗位 JD 匹配分析
- 详细的评分报告与个性化反馈

## 使用方式

在 Claude Code 中输入以下触发词：
- "开始面试" / "模拟面试" / "练习面试"
- "C++面试" / "后端面试"
- "帮我准备面试"

## 技术考察范围

- C++ 语言基础（虚函数、RAII、移动语义、模板）
- STL 标准库（容器、算法、配置器）
- 并发编程（线程、原子操作、无锁编程）
- Linux 系统编程（进程/线程、内存管理、文件IO）
- 网络编程（TCP/IP、epoll、高性能服务框架）
- 编译调试（编译链接过程、GDB、perf）
- MySQL / Redis / 消息队列
- 分布式系统设计
- 性能优化（CPU/内存/系统级）

## 结构

```
cpp-backend-interview-simulator/
├── SKILL.md                              # 主 Skill 文件
├── README.md
└── references/
    ├── interviewer-styles.md             # 面试官风格指南
    ├── tech-knowledge-base.md            # C++ 后端技术知识库
    ├── evaluation-rubric.md              # 评分标准与反馈模板
    ├── coding-challenges.md              # C++ 编码题题库
    ├── ai-dev-knowledge-base.md          # AI 开发知识库
    └── ai-dev-tools-knowledge-base.md    # AI 开发工具知识库
```

## 许可证

MIT
