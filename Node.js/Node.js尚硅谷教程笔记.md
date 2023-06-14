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

### 小总结

-   Node 是一个服务器端 JavaScript 解释器
-   Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境
-   Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效
-   Node.js 的包管理器 npm，是全球最大的开源库生态系统
-   Node.js 是一门动态语言，运行在服务端的 Javascript

## Node.js 的应用

Node.js 拥有强大的开发者社区，现在已经发展出比较成熟的技术体系，以及庞大的生态。它被广泛地应用在 Web 服务、开发工作流、客户端应用等诸多领域。其中，在 **Web 服务**领域，业界对 Node.js 的接受程度最高。

###  BFF 中间层
BFF，即 Backend For Frontend（服务于前端的后端）。玉伯在《从前端技术进化到体验科技》这篇文章中点出了 BFF 层的概念：

> BFF 模式下，整体分工很清晰，**后端通过 Java/C++ 等语言负责服务实现，理想情况下给前端提供的是基于领域模型的 RPC 接口，前端则在 BFF 层直接调用服务端 RPC 接口拿到数据**，按需加工消费数据，并实现人机交互。基于 BFF 模式的研发，很适合拥有前端技术背景的全栈型工程师。这种模式的好处很明显，后端可以专注于业务领域，更多从领域模型的视角去思考问题，页面视角的数据则交给前端型全栈工程师去搞定。**领域模型与页面数据是两种思维模式，通过 BFF 可以很好地解耦开，让彼此更专业高效**。

在 Web 服务里，搭建一个中间层，前端访问中间层的接口，中间层再访问后台的 Java/C++ 服务。这类服务的特点是不需要太强的服务器运算能力，但对程序的灵活性有较高的要求。这两个特点，正好和 Node.js 的优势相吻合。Node.js 非常适合用来做 BFF 层，优势如下：

-   对于前端来说：让前端**有能力自由组装后台数据**，这样可以减少大量的业务沟通成本，加快业务的迭代速度；并且，前端同学能够**自主决定**与后台的通讯方式。
-   对于后台和运维来说，好处是：安全性（不会把主服务器暴露在外面）、降低主服务器的复杂度等。

###  服务端渲染

**客户端渲染**（CSR / Client side render）：前端通过一大堆接口请求数据，然后通过 JS 动态处理和生成页面结构和展示。优点是**前后端分离**、减小服务器压力、局部刷新。缺点是不利于 SEO（如果你的页面然后通过 Ajax 异步获取内容，抓取工具并不会等待异步完成后再行抓取页面内容）、首屏渲染慢。

**服务端渲染**（SSR / Server Side Render）：服务器返回的不是接口数据，而是一整个页面（或整个楼层）的 HTML 字符串，浏览器直接显示即可。也就是说，在服务器端直接就渲染好了，然后一次性打包返回给前端。优点是**有利于 SEO、首屏渲染很快**。

**总结： 搜索引擎优化 + 首屏速度优化 = 服务端渲染**。

备注：这里的「服务端渲染」只是让 Node.js 做中间层，不会替代后端的，后台同学请放心。
历史回顾：

（1）一开始，页面很简单，html 是后端渲染的（比如PHP、ASP、JSP等方式）。后端发现页面中的 js 好麻烦（虽然简单，但是坑多），于是让公司招聘专门写 js 的人，简称「前端切图仔」。

（2）随着 Node.js 和前端 MVC 的兴起，以及前端越来越复杂，慢慢演变成了「前后端分离」。

（3）前端的 SPA 应用流行之后，发现 SEO 问题很大，而且首屏渲染速度很慢，但是自己选的路再难走也要走下去，于是用 Node.js 在服务端渲染被看成是一条出路。

（4）以前在一起的时候，是后端做部分前端的工作；现在在一起的时候，是前端做部分后端的工作。

###  做小型服务、小型网站的后端（基于 Express、Koa 框架）

现在很多公司的后台管理系统，都是用 Node.js 来开发接口，毕竟，后台管理系统对性能和并发的要求不是太高。有了 Node.js 之后，通过 JS 直接操作 DB，做增删改查，生成接口，极大降低了前端同学的学习门槛。

当然，有时候做 Node.js 开发，是因为：后台人力不够，所以把后台开发的一部分工作量，转移给前端同学。
### 做项目构建工具

前端正在广泛使用的构建工具 gulp、Webpack，就是基于 Node.js 来实现的。

### 做 PC 客户端软件（基于 Electron 框架）

Electron 框架就是基于 Node.js 的，可以用来开发客户端软件。

Electron 原名为 Atom Shell，是由 GitHub 开发的一个开源框架。Electron 以 Node.js 作为运行时（runtime），以 chromium 作为渲染引擎，使开发者可以使用 JS 这种前端技术栈开来发跨平台的桌面GUI应用程序。

