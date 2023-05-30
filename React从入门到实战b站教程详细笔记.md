视频： [React入门到实战(2022全网最新](https://www.bilibili.com/video/BV1Z44y1K7Fj/?spm_id_from=333.1007.top_right_bar_window_history.content.click\&vd_source=c8b9ba4c470a783033f0287d1c7b102b)

笔记[ 语雀](https://www.yuque.com/fechaichai/qeamqf)

> 说个题外话\
> 这个视频作者提供了语雀上面的文档，但是我需要markdown格式的笔记，因此花了两个小时研究怎么把网页里面的内容转换为markdown格式，尝试了cubox+ copy as markdown 以及印象笔记，还有各种将html文件转换为markdown的工具，最后发现复制到掘金里面就可以转换格式，太离谱了。

# React介绍

`目标任务:`  了解什么是React以及它的特点

**React是什么**

    一个专注于构建用户界面的 JavaScript 库，和vue和angular并称前端三大框架，不夸张的说，react引领了很多新思想，世界范围内是最流行的js前端框架，最新版本已经到了18，加入了许多很棒的新特性

React英文文档（<https://reactjs.org/）>

React中文文档 （<https://zh-hans.reactjs.org/）>

React新文档（<https://beta.reactjs.org/）（开发中....）>

**React有什么特点**

1- 声明式UI（JSX）

写UI就和写普通的HTML一样，抛弃命令式的繁琐实现

2- 组件化

组件是react中最重要的内容，组件可以通过搭积木的方式拼成一个完整的页面，通过组件的抽象可以增加复用能力和提高可维护性

3- 跨平台

react既可以开发web应用也可以使用同样的语法开发原生应用（react-native），比如安卓和ios应用，甚至可以使用react开发VR应用，想象力空间十足，react更像是一个 `元框架`  为各种领域赋能

# JSX基础

## 1. JSX介绍

`目标任务:`   能够理解什么是JSX，JSX的底层是什么

概念：JSX是 JavaScript XML（HTML）的缩写，表示在 JS 代码中书写 HTML 结构

作用：在React中创建HTML结构（页面UI结构）

优势：

1.  采用类似于HTML的语法，降低学习成本，会HTML就会JSX
2.  充分利用JS自身的可编程能力创建HTML结构

注意：JSX 并不是标准的 JS 语法，是 JS 的语法扩展，浏览器默认是不识别的，脚手架中内置的 [@babel/plugin-transform-react-jsx](@babel/plugin-transform-react-jsx) 包，用来解析该语法

## 2. JSX中使用js表达式

`目标任务:`   能够在JSX中使用表达式

**语法**
`{ JS 表达式 }`

```javascript
const name = '柴柴'

<h1> 你好，我叫{name} </h1>   //    <h1>你好,我叫柴柴</h1>
```

**可以使用的表达式**

1.  字符串、数值、布尔值、null、undefined、object（ \[] / {} ）
2.  1 + 2、'abc'.split('')、\['a', 'b'].join('-')
3.  fn()

**特别注意**

> if 语句/ switch-case 语句/ 变量声明语句，这些叫做语句，不是表达式，不能出现在 `{}` 中！！

## 3. JSX列表渲染

`目标任务:`   能够在JSX中实现列表渲染

> 页面的构建离不开重复的列表结构，比如歌曲列表，商品列表等，我们知道vue中用的是v-for，react这边如何实现呢？

实现：使用数组的`map` 方法

```js
// 来个列表
const songs = [
  { id: 1, name: '痴心绝对' },
  { id: 2, name: '像我这样的人' },
  { id: 3, name: '南山南' }
]
function App() {
  return (
    <div className="App">
      <ul>
        {
          songs.map(item => <li>{item.name}</li>)
        }
      </ul>
    </div>
  )
}
export default App
```

注意点：需要为遍历项添加 `key` 属性

1.  key 在 HTML 结构中是看不到的，是 React 内部用来进行性能优化时使用
2.  key 在当前列表中要唯一的字符串或者数值（String/Number）
3.  如果列表中有像 id 这种的唯一值，就用 id 来作为 key 值
4.  如果列表中没有像 id 这种的唯一值，就可以使用 index（下标）来作为 key 值

## 4. JSX条件渲染

`目标任务:`   能够在JSX中实现条件渲染

作用：根据是否满足条件生成HTML结构，比如Loading效果

实现：可以使用 `三元运算符` 或   `逻辑与(&&)运算符`

```js
// 来个布尔值
const flag = true
function App() {
  return (
    <div className="App">
      {/* 条件渲染字符串 */}
      {flag ? 'react真有趣' : 'vue真有趣'}
      {/* 条件渲染标签/组件 */}
      {flag ? <span>this is span</span> : null}
      
      {true && <span>this is span</span>} //显示
      {false && <span>this is span</span>} //不显示
    </div>
  )
}
export default App
```

## 5. JSX样式处理

`目标任务:`   能够在JSX中实现css样式处理

*   行内样式 - style

```jsx
function App() {
  return (
    <div className="App">
      <div style={{ color: 'red' }}>this is a div</div>
    </div>
  )
}
export default App
```

*   行内样式 - style - 更优写法

```js
const styleObj = {
    color:red
}

function App() {
  return (
    <div className="App">
      <div style={ styleObj }>this is a div</div>
    </div>
  )
}
export default App
```

*   类名 - className（推荐）

```app.css
.title {
  font-size: 30px;
  color: blue;
}
```

*   类名 - className - 动态类名控制

```app.js
import './app.css'
const showTitle = true
function App() {
  return (
    <div className="App">
      <div className={ showTitle ? 'title' : ''}>this is a div</div>
    </div>
  )
}
export default App
```

## 6. JSX注意事项

`目标任务:`   掌握JSX在实际应用时的注意事项

1.  JSX必须有一个根节点，如果没有根节点，可以使用`<></>`（幽灵节点）替代
2.  所有标签必须形成闭合，成对闭合或者自闭合都可以
3.  JSX中的语法更加贴近JS语法，属性名采用驼峰命名法  `class -> className`  `for -> htmlFor`
4.  JSX支持多行（换行），如果需要换行，需使用`()` 包裹，防止bug出现

## 格式化配置

`目标任务:`   基于vscode配置格式化工具，提高开发效率

1.  安装vsCode prettier插件
2.  修改配置文件 `setting.json`

## 阶段小练习

练习说明

1.  拉取准备好的项目模块到本地 ，安装依赖，run起来项目\
    <https://gitee.com/react-course-series/react-jsx-demo>
2.  按照图示，完成 `评论数据渲染`  `tab内容渲染`  `评论列表点赞和点踩`  三个视图渲染

# React组件基础

## 组件概念

## 函数组件

**概念**

使用 JS 的函数（或箭头函数）创建的组件，就叫做`函数组件`

**组件定义与渲染**

```js
// 定义函数组件
function HelloFn () {
  return <div>这是我的第一个函数组件!</div>
}

function App () {
  return (
    <div className="App">
      {/* 渲染函数组件 */}
      <HelloFn />
      <HelloFn></HelloFn>
    </div>
  )
}
export default App
```

**约定说明**

1.  组件的名称**必须首字母大写**，react内部会根据这个来判断是组件还是普通的HTML标签
2.  函数组件**必须有返回值**，表示该组件的 UI 结构；如果不需要渲染任何内容，则返回 null
3.  组件就像 HTML 标签一样可以被渲染到页面中。组件表示的是一段结构内容，对于函数组件来说，渲染的内容是函数的**返回值**就是对应的内容
4.  使用函数名称作为组件标签名称，可以成对出现也可以自闭合

## 类组件

`目标任务:`   能够独立完成类组件的创建和渲染

使用 ES6 的 class 创建的组件，叫做类（class）组件

**组件定义与渲染**

```js
// 引入React
import React from 'react'

// 定义类组件
class HelloC extends React.Component {
  render () {
    return <div>这是我的第一个类组件!</div>
  }
}

function App () {
  return (
    <div className="App">
      {/* 渲染类组件 */}
      <HelloC />
      <HelloC></HelloC>
    </div>
  )
}
export default App
```

**约定说明**

1.  **类名称也必须以大写字母开头**
2.  类组件应该继承 React.Component 父类，从而使用父类中提供的方法或属性
3.  类组件必须提供 render 方法**render 方法必须有返回值，表示该组件的 UI 结构**

## 函数组件的事件绑定

`目标任务:`   能够独立绑定任何事件并能获取到事件对象e

### 1. 如何绑定事件

*   语法\
    on + 事件名称 = { 事件处理程序 } ，比如：`<div onClick={ onClick }></div>`
*   注意点\
    react事件采用驼峰命名法，比如：onMouseEnter、onFocus
*   样例

```js
// 函数组件
function HelloFn () {
  // 定义事件回调函数
  const clickHandler = () => {
    console.log('事件被触发了')
  }
  return (
    // 绑定事件
    <button onClick={clickHandler}>click me!</button>
  )
}
```

### 2. 获取事件对象

获取事件对象e只需要在 事件的回调函数中 补充一个形参e即可拿到

```js
// 函数组件
function HelloFn () {
  // 定义事件回调函数
  const clickHandler = (e) => {
    console.log('事件被触发了', e)
  }
  return (
    // 绑定事件
    <button onClick={clickHandler}>click me!</button>
  )
}
```

### 3. 传递额外参数

解决思路: 改造事件绑定为**箭头函数** 在箭头函数中完成参数的传递

```js
import React from "react"

// 如何获取额外的参数？
// onClick={ onDel } -> onClick={ () => onDel(id) }
// 注意: 一定不要在模板中写出函数调用的代码 onClick = { onDel(id) }  bad!!!!!!

const TestComponent = () => {
  const list = [
    {
      id: 1001,
      name: 'react'
    },
    {
      id: 1002,
      name: 'vue'
    }
  ]
  const onDel = (e, id) => {
    console.log(e, id)
  }
  return (
      <ul>
        {list.map(item =>（
           <li key={item.id}>
                {item.name}
                <button onClick={(e) => onDel(e, item.id)}>x</button>
           </li>
        ))}
      </ul>
  )
}

function App () {
  return (
    <div>
      <TestComponent />
    </div>
  )
}
export default App
```

## 类组件的事件绑定

类组件中的事件绑定，整体的方式和函数组件差别不大

唯一需要注意的 因为处于class类语境下 所以定义事件回调函数以及它写法上有不同

1.  定义的时候: class Fields语法

2.  使用的时候: 需要借助this关键词获取

3.  回调函数必须要用 **箭头函数**

```js
import React from "react"
class CComponent extends React.Component {
  // class Fields 写法，推荐这样写
  clickHandler = (e, num) => {
    // 这里的this指向的是正确的当前的组件实例对象 
    // 可以非常方便的通过this关键词拿到组件实例身上的其他属性或者方法
    console.log(this)
  }
  // 错误写法
  clickHandler1 () {
    // 这里的this 不指向当前的组件实例对象而指向undefined 存在this丢失问题
    console.log(this)
  }

  render () {
    return (
      <div>
        <button onClick={(e) => this.clickHandler(e, '123')}>click me</button>
        <button onClick={this.clickHandler1}>click me</button>
      </div>
    )
  }
}

function App () {
  return (
    <div>
      <CComponent />
    </div>
  )
}

export default App
```

## 组件状态

`目标任务:`   能够为组件添加状态和修改状态的值

一个前提：在React hook出来之前，函数式组件是没有自己的状态的，所以我们统一通过类组件来讲解

初始化状态 -> 视图读取初始状态 -> 修改状态 -> 视图使用新状态自动更新

### 1. 初始化状态

*   通过class的实例属性state来初始化
*   state的值是一个对象结构，表示一个组件可以有多个数据状态

```js
class Counter extends React.Component {
  // 初始化状态
  state = {
    count: 0
  }
  render() {
    return <button>计数器</button>
  }
}
```

### 2. 读取状态

*   通过this.state来获取状态

```js
class Counter extends React.Component {
  // 初始化状态
  state = {
    count: 0
  }
  render() {
    // 读取状态
    return <button>计数器{this.state.count}</button>
  }
}
```

### 3. 修改状态

*   语法\
    `this.setState({ 要修改的部分数据 })`

*   setState方法作用

    1.  修改state中的数据状态
    2.  更新UI

*   思想\
    数据驱动视图，也就是只要修改数据状态，那么页面就会自动刷新，无需手动操作dom

*   注意事项\
    **不要直接修改state中的值，必须通过setState方法进行修改**

```js
class Counter extends React.Component {
  // 定义数据
  state = {
    count: 0
  }
  // 定义修改数据的方法
  setCount = () => {
    this.setState({
      count: this.state.count + 1
    })
  }
  // 使用数据 并绑定事件
  render () {
    return <button onClick={this.setCount}>{this.state.count}</button>
  }
}
```

## this问题说明

必须谨慎对待回调函数中的this，在JavaScript中，class的方法默认不会绑定this，如果你忘记绑定this.handleClick并把它传入了onClick，当你调用这个函数的时候this的值为undefined。通常情况下，如果你没有在方法后面添加`()`,例如`onClick={this.handleClick}`，你应该为这个方法绑定this。

*   回调函数不使用箭头函数时，可以在 `constructor`中使用bind进行修正

```js
import React from "react"
class CComponent extends React.Component {
    
  constructor(){
    super()
    //使用bind强行修正 this指向
    // 相当于在类组件初始化的阶段，就可以把回调函数的this 修正到
    // 永远指向当前组件实例对象
    this.handler = this.handler.bind(this)
  }
  // 错误写法
  handler () {
    // 这里的this 不指向当前的组件实例对象而指向undefined 存在this丢失问题
    console.log(this)
  }
  render () {
    // this函数中的this已经被React内部作了修正，这里的this就是指向当前的组件实例对象
    console.log(this)
    return (
      <div>
        <button onClick={this.handler}>click me</button>
        // 如果不使用constructor进行修正，则可以使用以下写法
        <button onClick={() => this.handler()}>click me</button>
      </div>
    )
  }
}
function App () {
  return (
    <div>
      <CComponent />
    </div>
  )
}
export default App
```

这里我们作为了解内容，随着js标准的发展，主流的写法已经变成了class fields，无需考虑太多this问题

## React的状态不可变

`目标任务:`  能够理解不可变的意义并且知道在实际开发中如何修改状态

**概念**：不要直接修改状态的值，而是基于当前状态创建新的状态值

**1. 错误的直接修改**

```js
state = {
  count : 0,
  list: [1,2,3],
  person: {
     name:'jack',
     age:18
  }
}
// 直接修改简单类型Number
this.state.count++
++this.state.count
this.state.count += 1
this.state.count = 1

// 直接修改数组
this.state.list.push(123)
this.state.list.spice(1,1)

// 直接修改对象
this.state.person.name = 'rose'
```

**2. 基于当前状态创建新值**

```js
this.setState({
    count: this.state.count + 1
    //list: [...this.state.list, 4],
    //删除数组元素 2
    list: this.state.list.filter(item => item !== 2)
    person: {
       ...this.state.person,
       // 覆盖原来的属性 就可以达到修改对象中属性的目的
       name: 'rose'
    }
})

```

## 表单处理

`目标任务:`  能够使用受控组件的方式获取文本框的值

使用React处理表单元素，一般有俩种方式：

1.  受控组件 （推荐使用）
2.  非受控组件 （了解）

### 1. 受控表单组件

什么是受控组件？  `input框自己的状态被React组件状态控制`

React组件的状态的地方是在state中，input表单元素也有自己的状态是在value中，React将state与表单元素的值（value）绑定到一起，由state的值来控制表单元素的值，从而保证单一数据源特性

**实现步骤**

以获取文本框的值为例，受控组件的使用步骤如下：

1.  在组件的state中声明一个组件的状态数据
2.  将状态数据设置为input标签元素的value属性的值
3.  为input添加change事件，在事件处理程序中，通过事件对象e获取到当前文本框的值（`即用户当前输入的值`）
4.  调用setState方法，将文本框的值作为state状态的最新值

```js
import React from 'react'

class InputComponent extends React.Component {
  // 声明组件状态
  state = {
    message: 'this is message',
  }
  // 声明事件回调函数
  changeHandler = (e) => {
    this.setState({ message: e.target.value })
  }
  render () {
    return (
      <div>
        {/* 绑定value 绑定事件*/}
        <input value={this.state.message} onChange={this.changeHandler} />
      </div>
    )
  }
}
function App () {
  return (
    <div className="App">
      <InputComponent />
    </div>
  )
}
export default App
```

### 2. 非受控表单组件

什么是非受控组件？

非受控组件就是通过手动操作dom的方式获取文本框的值，文本框的状态不受react组件的state中的状态控制，直接通过原生dom获取输入框的值

**实现步骤**

1.  导入`createRef` 函数
2.  调用createRef函数，创建一个ref对象，存储到名为`msgRef`的实例属性中
3.  为input添加ref属性，值为`msgRef`
4.  在按钮的事件处理程序中，通过`msgRef.current`即可拿到input对应的dom元素，而其中`msgRef.current.value`拿到的就是文本框的值

```jsx
import React, { createRef } from 'react'

class InputComponent extends React.Component {
  // 使用createRef产生一个存放dom的对象容器
  msgRef = createRef()

  changeHandler = () => {
    console.log(this.msgRef.current.value) //点击按钮即可获得输入框的值
  }

  render() {
    return (
      <div>
        {/* ref绑定 获取真实dom */}
        <input ref={this.msgRef} />
        <button onClick={this.changeHandler}>click</button>
      </div>
    )
  }
}
function App () {
  return (
    <div className="App">
      <InputComponent />
    </div>
  )
}
export default App
```

## 阶段小练习

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7faec25f81a94acea67bfd61dfd2158d~tplv-k3u1fbpfcp-zoom-1.image)
**练习说明**

1.  拉取项目模板到本地，安装依赖，run起来项目\
    <https://gitee.com/react-course-series/react-component-demo>
2.  完成tab点击切换激活状态交互
3.  完成发表评论功能\
    注意：生成独一无二的id 可以使用  uuid 包  `yarn add uuid`

### 问题（未解决）

评论框点击提交按钮后，评论输入框中的内容如何清空？\
直接在提交按钮的回调函数中，将value置为空好像不起作用。

```js
  //发表评论按钮的回调函数
  submitComment = ()=>{
    this.setState({
      list: [...this.state.list, 
        {
          id: uuid(),
          author: 'author',
          comment: this.state.comment,
          time: new Date(),
          // 1: 点赞 0：无态度 -1:踩
          attitude: 0
        }
      ],
      comment: '' //这里会把state中的comment置为空，但input里面的value
    })
  }
```

# React组件通信

## 组件通信的意义

`目标任务:`   了解为什么需要组件通信

组件是独立且封闭的单元，默认情况下组件**只能使用自己的数据（state）**

组件化开发的过程中，完整的功能会拆分多个组件，在这个过程中不可避免的需要互相传递一些数据

为了能让各组件之间可以进行互相沟通，数据传递，这个过程就是组件通信

1.  父子关系 -  **最重要的**
2.  兄弟关系 -  自定义事件模式产生技术方法 eventBus  /  通过共同的父组件通信
3.  其它关系 -  **mobx / redux / zustand**

## 父传子实现

`目标任务:`   实现父子通信中的父传子，把父组件中的数据传给子组件

**实现步骤**

1.  父组件提供要传递的数据  -  `state`
2.  给子组件标签`添加属性`值为 state中的数据
3.  子组件中通过 `props` 接收父组件中传过来的数据

<!---->

*   类组件使用this.props获取props对象
*   函数式组件直接通过参数获取props对象

```jsx
import React from 'react'

// 函数式子组件
function FSon(props) {
  console.log(props)
  return (
    <div>
      子组件1
      {props.msg}
    </div>
  )
}

// 类子组件
class CSon extends React.Component {
  render() {
    return (
      <div>
        子组件2
        {this.props.msg}
      </div>
    )
  }
}
// 父组件
class App extends React.Component {
  state = {
    message: 'this is message'
  }
  render() {
    return (
      <div>
        <div>父组件</div>
        <FSon msg={this.state.message} />
        <CSon msg={this.state.message} />
      </div>
    )
  }
}

export default App
```

## props说明

`目标任务:`   知道props传递时的一些注意事项

**1.  props是只读对象（readonly）**

根据单项数据流的要求，子组件只能读取props中的数据，不能进行修改

**2. props可以传递任意数据**

数字、字符串、布尔值、数组、对象、`函数、JSX`

```jsx
class App extends React.Component {
  state = {
    message: 'this is message'
  }
  render() {
    return (
      <div>
        <div>父组件</div>
        <FSon 
          msg={this.state.message} 
          age={20} 
          isMan={true} 
          cb={() => { console.log(1) }} 
          child={<span>this is child</span>}
        />
        <CSon msg={this.state.message} />
      </div>
    )
  }
}
```

## props解构

props是一个对象，里面存着通过父组件传入的所有数据，可以进行 **解构赋值**

```jsx
// 函数式子组件
function FSon(props) {
  const {msg, age, isMan, child} = props
  return (
    <div>
      子组件1
      {msg}
      {age}
    </div>
  )
}

//也可以直接在组件参数的地方进行解构
function FSon({msg, age, isMan, child}) {
  return (
    <div>
      子组件1
      {msg}
      {age}
    </div>
  )
}

```

## 子传父实现

`目标任务:`   实现父子通信中的子传父

**口诀：** 父组件给子组件传递回调函数，子组件调用

***

**实现步骤**

1.  父组件提供一个回调函数 - 用于接收数据
2.  将函数作为属性的值，传给子组件
3.  子组件通过props调用 回调函数
4.  将子组件中的数据作为参数传递给回调函数

**代码实现**

```jsx
import React from 'react'

// 子组件
function Son(props) {
  function handleClick() {
    // 调用父组件传递过来的回调函数 并注入参数
    props.changeMsg('this is newMessage')
  }
  return (
    <div>
      {props.msg}
      <button onClick={handleClick}>change</button>
    </div>
  )
}


class App extends React.Component {
  state = {
    message: 'this is message'
  }
  // 提供回调函数
  changeMessage = (newMsg) => {
    console.log('子组件传过来的数据:',newMsg)
    this.setState({
      message: newMsg
    })
  }
  render() {
    return (
      <div>
        <div>父组件</div>
        <Son
          msg={this.state.message}
          // 传递给子组件
          changeMsg={this.changeMessage}
        />
      </div>
    )
  }
}

export default App
```

## 兄弟组件通信

`目标任务:`   实现兄弟组件之间的通信

**核心思路：** 通过状态提升机制，利用共同的父组件实现兄弟通信

**实现步骤**

1.  将共享状态提升到最近的公共父组件中，由公共父组件管理这个状态

    *   提供共享状态
    *   提供操作共享状态的方法

2.  要接收数据状态的子组件通过 props 接收数据

3.  要传递数据状态的子组件通过props接收方法，调用方法传递数据

```jsx
import React from 'react'

// 子组件A
function SonA(props) {
  return (
    <div>
      SonA
      {props.msg}
    </div>
  )
}
// 子组件B
function SonB(props) {
  return (
    <div>
      SonB
      <button onClick={() => props.changeMsg('new message')}>changeMsg</button>
    </div>
  )
}

// 父组件
class App extends React.Component {
  // 父组件提供状态数据
  state = {
    message: 'this is message'
  }
  // 父组件提供修改数据的方法
  changeMsg = (newMsg) => {
    this.setState({
      message: newMsg
    })
  }

  render() {
    return (
      <>
        {/* 接收数据的组件 */}
        <SonA msg={this.state.message} />
        {/* 修改数据的组件 */}
        <SonB changeMsg={this.changeMsg} />
      </>
    )
  }
}

export default App
```

## 跨组件通信Context

`目标任务:`   了解Context机制解决的问题和使用步骤

![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7c4ea1ac39c847eeaca7b68815de79cb~tplv-k3u1fbpfcp-watermark.image?)

上图是一个react形成的嵌套组件树，如果我们想从App组件向任意一个下层组件传递数据，该怎么办呢？目前我们能采取的方式就是一层一层的props往下传，显然很繁琐

那么，Context 提供了一个**无需为每层组件手动添加 props，就能在组件树间进行数据传递的方法**

***

**实现步骤**

1- 创建Context对象 导出 Provider 和 Consumer对象

```jsx
    const { Provider, Consumer } = createContext()
```

2- 使用Provider包裹上层组件提供数据

```jsx
    <Provider value={this.state.message}>{/* 根组件 */} </Provider>
```

3- 需要用到数据的组件使用Consumer包裹获取数据

```jsx
<Consumer >
    {value => /* 基于 context 值进行渲染*/}
</Consumer>
```

**代码实现**

```jsx
import React, { createContext }  from 'react'

// 1. 创建Context对象 
const { Provider, Consumer } = createContext()


// 3. 消费数据
function ComC() {
  return (
    <Consumer >
      {value => <div>{value}</div>}
    </Consumer>
  )
}

function ComA() {
  return (
    <ComC/>
  )
}

// 2. 提供数据
class App extends React.Component {
  state = {
    message: 'this is message'
  }
  render() {
    return (
      <Provider value={this.state.message}>
        <div className="app">
          <ComA />
        </div>
      </Provider>
    )
  }
}

export default App
```

## 阶段小练习

要求：App为父组件用来提供列表数据 ，ListItem为子组件用来渲染列表数据

```js
// 列表数据
[
  { id: 1, name: '超级好吃的棒棒糖', price: 18.8, info: '开业大酬宾，全场8折' },
  { id: 2, name: '超级好吃的大鸡腿', price: 34.2, info: '开业大酬宾，全场8折' },
  { id: 3, name: '超级无敌的冰激凌', price: 14.2, info: '开业大酬宾，全场8折' }
]
```

完整代码

```jsx
import React from 'react'

// 子组件
function ListItem(props) {
  const { name, price, info, id, delHandler } = props
  return (
    <div>
      <h3>{name}</h3>
      <p>{price}</p>
      <p>{info}</p>
      <button onClick={() => delHandler(id)}>删除</button>
    </div>
  )
}

// 父组件
class App extends React.Component {
  state = {
    list: [
      { id: 1, name: '超级好吃的棒棒糖', price: 18.8, info: '开业大酬宾，全场8折' },
      { id: 2, name: '超级好吃的大鸡腿', price: 34.2, info: '开业大酬宾，全场8折' },
      { id: 3, name: '超级无敌的冰激凌', price: 14.2, info: '开业大酬宾，全场8折' }
    ]
  }
  delHandler = (id) => {
    this.setState({
      list: this.state.list.filter(item => item.id !== id)
    })
  }
  render() {
    return (
      <>
        {
          this.state.list.map(item =>
            <ListItem
              key={item.id}
              {...item}
              delHandler={this.delHandler} 
            />
          )
        }
      </>
    )
  }
}
export default App
```
# React组件进阶

## children属性

`目标任务:`  掌握props中children属性的用法
**children属性是什么**

表示该组件的子节点，只要组件内部有子节点，props中就有该属性

**children可以是什么**

1.  普通文本
1.  普通标签元素
1.  函数 / 对象
1.  JSX

## props校验-场景和使用

`目标任务:`  掌握组件props的校验写法，增加组件的健壮性


对于组件来说，props是由外部传入的，我们其实无法保证组件使用者传入了什么格式的数据，如果传入的数据格式不对，就有可能会导致组件内部错误，有一个点很关键 - **组件的使用者可能报错了也不知道为什么**，看下面的例子

```jsx
const list = props => [
    const arr = props.color
    const lis = arr.map((item, index) => <li key = {index}>{item.name}</li>)
    return (
        <ul>{lis}</ul>
    )
}
<List colors = {19}/>
```

面对这样的问题，如何解决？ **props校验**

**实现步骤**

1.  安装属性校验包：`yarn add prop-types`
2.  导入`prop-types` 包
3.  使用 `组件名.propTypes = {}` 给组件添加校验规则

```jsx
import PropTypes from 'prop-types'

const List = props => {
  const arr = props.colors
  const lis = arr.map((item, index) => <li key={index}>{item.name}</li>)
  return <ul>{lis}</ul>
}

List.propTypes = {
  colors: PropTypes.array
}
```

## props校验-规则说明

`目标任务:`  掌握props常见的规则

**四种常见结构**

1.  常见类型：array、bool、func、number、object、string
2.  React元素类型：element
3.  必填项：isRequired
4.  特定的结构对象：shape({})

***

```jsx
// 常见类型
optionalFunc: PropTypes.func,
// 必填 只需要在类型后面串联一个isRequired
requiredFunc: PropTypes.func.isRequired,
// 特定结构的对象
optionalObjectWithShape: PropTypes.shape({
	color: PropTypes.string,
	fontSize: PropTypes.number
})
```

官网文档更多阅读：<https://reactjs.org/docs/typechecking-with-proptypes.html>

## props校验-默认值

`目标任务:`  掌握如何给组件的props提供默认值

通过 `defaultProps` 可以给组件的props设置默认值，在未传入props的时候生效

### 1. 函数组件

直接使用函数参数默认值

```jsx
function List({pageSize = 10}) {
  return (
    <div>
      此处展示props的默认值：{ pageSize }
    </div>
  )
}

// 不传入pageSize属性
<List />
```

### 2. 类组件

使用类静态属性声明默认值，`static defaultProps = {}`

```jsx
class List extends Component {
  static defaultProps = {
    pageSize: 10
  }
  render() {
    return (
      <div>
        此处展示props的默认值：{this.props.pageSize}
      </div>
    )
  }
}
<List />
```

## 生命周期 - 概述

`目标任务:`  能够说出组件生命周期一共几个阶段

组件的生命周期是指组件从被创建到挂载到页面中运行起来，再到组件不用时卸载的过程，注意，只有类组件才有生命周期（类组件 实例化  函数组件 不需要实例化）

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8cb914ab73854d7d9f2692e807669239~tplv-k3u1fbpfcp-zoom-1.image)

Render阶段—— 纯净且不包含副作用

<http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/>

## 生命周期 - 挂载阶段

`目标任务:`  能够说出在组件挂载阶段执行的钩子函数和执行时机

![life1.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a223f81528de41bebf467f5fcb1d695c~tplv-k3u1fbpfcp-zoom-1.image)

| 钩子 函数             | 触发时机                        | 作用                                              |
| ----------------- | --------------------------- | ----------------------------------------------- |
| constructor       | 创建组件时，最先执行，初始化的时候只执行一次      | 1. 初始化state  2. 创建 Ref（前两种情况，**是之前这样用，现在不这样用了**） 3. 使用 bind 解决 this 指向问题等 |
| render            | 每次组件渲染都会触发                  | 渲染UI（注意： 不能在里面调用setState() ）                    |
| componentDidMount | 组件挂载（完成DOM渲染）后执行，初始化的时候执行一次 | 1. 发送网络请求   2.DOM操作                             |

## 生命周期 - 更新阶段

`目标任务:`  能够说出组件的更新阶段的钩子函数以及执行时机

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/631cf28553a444e98e91327f172df91b~tplv-k3u1fbpfcp-zoom-1.image)

