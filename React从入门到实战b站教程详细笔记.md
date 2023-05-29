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