有一点你可能会感到惊讶：程序员们都在用的代码编辑器 VS Code 软件， 就是基于 Electron 框架来开发的。其他使用 Electron 进行开发的知名应用还有：Skype、GitHub Desktop、Slack、WhatsApp等。


### 知名度较高的 Node.js 开源项目
-   express：Node.js 中著名的 web 服务框架。
-   Koa：下一代的 Node.js 的 Web 服务框架。所谓的“下一代”是相对于 Express 而言的。
-   Egg：2016 年，阿里巴巴研发了知名的 Egg.js 开源项目，号称企业级 Web 服务框架。Egg.js 是基于 Koa 开发的。
-   mocha：是现在最流行的 JavaScript 测试框架，在浏览器和 Node 环境都可以使用。
-   PM2：node 多进程管理。
-   jade：非常优秀的模板引擎，不仅限于 js 语言。
-   CoffeeScript：用简洁的方式展示 JavaScript 优秀的部分。
-   Atom：编辑器。
-   VS Code：最酷炫的编辑器。
-   socket.io：实时通信框架

### 总结

或许，能用 Node.js 做的后台应用，Java/C++ 也能做；但是 Node.js 可以让我们多一种选择。

短期来看，Node.js 很难像 Java/C++ 那样，成为后台的主力开发语言。这并非是因为 Node.js 的性能问题，主要是因为，Node.js 还比较年轻，经验积累太少，框架的支持度不够。搞企业级服务，Node.js 敌不过 Java/C++，所以目前只能搞「轻量级」；但未来可期。

限制语言能力的不是语言本身，而是生态。

##  Node.js 的特点

-   异步、非阻塞 IO 模型
-   事件循环
-   单线程
-   总结：轻量和高效

Node.js 的性能和效率非常高。

传统的 Java 语言是一个请求开启一个线程，当请求处理完毕后就关闭这个线程。而 Node.js 则完全没有采用这种模型，它本质上就是一个单线程。

你可能会疑问：一个线程如何服务于大量的请求、如何处理高并发的呢？这是因为，Node.js 采用的是异步的、非阻塞的模型。

这里所谓的“单线程”，指的是 Node 的主线程只有一个。为了确保主线程不被阻塞，主线程是用于接收客户端请求。但不会处理具体的任务。而 Node 的背后还有一个线程池，线程池会处理长时间运行的任务（比如 IO 操作、网络操作）。线程池里的任务是通过队列和事件循环的机制来执行。

##  使用 Node.js 时的劣势

-   程序运行不稳定，可能会出现服务不可用的情况
-   程序运行效率较低，每秒的请求数维持在一个较低的水平
-   前端同学对服务器端的技术不太熟悉。
# 【npm的使用】

##  包和npm

###  什么是包

由于 Node 是一套轻内核的平台，虽然提供了一系列的内置模块，但是不足以满足开发者的需求，于是乎出现了包（package）的概念： 与核心模块类似，就是将一些预先设计好的功能或者说 API 封装到一个文件夹，提供给开发者使用。

Node 本身并没有太多的功能性 API，所以市面上涌现出大量的第三方人员开发出来的 Package。
### 包的加载机制

Node.js中使用`CommonJs`模块化机制，通过`npm`下载的第三方包，我们在项目中引入第三方包都是：`let xx = require('第三方包名')`，究竟`require`方法加载第三方包的原理机制是什么，今天我们来探讨下。

1.  `require('第三方包名')`优先在加载该包的模块的同级目录`node_modules`中查找第三方包。
1.  找到该第三方包中的`package.json`文件，并且找到里面的`main`属性对应的入口模块，该入口模块即为加载的第三方模块。
1.  如果在要加载的第三方包中没有找到`package.json`文件或者是`package.json`文件中没有`main`属性，则默认加载第三方包中的`index.js`文件。
1.  如果在加载第三方模块的文件的同级目录没有找到`node_modules`文件夹，或者以上所有情况都没有找到，则会向上一级父级目录下查找`node_modules`文件夹，查找规则如上一致。
1.  如果一直找到该模块的磁盘根路径都没有找到，则会报错：`can not find module xxx`。

### npm 的概念

**NPM**：Node Package Manager。官方链接： https://www.npmjs.com/

Node.js 发展到现在，已经形成了一个非常庞大的生态圈。包的生态圈一旦繁荣起来，就必须有工具去来管理这些包。NPM 应运而生。

举个例子，当我们在使用 Java 语言做开发时，需要用到 JDK 提供的内置库，以及第三方库。同样，在使用 JS 做开发时，我们可以使用 NPM 包管理器，方便地使用成熟的、优秀的第三方框架，融合到我们自己的项目中，极大地加速日常开发的构建过程。

随着时间的发展，NPM 出现了两层概念：

-   一层含义是 Node 的开放式模块登记和管理系统，亦可以说是一个生态圈，一个社区。
-   另一层含义是 Node 默认的模块管理器，是一个命令行下的软件，用来安装和管理 Node 模块。