| 钩子函数               | 触发时机           | 作用                                      |
| ------------------ | -------------- | --------------------------------------- |
| render             | 每次组件渲染都会触发     | 渲染UI（与 挂载阶段 是同一个render）                 |
| componentDidUpdate | 组件更新后（DOM渲染完毕） | DOM操作，可以获取到更新后的DOM内容，**不要直接调用setState** |

## 生命周期 - 卸载阶段

`目标任务:`  能够说出组件的销毁阶段的钩子函数以及执行时机

| 钩子函数                 | 触发时机         | 作用                |
| -------------------- | ------------ | ----------------- |
| componentWillUnmount | 组件卸载（从页面中消失） | 执行清理工作（比如：清理定时器等） |

## 阶段小练习 - todoMVC

案例仓库地址：<https://gitee.com/react-course-series/react-todo-mvc>\
1- 克隆项目到本地

2- 安装必要依赖

3- 开启mock接口服务，保持窗口不关闭  ！！！！！

4- 另起一个bash窗口开启前端服务

5- 切换到todo-test分支

接口文档

| 接口作用 | 接口地址                                                                              | 接口方法   | 接口参数            |
| ---- | --------------------------------------------------------------------------------- | ------ | --------------- |
| 获取列表 | <http://localhost:3001/data>                                                      | GET    | 无               |
| 删除   | <http://localhost:3001/data/:id>                                                  | DELETE | id              |
| 搜索   | [http://localhost:3001/data/?name=keyword](http://localhost:3001/data/?q=keyword) | GET    | name（以name字段搜索） |

实现功能

| 功能     | 核心思路                 |
| ------ | -------------------- |
| 表格数据渲染 | 组件使用                 |
| 删除功能   | 获取当前id  调用接口         |
| 搜索功能   | 用的依旧是列表接口，多传一个name参数 |
| 清除搜索功能 | 清空搜索参数  重新获取列表       |

```jsx
import { Input, Table, Space, Popconfirm } from 'antd'
import React from 'react'
import './App.css'
import axios from 'axios'

// 1. 找到对应的组件 把页面搭起来
// 2. table渲染出来 (发送请求（componentDidMount）) 拿到数据 交给list（this.setState）
// 3. 删除功能（点击哪个用哪个id  调用删除接口 重新拉取列表）
const { Search } = Input

class App extends React.Component {
  state = {
    list: [],
    columns: [
      {
        title: '任务编号',
        dataIndex: 'id',
        key: 'id',
      },
      {
        title: '任务名称',
        dataIndex: 'name',
        key: 'name', //与axios获得的数据相对，找key相同的内容来渲染这一列
      },
      {
        title: '任务描述',
        dataIndex: 'des',
        key: 'des',
      },
      {
        title: '操作',
        dataIndex: 'do',
        key: 'do',
        render: (_, record) => (
          <Space size="middle">
            <Popconfirm title="确定要删除吗?"
            /* record 当前行数据*/
              onConfirm={() => this.handleDelete(record.id)}>
              <a href="#">删除</a>
            </Popconfirm>
          </Space>
        ),
      },
    ]
  }

  // 搜索
  onSearch = async (value) => {
    console.log(value)
    const res = axios.get(`http://localhost:3001/data/?name=${value}`)
    this.setState({
      list: res.data
    })
  }
  // 删除
  handleDelete = async (id) => {
    await axios.delete(`http://localhost:3001/data/${id}`)
  }
  // 加载列表
  LoadList = async() => {
    const res = await axios.get('http://localhost:3001/data')
    console.log(res)
    this.setState({
      list: res.data
    })
  }

  componentDidMount(){
    this.LoadList()
  }
  render () {
    return (
      <div className="container">
        <div className="search-box">
          <Search
            placeholder="请输入关键词"
            allowClear
            enterButton="搜索"
            size="large"
            onChange={this.inputChange}
            value={this.state.keyword}
            /* 点击搜索图标，清除图标，或按下回车键时的回调函数  onSearch(value, event)*/
            onSearch={this.onSearch} 
          />
        </div>
        {/* table 表格组件， 依赖两个必要数据，一个定义列，一个用来遍历渲染*/}
        <Table bordered dataSource={this.state.list} columns={this.state.columns} pagination={false} />
      </div>
    )
  }
}

