# React 源码解读

这里是 React 源码解读系列，主要围绕 **React 19 主线机制** 展开。

这组文章不会一上来就扎进特别碎的实现细节，而会尽量沿着一条稳定主线往里拆：先把整体地图搭起来，再进入具体问题。这样做的目的很简单——第一次读 React 源码时，我们最容易卡住的地方，往往不是某个函数本身，而是看着看着就失去了方向。

所以这组文章会尽量做两件事：

- 帮我们先把 React 源码里的主线理顺
- 让后面继续往里读的时候，心里始终有一张总图

## 这组文章主要在讲什么

当前这组 React 文章，核心会围绕这些问题展开：

- JSX 编译后到底是什么
- React 真正接收到的第一个核心对象是什么
- `createRoot(container)` 到底创建了什么
- `root.render(<App />)` 做了什么
- Fiber 为什么存在，它和 ReactElement、DOM 分别是什么关系
- 一次更新是怎么从 `setState` / Hook dispatch 进入系统的
- render 阶段和 commit 阶段分别在做什么
- Hooks 为什么必须按顺序调用

如果我们把这些问题串起来，React 源码就不再只是一些零散名词，而会慢慢变成一条完整的更新链路。

## 建议怎么读

如果是第一次系统读 React 源码，我更建议按下面这个顺序往下看：

### 1. 先看整体地图
先把 React 到底是一套什么系统看清楚，知道 JSX、ReactElement、Root/Fiber、调度、render、commit 大概是怎么串起来的。

- [01 React 19 源码怎么读：目录结构、包关系、调试方式与主线问题](./articles/01-React-19-源码怎么读.md)

### 2. 再看 React 真正接收到的输入是什么
很多后面的理解，都建立在这一层之上。

- [02 JSX 到 ReactElement](./articles/02-JSX-到-ReactElement.md)

### 3. 再进入应用启动和 Root 初始化
看 React 应用是怎么从 `createRoot` 开始真正接入更新系统的。

- [03 createRoot 与 root.render](./articles/03-createRoot-与-root-render.md)

### 4. 然后看 Fiber 这层核心结构
这一步会帮助我们把很多抽象词真正落到一个具体的数据结构上。

- [04 Fiber 到底是什么](./articles/04-Fiber-到底是什么.md)

### 5. 接着看一次更新是怎么进入系统的
也就是从 `setState` / Hook dispatch 到调度入口这一段。

- [05 从 setState 到调度](./articles/05-从-setState-到调度.md)

### 6. 再看 render 阶段
这里重点是：React 到底是怎么“算”出下一次提交结果的。

- [06 render 阶段做了什么](./articles/06-render-阶段做了什么.md)

### 7. 然后看 commit 阶段
这里重点是：DOM 和 effect 到底在什么时机真正执行。

- [07 commit 阶段做了什么](./articles/07-commit-阶段做了什么.md)

### 8. 最后再看 Hooks 内部原理
前面的主线立住之后，Hooks 这部分会更容易真正看懂。

- [08 Hooks 内部原理](./articles/08-Hooks-内部原理.md)

## 如果是第一次读 React 源码，可以先记住什么

如果现在还没有真正开始往里看，只想先有一个大概印象，那我觉得可以先记住这几件事：

1. React 不是“收到 JSX 就直接改 DOM”的黑盒  
2. JSX 只是输入形式，React 运行时真正处理的是编译后的对象描述  
3. React 内部有自己的更新系统，Root、Fiber、调度、render、commit 都是这套系统的一部分  
4. render 和 commit 不是一回事：一个更偏计算，一个更偏提交  
5. 后面很多源码细节，其实都可以挂到这条主线上理解

只要这几件事先有了印象，后面继续往里读，节奏会顺很多。

## 版本口径

这一组文章整体讨论的是 **React 19 主线机制**。  
如果涉及具体源码观察，我会在单篇文章开头说明当前参考的源码基线版本，例如 `19.1.1`。

## 这组文章适合谁

- 想系统补 React 原理的前端开发者
- 想把 React 源码主线梳理清楚的人
- 想把源码理解进一步转成面试表达的人

## 相关项目

如果你对 AI 应用工程化方向也感兴趣，我最近还在持续迭代一个 AI 项目：

**AI Mind**  
GitHub: https://github.com/HWYD/ai-mind