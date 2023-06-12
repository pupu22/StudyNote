- 视频链接：[尚硅谷Nodejs教程](https://www.bilibili.com/video/BV1gM411W7ex?p=1&vd_source=c8b9ba4c470a783033f0287d1c7b102b)
- 参考笔记：[尚硅谷Nodejs笔记](https://gitee.com/river-ice/notes/tree/master/%E5%89%8D%E7%AB%AF/nodejs/%E5%A4%A7%E4%BD%AC)  

# node.js简介
[了解commonJS与node.js的关系](https://juejin.cn/post/7224393585247911992)


## 前言

Node 的重要性已经不言而喻，很多互联网公司都已经有大量的高性能系统运行在 Node 之上。Node 凭借其单线程、异步等举措实现了极高的性能基准。此外，目前最为流行的 Web 开发模式是前后端分离的形式，即前端开发者与后端开发者在自己喜欢的 IDE 上独立进行开发，然后通过 HTTP 或是 RPC 等方式实现数据与流程的交互。这种开发模式在 Node 的强大功能的引领下变得越来越高效，也越来越受到各个互联网公司的青睐。

### 前端同学为什么要学习后端/后端同学为什么要学习前端

*   了解前后端交互流程。
*   前端同学能够和后台开发的程序员更佳紧密地结合、更顺畅地沟通。
*   当网站的业务逻辑需要前置时，前端人员需要学习一些后台开发的技术，以完成相应的任务；；反过来也一样。
*   拓宽知识视野和技术栈，能够站在全局的角度审视整个项目。

### 前端同学为什么要学 Node.js

1、Node.js 使用 JavaScript 语言开发服务器端应用，**便于前端同学上手**（一些公司甚至要求前端工程师掌握 Node.js 开发）。

2、实现了前后端的语法统一，**有利于和前端代码整合**，甚至共用部分代码。

比如说，针对接口返回的各种字段，前后端都必须要做校验。此时，如果用 Node.js 来做后台开发的话，前后端可以共用校验的代码。

3、Node.js 性能高、生态系统活跃，提供了大量的开源库。

4、Jeff Atwood 在 2007 年提出了著名的 Atwood 定律：**任何能够用 JavaScript 实现的应用系统，最终都必将用 JavaScript 实现**。 Jeff Atwood 是谁不重要（他是 Stack Overflow 网站的联合创始人），重要的是这条定律。

## Node.js是什么？

### 官方定义

`Node.js` 是一个基于 **Chrome V8 引擎**的 JavaScript 运行环境。Node.js 使用了一个**事件驱动**、**非阻塞式 I/O**的模型，使其轻量又高效。Node.js 的包管理工具 npm 是全球最大的开源库生态系统。

Node.js 不是一门语言，也不是 JavaScript 的框架，也不是像Nginx一样的Web服务器 ，**Node.js 是 JavaScript 在服务器端的运行环境（平台）** 。

### Node.js 的组成

在 Node.js 里运行 JavaScript，跟在 Chrome 里运行 JavaScript 有什么不同？

二者采用的是同样的 JS 引擎。在 Node.js 里写 JS，和在前端写 JS，几乎没有不同。在写法上的区别在于：Node.js 没有浏览器、页面标签相关的 API，但是新增了一些 Node.js 相关的 API。通俗来说，对于开发者而言，在前端写 JS 是用于控制浏览器；而 Node.js 环境写 JS 可以控制整个计算机。

我们知道，JavaScript 的组成分为三个部分：

*   ECMAScript
*   DOM：标签元素相关的API
*   BOM：浏览器相关的API

ECMAScript 是 JS 的语法；DOM 和 BOM 浏览器端为 JS 提供的 API。

而 Node.js 的组成分为：

*   **ECMAScript**。ECMAScript 的所有语法在 Node 环境中都可以使用。
*   **Node 环境**提供的一些**附加 API**(包括文件、网络等相关的 API)。

![](https://cdn.jsdelivr.net/gh/pupu22/image/image/20230611214556.png)