export default App

```
# Hooks基础

## Hooks概念理解

`本节任务:` 能够理解hooks的概念及解决的问题

### 1. 什么是hooks

Hooks的本质：**一套能够使函数组件更强大，更灵活的“钩子”**

React体系里组件分为 类组件 和 函数组件

经过多年的实战，函数组件是一个更加匹配React的设计理念 `UI = f(data)`，也更有利于逻辑拆分与重用的组件表达形式，而先前的函数组件是不可以有自己的状态的，为了能让函数组件可以拥有自己的状态，所以从react v16.8开始，Hooks应运而生

**注意点：**

1.  有了hooks之后，为了兼容老版本，class类组件并没有被移除，俩者都可以使用

2.  有了hooks之后，不能在把函数成为无状态组件了，因为hooks为函数组件提供了状态

3.  hooks只能在函数组件中使用

### 2. Hooks解决了什么问题

Hooks的出现解决了俩个问题    1. 组件的状态逻辑复用  2.class组件自身的问题

1.  组件的逻辑复用\
    在hooks出现之前，react先后尝试了 mixins混入，HOC高阶组件，render-props等模式\
    但是都有各自的问题，比如mixin的数据来源不清晰，高阶组件的嵌套问题等等
2.  class组件自身的问题\
    class组件就像一个厚重的‘战舰’ 一样，大而全，提供了很多东西，有不可忽视的学习成本，比如各种生命周期，this指向问题等等，而我们更多时候需要的是一个轻快灵活的'快艇'

## useState

### 1. 基础使用

`本节任务:` 能够学会useState的基础用法

**作用**

useState为函数组件提供状态（state）

**使用步骤**

1.  导入 `useState` 函数
2.  调用 `useState` 函数，并传入状态的初始值
3.  从`useState`函数的返回值中，拿到状态和修改状态的方法
4.  在JSX中展示状态
5.  调用修改状态的方法更新状态

**代码实现**

```jsx
import { useState } from 'react'

