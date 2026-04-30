# source-reading-notes

一个持续更新的源码解读仓库。  
**现阶段会优先围绕 React 展开**，重点整理 React 主线机制相关的源码学习笔记、系列文章、结构图和源码截图。

如果想更系统地理解 React 源码，这个仓库会尽量把零散知识点收束到一条主线上：  
**JSX → ReactElement → Root / Fiber → Update → render → commit → Hooks**

后续也会逐步补充 Vue 以及其他值得系统梳理的源码专题，但当前仓库的核心重心，仍然是 **React 源码解读**。

> 持续更新的 React 源码解读仓库，围绕 React 主线机制整理系列文章、结构图与源码笔记。

---

## 这个仓库会放什么

这个仓库不是单纯存放 Markdown 文件的地方，而是一个围绕 **React 源码主线** 持续整理的源码解读仓库。

目前主要会整理这些内容：

- React 源码系列文章
- 关键主线结构图
- 关键源码截图与注释
- 便于复习和面试表达的主线总结

我会尽量把每个系列写成一组结构稳定、可连续阅读的文章，重点不是罗列知识点，而是把主线真正理清。

---

## 当前重点：React 源码主线拆解

目前仓库会优先更新 React 相关内容，重点关注这些问题：

- JSX 编译后到底产出了什么
- React 真正接收到的第一个核心对象是什么
- `createRoot` 和 `root.render` 到底做了什么
- Fiber 到底是什么，React 为什么需要 Fiber
- 一次更新是怎么进入系统的
- render / commit 分别做了什么
- Hooks 为什么必须按顺序调用

如果是第一次读 React 源码，也可以从这里顺着主线往下看。

---

## 当前目录结构

```text
source-reading-notes/
├─ react/               # React 源码解读系列
│  └─ articles/         # React 系列文章
├─ vue/                 # Vue 相关专题（后续逐步补充）
└─ assets/              # 仓库级公共资源
   └─ react/            # React 文章配图、源码截图
```

---

## 当前进度

- [x] 01 React 19 源码主线拆解：目录结构、包关系与运行时主线
- [x] 02 React 19 源码主线拆解：JSX 编译后为什么是 ReactElement？
- [x] 03 React 19 源码主线拆解：createRoot 和 root.render 到底做了什么？
- [x] 04 React 19 源码主线拆解：Fiber 到底是什么，React 为什么需要 Fiber？
- [ ] 05 React 19 源码主线拆解：一次更新是怎么进入系统的？
- [ ] 06 React 19 源码主线拆解：render 阶段做了什么？
- [ ] 07 React 19 源码主线拆解：commit 阶段如何更新 DOM 和执行副作用？
- [ ] 08 React 19 源码主线拆解：Hooks 内部原理

---

## React 系列文章

React 系列会围绕主线持续更新。  
现阶段的重点不是把所有细节一次性铺开，而是先把主干链路真正讲清楚。

已完成 / 持续更新中：

- [01 - React 19 源码主线拆解：目录结构、包关系与运行时主线](./react/articles/01-react-overview.md)
- [02 - React 19 源码主线拆解：JSX 编译后为什么是 ReactElement？](./react/articles/02-jsx-react-element.md)
- [03 - React 19 源码主线拆解：createRoot 和 root.render 到底做了什么？](./react/articles/03-createRoot-root-render.md)
- [04 - React 19 源码主线拆解：Fiber 到底是什么，React 为什么需要 Fiber？](./react/articles/04-fiber.md)

---

## 适合谁看

这个仓库更适合这几类读者：

- 想系统学习 React 源码的前端开发者
- 想把 React 原理讲清楚、用于面试表达的人
- 第一次进入 React 源码阅读，但不想一上来就陷进细节里的人

---

## 后续更新方向

当前阶段会继续把 React 这条主线往后补完整，包括：

- Update / Queue / Lane / Schedule
- render 阶段
- commit 阶段
- Hooks 内部原理

Vue 以及其他源码专题会在后续逐步补充，但不会影响当前仓库以 **React 源码解读** 为主的定位。

---

## 系列博客 

- 掘金专栏（持续更新）：
  [React19 源码主线拆解 系列博客](https://juejin.cn/column/7629539619139321865)

## 相关项目

如果你对 AI 应用工程化方向也感兴趣，我最近还在持续迭代一个 AI 项目：

**AI Mind**  
GitHub: https://github.com/HWYD/ai-mind

---

## Star 支持

如果这组内容对你有帮助，欢迎点个 Star。  
这会让我更有动力把这条 React 源码主线持续补完整。
