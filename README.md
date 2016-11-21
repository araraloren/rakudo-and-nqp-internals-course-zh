# Rakudo 和 NQP 内部研讨会

## 这儿有什么?

该仓库包含了关于 Rakudo 和 NQP 内部研讨会的课程材料。 在这里你会发现：

* 原始源码 (下面有构建说明)
* [Pre-built PDFs](http://edumentab.github.io/rakudo-and-nqp-internals-course/)

## 摘要

这个密集的为期两天的研讨会深入探讨了 Rakudo Perl 6 和 NQP 内部的许多领域，主要集中在后端不可知的部分，但有一些涵盖了 JVM 和未来 MoarVM 后端的东西。 在课程中，参与者将构建他们自己的小编译器，连同一个简单的基于类的对象系统，以帮助他们了解工具链的工作原理。

### 预备知识

对 Perl 6 语言有一定的了解，并且最好还有使用 NQP 的经验。

### 第一天

#### 全局预览：编译器和 NQP/Rakudo 架构

* 编译器做什么
* 运行时做什么
* Perl 6 的挑战
* NQP 作为语言
* NQP 作为编译器构建工具链
* QAST
* nqp::op 集合
* 自举简单介绍
* Rakudo 如何使用 NQP

#### NQP 语言

* 设计目标
* 字面值, 变量, 控制流
* 子例程, pointy blocks, 闭包语义
* 类, 属性, 方法
* 正则表达式和 grammars
* Roles
* 多重分派
* 内建方法和 nqp::ops
* 异常处理
* 限制和与完整 Perl 6 的其它差异
* 缺点

#### 编译流水线

* HLL::Compiler 类
* 前端, 后端和它们之间的 QAST
* 用 grammars 解析, 用 actions 构建 AST
* 代码生成
* 从头开始构建一个微小的语言

#### QAST

* QAST::Node, 这一切的基础
* AST 的总体结构
* 字面值: QAST::IVal, QAST::NVal 和 QAST::SVal
* 运算: QAST::Op, 基本的例子
* 序列: QAST::Stmts, QAST::Stmt
* 变量: QAST::Var, QAST::VarWithFallback, scope, decl, value
* block 符号表
* 调用
* 形参和实参
* 上下文化: QAST::Want
* Block 引用: QAST::BVal
* 对象引用: QAST::WVal
* The backend escape hatch: QAST::VM
* 在顶部: QAST::CompUnit

#### 探索 nqp:: ops

* 计算
* 关系
* 聚集
* 字符串
* 流程控制
* 异常相关
* 上下文自省
* 大整数

### 第二天

#### 6model

* 对象: 行为 + 状态
* 类型和种类
* 元对象
* Representations
* STables
* 知其所以然, 这一切的根本
* 从头开始构建一个简单的对象系统
* 使用 World 类为我们的小语言添加对象
* 方法缓存
* 类型检查
* （布尔化）Boolification
* 调用
* 探索 NQP 的元对象
* 探索 Rakudo 的元对象
* 容器处理

#### 有界序列化和模块加载

* 编译时/运行时边界
* 序列化上下文
* 重访 QAST::WVal
* 什么是"有界的"
* Repossession, 冲突和其它令人讨厌的东西
* 与序列化上下文相关的 nqp:: ops
* 重访 World 类
* 模块加载的工作原理

#### 正则表达式和 grammar 引擎

* QAST::Regex 节点和它的子类型
* 游标 和 匹配
* bstack 和 cstack
* NFAs 和 最长令牌匹配（Longest Token Matching）

#### JVM 后端

* JVM 概述
* QAST 到 JAST 的翻译
* 运行时支持库

#### MoarVM 后端

* MoarVM 概述
* QAST 到 MAST 的翻译

## 构建说明

运行 `Makefile` 来构建这两天的幻灯片。 为此，您需要：

* 一个 `make` 程序 (Windows 上的 `nmake` 也能很好地工作)
* Perl 5.10 或以上
* Pandoc (参见 http://johnmacfarlane.net/pandoc/)
* 你的 path 路径中有 `latex`, `dvips` 和 `ps2pdf` 命令

在 Linux 上，您可以执行以下操作：

    apt-get install texlive
    apt-get install pandoc

在 Windows 上，有一个上面提到的 URL 中的 Pandoc 安装程序，然后安装 MiKTeX 的其他命令。

## 课程发行

本课程资料由 Edument AB 根据知识共享许可证（见LICENSE文件）提供，以支持 Perl 6 开发社区。 但是，这是最好的现场经验！ 如果您有兴趣在您选择的地方由有经验的讲师发行这种材料，请随时通过 info@edument.se 与我们联系。 要了解更多关于Edument和我们的其他令人惊叹的课程，请参阅 http://edument.se/。