function App() {
  // 参数：状态初始值比如,传入 0 表示该状态的初始值为 0
  // 返回值：数组,包含两个值：1 状态值（state） 2 修改该状态的函数（setState）
  const [count, setCount] = useState(0)
  return (
    <button onClick={() => { setCount(count + 1) }}>{count}</button>
  )
}
export default App
```

### 2. 状态的读取和修改

`本节任务:` 能够理解useState下状态的读取和修改

**读取状态**

该方式提供的状态，是函数内部的局部变量，可以在函数内的任意位置使用

**修改状态**

1.  setCount是一个函数，参数表示`最新的状态值`

2.  调用该函数后，将使用新值替换旧值

3.  修改状态后，由于状态发生变化，会引起视图变化

**注意事项**

1.  修改状态的时候，一定要使用新的状态替换旧的状态，不能直接修改旧的状态，尤其是引用类型

### 3. 组件的更新过程

`本节任务:`  能够理解使用hook之后组件的更新情况

函数组件使用 **useState** hook 后的执行过程，以及状态值的变化

*   组件第一次渲染

    1.  从头开始执行该组件中的代码逻辑
    2.  调用 `useState(0)` 将传入的参数作为状态初始值，即：0
    3.  渲染组件，此时，获取到的状态 count 值为： 0

*   组件第二次渲染

    1.  点击按钮，调用 `setCount(count + 1)` 修改状态，因为状态发生改变，所以，该组件会重新渲染

    2.  组件重新渲染时，会再次执行该组件中的代码逻辑

    3.  再次调用 `useState(0)`，此时 **React 内部会拿到最新的状态值而非初始值**，比如，该案例中最新的状态值为 1

    4.  再次渲染组件，此时，获取到的状态 count 值为：1

注意：**useState 的初始值(参数)只会在组件第一次渲染时生效**。也就是说，以后的每次渲染，useState 获取到都是最新的状态值，React 组件会记住每次最新的状态值

```jsx
import { useState } from 'react'