### npm 的安装（不需要单独安装）

NPM 不需要单独安装。默认在安装 Node 的时候，会连带一起安装 NPM

## npm命令总结

```
1.npm init -y 添加初始化文件记录安装信息，如果在后面加-S或者-D会自动创建该文件

2.npm install 包名 –g  （uninstall,update）

3.npm install 包名 --save（-S） --dev(-D)  (uninstall,update)
如果不写后缀默认是安装到生产环境
如果先装到了开发环境，那么后面覆盖安装不写后缀也是本身的环境下
一个包只能存在在一种环境，得先卸载才能换环境

4.npm list -g (不加-g，列举当前目录下的安装包)

5.npm info 包名（详细信息） npm info 包名 version (获取最新版本)

6.npm install md5@1.8.0（安装指定版本）

7.npm outdated(检查包是否已经过时)
如果版本比较新就不会有输出

8.pwd输出当前目录的绝对路径

9.npm view 包名 version查看当前版本   npm view 包名 versions查看该包所有版本

10.npm update 包名 更新指定包 npm update 更新所有的包（pnpm up）

11.npm config list  查看npm配置信息

12.npm 指定命令 --help 查看指定命令的帮助。

13.npm root：查看当前包的安装路径。  npm root -g：查看全局的包的安装路径。

14.npm ls 包名：查看本地安装的指定包及版本信息，没有显示empty。 npm ls 包名 -g：查看全局安装的指定包及版本信息

15.npm cache clean --force 清除缓存

16.npm -v查看npm的版本


"dependencies": {    "md5": "^2.1.0"  }  ^ 表示 如果 直接npm install 将会 安md5@2.*.*  	最新版本

"dependencies": {    "md5": "~2.1.0"  }  ~ 表示 如果 直接npm install 将会 安装md5 2.1.*  最新版本

"dependencies": {    "md5": "*"  }  * 表示 如果 直接npm install 将会 安装 md5  最新版本
```
## pnpm

### [](https://gitee.com/river-ice/notes/blob/master/%E5%89%8D%E7%AB%AF/nodejs/%E5%A4%A7%E4%BD%AC/03%20%E3%80%90npm%E7%9A%84%E4%BD%BF%E7%94%A8%E3%80%91.md#51-pnpm-%E6%98%AF%E4%BB%80%E4%B9%88)5.1 pnpm 是什么

> pnpm是 Node.js 的替代包管理器。它是 npm 的直接替代品，但速度更快、效率更高。

> 为什么效率更高？当您安装软件包时，我们会将其保存在您机器上的全局存储中，然后我们会从中创建一个硬链接，而不是进行复制。对于模块的每个版本，磁盘上只保留一个副本。例如，当使用 npm 或 yarn 时，如果您有 100 个使用 lodash 的包，则磁盘上将有 100 个 lodash 副本。pnpm 可让您节省数 GB 的磁盘空间！

pnpm优势 pnpm 拥有 Yarn 超过 npm 的所有附加功能：

-   **安全**: 与 yarn 一样，pnpm 有一个包含所有已安装包校验和的特殊文件，用于在执行代码之前验证每个已安装包的完整性。
-   **离线模式**: pnpm 将所有下载的包 tarball 保存在本地注册表镜像中。当包在本地可用时，它从不发出请求。使用该--offline参数可以完全禁止 HTTP 请求。
-   **速度**: pnpm 不仅比 npm 快，而且比 yarn 快。无论是冷缓存还是热缓存，它都比 yarn 快。yarn 从缓存中复制文件，而 pnpm 只是从全局存储中链接它们。

### [](https://gitee.com/river-ice/notes/blob/master/%E5%89%8D%E7%AB%AF/nodejs/%E5%A4%A7%E4%BD%AC/03%20%E3%80%90npm%E7%9A%84%E4%BD%BF%E7%94%A8%E3%80%91.md#pnpm-%E7%9A%84%E4%BD%BF%E7%94%A8)pnpm 的使用

**官网**： `https://pnpm.js.org/installation/`

**全局安装**

```
npm install pnpm -g
```

**设置源**

```
//查看源
pnpm config get registry 
//切换淘宝源
pnpm config set registry https://registry.npmmirror.com/
```

**使用**

```
//可以和npm一样使用方式

pnpm init //直接初始化
pnpm install 包  // 
pnpm i 包
pnpm add 包    // -S  默认写入dependencies
pnpm add -D    // -D devDependencies
pnpm add -g    // 全局安装
```

**移除**

```
pnpm remove(uninstall) 包                            //移除包
pnpm remove 包 --global                   //移除全局包
```

**更新**

```
pnpm up                //更新所有依赖项
pnpm upgrade 包        //更新包
pnpm upgrade 包 --global   //更新全局包
pnpm up --latest //最新更新所有依赖项，忽略package.json中指定的范围
```
