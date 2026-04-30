# React 源码解读

这里是 React 源码解读系列，主要围绕 **React 19 主线机制** 展开。

这组文章不会一上来就扎进特别碎的实现细节，而会尽量沿着一条稳定主线往里拆：先把整体地图搭起来，再进入具体问题。这样做的目的很简单——第一次读 React 源码时，我们最容易卡住的地方，往往不是某个函数本身，而是看着看着就失去了方向。

所以这组文章会尽量做两件事：

- 帮我们先把 React 源码里的主线理顺
- 让后面继续往里读的时候，心里始终有一张总图

---

## 当前主线

如果把这组文章串起来，React 源码主线大致可以先理解成：

**JSX → ReactElement → Root / Fiber → Update → render → commit → Hooks**

这不是一条完整到所有细节的源码调用链，而是一条适合第一次系统阅读 React 源码时使用的理解主线。

---

## 系列文章

已完成 / 持续更新中：

- [01 - React 19 源码主线拆解：目录结构、包关系与运行时主线](./articles/01-react-overview.md)
- [02 - React 19 源码主线拆解：JSX 编译后为什么是 ReactElement？](./articles/02-jsx-react-element.md)
- [03 - React 19 源码主线拆解：createRoot 和 root.render 到底做了什么？](./articles/03-createRoot-root-render.md)
- [04 - React 19 源码主线拆解：Fiber 到底是什么，React 为什么需要 Fiber？](./articles/04-fiber.md)

---

## 建议怎么读

如果是第一次系统读 React 源码，我更建议按下面这个顺序往下看。

### 1. 先看整体地图

先把 React 到底是一套什么系统看清楚，知道 JSX、ReactElement、Root / Fiber、调度、render、commit 大概是怎么串起来的。

- [01 - React 19 源码主线拆解：目录结构、包关系与运行时主线](./articles/01-react-overview.md)

### 2. 再看 React 真正接收到的输入是什么

很多后面的理解，都建立在这一层之上。  
JSX 不会原样进入 React 运行时，React 真正接收到的第一层核心对象是 ReactElement。

- [02 - React 19 源码主线拆解：JSX 编译后为什么是 ReactElement？](./articles/02-jsx-react-element.md)

### 3. 再进入应用启动和 Root 初始化

看 React 应用是怎么从 `createRoot` 开始接入更新系统的，以及 `root.render(element)` 如何把 ReactElement 包装成一次根更新。

- [03 - React 19 源码主线拆解：createRoot 和 root.render 到底做了什么？](./articles/03-createRoot-root-render.md)

### 4. 然后看 Fiber 这层核心结构

这一步会帮助我们把很多抽象词真正落到一个具体的数据结构上：Fiber 不是 ReactElement 的别名，而是 React 运行时的工作节点。

- [04 - React 19 源码主线拆解：Fiber 到底是什么，React 为什么需要 Fiber？](./articles/04-fiber.md)

### 5. 接着看一次更新是怎么进入系统的

也就是从 `setState` / Hook dispatch 到 Update、Queue、Lane、Schedule 这一段。

- 05 - React 19 源码主线拆解：一次更新是怎么进入系统的？（待更新）

### 6. 再看 render 阶段

这里重点是：React 到底是怎么“算”出下一次提交结果的。

- 06 - React 19 源码主线拆解：render 阶段做了什么？（待更新）

### 7. 然后看 commit 阶段

这里重点是：DOM 和 effect 到底在什么时机真正执行。

- 07 - React 19 源码主线拆解：commit 阶段如何更新 DOM 和执行副作用？（待更新）

### 8. 最后再看 Hooks 内部原理

前面的主线立住之后，Hooks 这部分会更容易真正看懂。

- 08 - React 19 源码主线拆解：Hooks 内部原理（待更新）

---

## 当前进度

- [x] 整体地图
- [x] JSX → ReactElement
- [x] createRoot / root.render
- [x] Fiber
- [ ] Update / Queue / Lane / Schedule
- [ ] render 阶段
- [ ] commit 阶段
- [ ] Hooks 内部原理

---

## 如果是第一次读 React 源码，可以先记住什么

如果现在还没有真正开始往里看，只想先有一个大概印象，那我觉得可以先记住这几件事：

1. React 不是“收到 JSX 就直接改 DOM”的黑盒  
2. JSX 只是输入形式，React 运行时真正处理的是编译后的对象描述  
3. ReactElement 是输入描述，Fiber 是运行时工作节点  
4. React 内部有自己的更新系统，Root、Fiber、Update、调度、render、commit 都是这套系统的一部分  
5. render 和 commit 不是一回事：一个更偏计算，一个更偏提交  
6. 后面很多源码细节，其实都可以挂到这条主线上理解

只要这几件事先有了印象，后面继续往里读，节奏会顺很多。

---

## 版本口径

这一组文章整体讨论的是 **React 19 主线机制**。  
如果涉及具体源码观察，我会在单篇文章开头说明当前参考的源码基线版本，例如 `19.1.1`。

---

## 这组文章适合谁

- 想系统补 React 原理的前端开发者
- 想把 React 源码主线梳理清楚的人
- 想把源码理解进一步转成面试表达的人

---

## 系列博客 

- 掘金专栏（持续更新）：
  [React19 源码主线拆解 系列博客](https://juejin.cn/column/7629539619139321865)

## 相关项目

如果你对 AI 应用工程化方向也感兴趣，我最近还在持续迭代一个 AI 项目：

**AI Mind**  
GitHub: https://github.com/HWYD/ai-mind