function App() {
  const [count, setCount] = useState(0)
  // 在这里可以进行打印测试
  console.log(count)
  return (
    <button onClick={() => { setCount(count + 1) }}>{count}</button>
  )
}
export default App
```

### 4. 使用规则

`本节任务:`  能够记住useState的使用规则

1.  `useState` 函数可以执行多次，每次执行互相独立，每调用一次为函数组件提供一个状态

```jsx
function List(){
  // 以字符串为初始值
  const [name, setName] = useState('cp')
  // 以数组为初始值
  const [list,setList] = useState([])
}
```

2.  `useState` 注意事项

<!---->

*   只能出现在函数组件或者其他hook函数中
*   不能嵌套在if/for/其它函数中（react按照hooks的调用顺序识别每一个hook）
*  可以通过开发者工具查看hooks状态

```jsx
let num = 1
function List(){
  num++
  if(num / 2 === 0){
     const [name, setName] = useState('cp') 
  }
  const [list,setList] = useState([])
}
// 俩个hook的顺序不是固定的，这是不可以的！！！
```
## useEffect

### 1. 理解函数副作用

`本节任务:` 能够理解副作用的概念

**什么是副作用**

副作用是相对于主作用来说的，一个函数除了主作用，其他的作用就是副作用。对于 React 组件来说，**主作用就是根据数据（state/props）渲染 UI**，除此之外都是副作用（比如，手动修改 DOM）

**常见的副作用**

1.  数据请求 ajax发送
2.  手动修改dom
3.  localstorage操作

useEffect函数的作用就是为react函数组件提供副作用处理的！

```js
function geNum1(a + b){
    return a + b //纯函数
}
let count = 0
function geNum2(a + b){
    count ++;
    return a + b //不是纯函数，还包含了副作用count ++
}

