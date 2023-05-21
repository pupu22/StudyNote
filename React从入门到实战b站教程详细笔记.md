视频： [React入门到实战(2022全网最新](https://www.bilibili.com/video/BV1Z44y1K7Fj/?spm_id_from=333.1007.top_right_bar_window_history.content.click\&vd_source=c8b9ba4c470a783033f0287d1c7b102b)

笔记[ 语雀](https://www.yuque.com/fechaichai/qeamqf)

> 说个题外话\
> 这个视频作者提供了语雀上面的文档，但是我需要markdown格式的笔记，因此花了两个小时研究怎么把网页里面的内容转换为markdown格式，尝试了cubox+ copy as markdown 以及印象笔记，还有各种将html文件转换为markdown的工具，最后发现复制到掘金里面就可以转换格式，太离谱了。

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

解决思路: 改造事件绑定为箭头函数 在箭头函数中完成参数的传递

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

唯一需要注意的 因为处于class类语境下 所以定义事件回调函数以及定它写法上有不同

1.  定义的时候: class Fields语法

2.  使用的时候: 需要借助this关键词获取

```js
import React from "react"
class CComponent extends React.Component {
  // class Fields
  clickHandler = (e, num) => {
    // 这里的this指向的是正确的当前的组件实例对象 
    // 可以非常方便的通过this关键词拿到组件实例身上的其他属性或者方法
    console.log(this)
  }

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
    list: [...this.state.list, 4],
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
    console.log(this.msgRef.current.value)
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

1.  1.  类组件使用this.props获取props对象
    2.  函数式组件直接通过参数获取props对象

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
## 子传父实现

`目标任务:`   实现父子通信中的子传父

**口诀：** 父组件给子组件传递回调函数，子组件调用

****

**实现步骤**

1.  父组件提供一个回调函数 - 用于接收数据
1.  将函数作为属性的值，传给子组件
1.  子组件通过props调用 回调函数
1.  将子组件中的数据作为参数传递给回调函数