```

### 2. 基础使用

`本节任务:` 能够学会useEffect的基础用法并且掌握默认的执行执行时机

**作用**

为react函数组件提供副作用处理

**使用步骤**

1.  导入 `useEffect` 函数
2.  调用 `useEffect` 函数，并传入回调函数
3.  在回调函数中编写副作用处理（dom操作）
4.  修改数据状态
5.  检测副作用是否生效

```jsx
//在修改数据后，把count 值放到页面标题中
import { useEffect, useState } from 'react'

function App() {
  const [count, setCount] = useState(0)
 
  useEffect(()=>{
    // dom操作
    document.title = `当前已点击了${count}次`
  })
  return (
    <button onClick={() => { setCount(count + 1) }}>{count}</button>
  )
}

export default App
```

### 3. 依赖项控制执行时机

`本节任务:` 能够学会使用依赖项控制副作用的执行时机

**1. 不添加依赖项**

组件首次渲染执行一次，以及不管是哪个状态更改引起组件更新时都会重新执行

1.  组件初始渲染
2.  组件更新 （不管是哪个状态引起的更新）

```jsx
useEffect(()=>{
    console.log('副作用执行了')
})
```

**2. 添加空数组**

组件只在首次渲染时执行一次

```jsx
useEffect(()=>{
	 console.log('副作用执行了')
},[])
```

**3. 添加特定依赖项**

副作用函数在首次渲染时执行，在依赖项发生变化时重新执行

```jsx
function App() {  
    const [count, setCount] = useState(0)  
    const [name, setName] = useState('zs') 
    
    useEffect(() => {    
        console.log('副作用执行了')  
    }, [count])  
    
    return (    
        <>      
         <button onClick={() => { setCount(count + 1) }}>{count}</button>      
         <button onClick={() => { setName('cp') }}>{name}</button>    
        </>  
    )
}
```

**注意事项**

useEffect 回调函数中用到的数据（比如，count）就是依赖数据，就应该出现在依赖项数组中，如果不添加依赖项就会有bug出现（即回调函数中包含了哪个数据，哪些数据就应该放在useEffect的第二个参数数组中）

### 4. 清理副作用

如果想要清理副作用 可以在副作用函数中的末尾return一个新的函数，在新的函数中编写清理副作用的逻辑

注意执行时机为：

1.  组件卸载时自动执行
2.  组件更新时，下一个useEffect副作用函数执行之前自动执行

```jsx
import { useEffect, useState } from "react"


const App = () => {
  const [count, setCount] = useState(0)
  useEffect(() => {
    const timerId = setInterval(() => {
      setCount(count + 1)
    }, 1000)
    return () => {
      // 用来清理副作用的事情
      clearInterval(timerId)
    }
  }, [count])
  return (
    <div>
      {count}
    </div>
  )
}

export default App
```

## 阶段小练习 - 自定义hook

**需求描述**：自定义一个hook函数，实现获取滚动距离Y

`const [y] = useWindowScroll()`

```jsx
import { useState, useEffect } from "react"

export function useWindowScroll () {
  const [y, setY] = useState(0)
  useEffect(()=>{
     const scrollHandler = () => {
        const h = document.documentElement.scrollTop
        setY(h)
     })
     window.addEventListener('scroll', scrollHandler)
     return () => window.removeEventListener('scroll', scrollHandler)
  })
 
  return [y]
}
```

**需求描述：** 自定义hook函数，可以自动同步到本地LocalStorage

`const [message, setMessage] = useLocalStorage(key，defaultValue)`

1.  message可以通过自定义传入默认初始值
2.  每次修改message数据的时候 都会自动往本地同步一份

```jsx
import { useEffect, useState } from 'react'

export function useLocalStorage (key, defaultValue) {
  const [message, setMessage] = useState(defaultValue)
  // 每次只要message变化 就会自动同步到本地ls
  useEffect(() => {
    window.localStorage.setItem(key, message)
  }, [message, key])
  return [message, setMessage]
}
```

# Hooks进阶

## useState - 回调函数的参数

`本节任务:`  能够理解useState回调函数作为参数的使用场景

**使用场景**

参数只会在组件的初始渲染中起作用，后续渲染时会被忽略。如果初始 state 需要通过计算才能获得，则可以传入一个函数，在函数中计算并返回初始的 state，此函数只在初始渲染时被调用

**语法**

```jsx
const [name, setName] = useState(()=>{   
  // 编写计算逻辑    return '计算之后的初始值'
})
```

**语法规则**

1.  回调函数return出去的值将作为 `name` 的初始值

2.  回调函数中的逻辑只会在组件初始化的时候执行一次

**语法选择**

1.  如果就是初始化一个普通的数据 直接使用 `useState(普通数据)` 即可

2.  如果要初始化的数据无法直接得到需要通过计算才能获取到，使用`useState(()=>{})`

**来个需求**

```jsx
import { useState } from 'react'

function Counter(props) {
  const [count, setCount] = useState(() => {
    return props.count
  })
  return (
    <div>
      <button onClick={() => setCount(count + 1)}>{count}</button>
    </div>
  )
}

function App() {
  return (
    <>
      <Counter count={10} />
      <Counter count={20} />
    </>
  )
}

export default App
```

## useEffect - 发送网络请求

`本节任务:`  能够掌握使用useEffect hook发送网络请求

**使用场景**

如何在useEffect中发送网络请求，并且封装同步 async await操作

**语法要求**

不可以直接在useEffect的回调函数外层直接包裹 await ，因为**异步会导致清理函数无法立即返回**

```jsx
useEffect(async ()=>{    
    const res = await axios.get('http://geek.itheima.net/v1_0/channels')   
    console.log(res)
},[])
```

**正确写法**

在内部单独定义一个函数，然后把这个函数包装成同步

```jsx
useEffect(()=>{   
    async function fetchData(){      
       const res = await axios.get('http://geek.itheima.net/v1_0/channels')                            console.log(res)   
    } 
},[])
```

## useRef

`本节任务:`  能够掌握使用useRef获取真实dom或组件实例的方法

**使用场景**

在函数组件中获取真实的dom元素对象或者是组件对象

**使用步骤**

1.  导入 `useRef` 函数

2.  执行 `useRef` 函数并传入null，返回值为一个对象 内部有一个current属性存放拿到的dom对象（组件实例）

3.  通过ref 绑定 要获取的元素或者组件

**获取dom**

```jsx
import { useEffect, useRef } from 'react'
function App() {  
    const h1Ref = useRef(null)  
    useEffect(() => {    
        console.log(h1Ref.current)  
    },[])  
    return (    
        <div>      
            <h1 ref={ h1Ref }>this is h1</h1>    
        </div>  
    )
}
export default App
```

**获取组件实例**

函数组件由于没有实例，不能使用ref获取，如果想获取组件实例，必须是类组件

```jsx
class Foo extends React.Component {  
    sayHi = () => {    
        console.log('say hi')  
    }  
    render(){    
        return <div>Foo</div>  
    }
}
    
export default Foo
```

```jsx
import { useEffect, useRef } from 'react'
import Foo from './Foo'
function App() {  
    const h1Foo = useRef(null)  
    useEffect(() => {    
        console.log(h1Foo)  //组件示例对象，包含了各种方法和对象
        console.log(h1Foo.)
    }, [])  
    return (    
        <div> <Foo ref={ h1Foo } /></div>  
    )
}
export default App
```

## useContext

`本节任务:`  能够掌握hooks下的context使用方式

**实现步骤**

1.  使用`createContext` 创建Context对象
2.  在顶层组件通过`Provider` 提供数据
3.  在底层组件通过`useContext`函数获取数据

**代码实现**

```jsx
import { createContext, useContext } from 'react'
// 创建Context对象
const Context = createContext()

function Foo() {  
    return <div>Foo <Bar/></div>
}

function Bar() {  
    // 底层组件通过useContext函数获取数据  
    const name = useContext(Context)  
    return <div>Bar {name}</div>
}

function App() {  
    return (    
        // 顶层组件通过Provider 提供数据    
        <Context.Provider value={'this is name'}>     
            <div><Foo/></div>    
        </Context.Provider>  
    )
}
export default App
```

## 补充知识

\<Context.Provider value={'this is name'}> 也可以直接写到index.js文件中，包裹app.js，但这是静态数据。

如果Context需要传递数据并且将来还需要对数据做修改，底层组件也需要跟着一起变，写到app.js中

**ReactRouter**

# ReactRouter前置知识

## 1. 单页应用

只有一个html文件 主流的开发模式变成了通过路由进行页面切换 优势: 避免整体页面刷新 用户体验变好

前端负责事情变多了 开发的难度变大

## 2. 路由的本质

概念来源于后端 : 一个路径表示匹配一个服务器资源 /a.html -> a对应的文件资源 /b.html -> b对应的文件资源

共同的思想: 一对一的关系

前端的路由: 一个路径path对应唯一的一个组件comonent 当我们访问一个path 自动把path对应的组件进行渲染

```jsx
const routes = [
  {
    path:'/home',
    component: Home
  },
   {
    path:'/about',
    component: About
  },
   {
    path:'/article',
    component: Article
  }
]
```
# 准备项目环境

create-react-app -> cra -> webpack

vite: 可以实现cra同等能力 但是速度更快的打包工具

使用vite新增一个React项目，然后安装一个v6版本的react-router-dom

```jsx
# 创建react项目
$ yarn create vite react-router --template react

# 安装所有依赖包
$ yarn

# 启动项目
$ yarn dev

# 安装react-router包
$ yarn add react-router-dom@6
```

# 基础使用

需求: 准备俩个按钮，点击不同按钮切换不同组件内容的显示

实现步骤：

1.  导入必要的路由router内置组件
2.  准备俩个React组件
3.  按照路由的规则进行路由配置

```jsx
// 引入必要的内置组件
import { BrowserRouter, Routes, Route, Link } from 'react-router-dom'

// 准备俩个路由组件

const Home = () => <div>this is home</div>
const About = () => <div>this is about</div>

function App() {
  return (
    <div className="App">
      {/* 按照规则配置路由,声明当前要用一个非hash模式的路由 */}
      <BrowserRouter>
      {/*指定跳转的组件，to用来配置路由地址*/}
        <Link to="/">首页</Link>
        <Link to="/about">关于</Link>
        <Routes>
          <Route path="/" element={<Home />}></Route>
          <Route path="/about" element={<About />}></Route>
        </Routes>
      </BrowserRouter>
    </div>
  )
}

export default App
```

# 核心内置组件说明

## 1. BrowerRouter

作用: 包裹整个应用，一个React应用只需要使用一次

如果将BrowerRouter改为HashRouter，里面的代码不需要改变，只有网页的路径会包含一个#，即由history模式变为哈希模式。

| **模式**       | **实现方式**                    | **路由url表现**                     |
| ------------ | --------------------------- | ------------------------------- |
| HashRouter   | 监听url hash值实现               | <http://localhost:3000/#/about> |
| BrowerRouter | h5的 history.pushState API实现 | <http://localhost:3000/about>   |

## 2. Link

作用: 用于指定导航链接，完成声明式的路由跳转 类似于\<router-link/>

```js
<Link to="/about">关于</Link>
```

这里to属性用于指定路由地址，表示要跳转到哪里去，Link组件最终会被渲染为原生的a链接

## 3. Routes

> 作用: 提供一个路由出口，组件内部会存在多个内置的Route组件，满足条件的路由会被渲染到组件内部
>
> 类比 router-view

```jsx
  <Routes>
  //以下两个路由，哪个满足条件，哪个对应的组件就会渲染到这里
    <Route path="/" element={<Home />}></Route>
    <Route path="/about" element={<About />}></Route>
  </Routes>
```

## 4. Route

作用: 用于定义路由路径和渲染组件的对应关系 \[element：因为react体系内 把组件叫做react element]

```jsx
<Route path="/about" element={<About />}></Route>
```

其中path属性用来指定匹配的路径地址，element属性指定要渲染的组件，图中配置的意思为: 当url上访问的地址为 /about 时，当前路由发生匹配，对应的About组件渲染

# 编程式导航

声明式 【 Link to】 vs 编程式 【调用路由方法进行路由跳转】

概念: 通过js编程的方式进行路由页面跳转，比如说从登录跳转到关于页

实现步骤：

1.  导入一个 useNavigate 钩子函数
2.  执行 useNavigate 函数 得到 跳转函数
3.  在事件中执行跳转函数完成路由跳转

```jsx
// 导入useNavigate函数
import { useNavigate } from 'react-router-dom'
const Home = () => {
  // 执行函数
  const navigate = useNavigate()
  return (
    <div>
      Home
      <button onClick={ ()=> navigate('/about') }> 跳转关于页 </button>
    </div>
  )
}

export default Home
```

注: 如果在跳转时不想添加历史记录，可以添加额外参数replace 为true

```jsx
navigate('/about', { replace: true } )
```

# 路由传参

场景：跳转路由的同时，有时候要需要传递参数

## 1. searchParams传参

**路由传参**

```jsx
navigate('/about?id=1001')
navigate('/about?id=1001&name=cp&id=1002') //如果有重复的，会以第一个值为最终结果
```

**路由取参**

```jsx
let [params] = useSearchParams()
let id = params.get('id')
let name = params.get('name')
console.log(params) //是一个对象，包含了许多方法
```

## 2. params传参

**路由传参**

```jsx
navigate('/about/1001')
```

**路由取参**

Route里面也需要进行修改

```jsx
<Route path="/about/:id" element={<About />}></Route>

let params = useParams()//返回一个对象
let id = params.id
```

# 嵌套路由

场景：在我们做的很多的管理后台系统中，通常我们都会设计一个Layout组件，在它内部实现嵌套路由。

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8181a4aa62734dba80769a3f266105c7~tplv-k3u1fbpfcp-watermark.image?)

实现步骤：

1.  App.js中定义嵌套路由声明
2.  Layout组件内部通过 <Outlet/> 指定二级路由出口

1- App.js组件中定义路由嵌套关系

```jsx
<Routes>
  <Route path="/"  element={<Layout/>}>
  { /* 二级路由的path不需要加 / */ }
    <Route path="board" element={ <Board/> } />
    <Route path="article" element={ <Article/> } />
  </Route>
   { /* 省略部分  */ }
</Routes>
```

2- Layout.js组件中使用 Outlet 组件添加二级路由出口

```jsx
import { Outlet } from 'react-router-dom'

const Layout = () => {
  return (
    <div>
      layout
      { /* 二级路由的path等于 一级path + 二级path  */ }
      <Link to="/board">board</Link>
      <Link to="/article">article</Link>
      { /* 二级路由出口 */ }
      <Outlet/>
    </div>
  )
}
export default Layout
```

# 默认二级路由

场景: 应用首次渲染完毕就需要显示的二级路由

实现步骤:

1.  给默认二级路由标记index属性
2.  把原本的路径path属性去掉

```jsx
<Routes>
  <Route path="/"  element={<Layout/>}>
    <Route index element={ <Board/> } />
    <Route path="article" element={ <Article/> } />
  </Route>
</Routes>
```

```jsx
import { Outlet } from 'react-router-dom'

const Layout = () => {
  return (
    <div>
      layout
      { /* 默认二级不再具有自己的路径  */ }
      <Link to="/">board</Link>
      <Link to="/article">article</Link>
      { /* 二级路由出口 */ }
      <Outlet/>
    </div>
  )
}
```

# 404路由配置

场景：当url的路径在整个路由配置中都找不到对应的path，使用404兜底组件进行渲染

在各级路由的最后添加 \* 号路由作为兜底

1- 准备一个NotFound组件

```jsx
const NotFound = () => {
  return <div>this is NotFound</div>
}

export default NotFound
```

```jsx
//App.js
<BrowserRouter>
  <Routes>
    <Route path="/" element={<Layout />}>
      <Route index element={<Board />} />
      <Route path="article" element={<Article />} />
    </Route>
    <Route path="*" element={<NotFound />}></Route>
  </Routes>
</BrowserRouter>
```

# 集中式路由配置

> 场景: 当我们需要路由权限控制点时候, 对路由数组做一些权限的筛选过滤，所谓的集中式路由配置就是用一个数组统一把所有的路由对应关系写好替换 本来的Roues组件

```jsx
import { BrowserRouter, Routes, Route, useRoutes } from 'react-router-dom'

import Layout from './pages/Layout'
import Board from './pages/Board'
import Article from './pages/Article'
import NotFound from './pages/NotFound'

// 1. 准备一个路由数组 数组中定义所有的路由对应关系
const routesList = [
  {
    path: '/',
    element: <Layout />,
    children: [
      {
        element: <Board />,
        index: true, // index设置为true 变成默认的二级路由
      },
      {
        path: 'article',
        element: <Article />,
      },
    ],
  },
  // 增加n个路由对应关系
  {
    path: '*',
    element: <NotFound />,
  },
]

// 2. 使用useRoutes方法传入routesList生成Routes组件
function WrapperRoutes() {
  let element = useRoutes(routesList)
  return element
}

function App() {
  return (
    <div className="App">
      <BrowserRouter>
        {/* 3. 替换之前的Routes组件 */}
        <WrapperRoutes />
      </BrowserRouter>
    </div>
  )
}

export default App
```
