视频地址：[黑马ajax](https://www.bilibili.com/video/BV1zs411h74a/?p=2\&spm_id_from=pageDriver\&vd_source=c8b9ba4c470a783033f0287d1c7b102b)

笔记地址：[ajax笔记](https://gitee.com/AuroraManito/note/tree/master/sgg/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98AJAX%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%88%B0%E7%B2%BE%E9%80%9A_%E6%95%B4%E5%90%88Git%E6%A0%B8%E5%BF%83%E5%86%85%E5%AE%B9%E5%85%A8%E5%A5%97%E6%95%99%E7%A8%8B)

# 一、Ajax基础

## 1. 客户端与服务器

### 1.1 上网的目的

*   刷微博
*   浏览新闻
*   在线听音乐
*   在线看电影
*   etc...

上网的本质目的:通过互联网的形式来获取和消费资源

### 1.2 服务器

上网过程中，负责存放和对外提供资源的电脑，叫做服务器。

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a5b9782c0e76464ea81bd4b28301b6bf~tplv-k3u1fbpfcp-watermark.image?)

### 1.3 客户端

上网过程中，负责获取和消费资源的电脑，叫做客户端。

## 2.URL地址

### 2.1 URL地址的概念

URL(全称是UniformResourceLocator)中文叫统一资源定位符，用于标识互联网上每个资源的唯一存放位置。浏览器只有通过URL地址，才能正确定位资源的存放位置，从而成功访问到对应的资源。

常见的URL举例: `http://www.baidu.com http://www.taobao.com http://www.cnblogs.com/liulongbinblogs/p/11649393.html `

### 2.2 URL地址的组成部分

URL地址一般由三部组成:

1.  客户端与服务器之间的通信协议
2.  存有该资源的服务器名称
3.  资源在服务器上具体的存放位置

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/56515c64df3840debd53e196a98ecc13~tplv-k3u1fbpfcp-zoom-1.image)

## 3. 客户端与服务器的通信过程

1.  打开Chrome浏览器
2.  Ctrl+Shift+l打开Chrome的开发者工具
3.  切换到Network面板
4.  选中Doc页签
5.  刷新页面，分析客户端与服务器的通信过程

## 4.服务器对外提供了哪些资源

### 4.1 例举网页中常见的资源

文字内容、Image图片、音频、视频

**数据也是一种资源**

### 4.2 网页中如何请求数据

数据，也是服务器对外提供的一种资源。只要是资源，必然要通过请求-处理-响应的方式进行获取。

如果要在网页中请求服务器上的数据资源，则需要用到`XMLHttpRequest`对象。 XMLHttpRequest(简称xhr）是浏览器提供的js成员，通过它，可以请求服务器上的数据资源。 最简单的用法`var xhrObj = new XMLHttpRequest()`

### 4.3 资源的请求方式

客户端请求服务器时，请求的方式有很多种，最常见的两种请求方式分别为get和post请求。 get请求通常用于获取服务端资源（向服务器要资源)

> 例如:根据URL地址，从服务器获取HTML文件、css文件、js文件、图片文件、数据资源等

post 请求通常用于向服务器提交数据(往服务器发送资源)

> 例如:登录时向服务器提交的登录信息、注册时向服务器提交的注册信息、添加用户时向服务器提交的用户信息等各种数据提交操作

## 5.了解Ajax

### 5.1 什么是Ajax

Ajax的全称是Asynchronous Javascript And XML(异步JavaScript和XML)。 通俗的理解:在网页中利用XMLHttpRequest对象和服务器进行数据交互的方式，就是Ajax

### 5.2 为什么要学Ajax

之前所学的技术，只能把网页做的更美观漂亮，或添加一些动画效果，但是，Ajax能让我们轻松实现网页与服务器之间的数据交互。

### 5.3 Ajax的典型应用场景

用户名检测:注册用户时，通过ajax的形式，动态检测用户名是否被占用

## 6. jQuery中的Ajax

### 6.1 了解jQuery中的Ajax

浏览器中提供的XMLHttpRequest用法比较复杂，所以jQuery对 XMLHttpRequest进行了封装，提供了一系列Ajax相关的函数，极大地降低了Ajax的使用难度。 jQuery中发起Ajax请求最常用的三个方法如下:

    //JavaScript
    $.get()
    $.post()
    $.ajax()

### 6.2 \$.get()函数的语法

jQuery 中 \$.get()函数的功能单一，专门用来发起get请求，从而将服务器上的资源请求到客户端来进行使用。 `$.get(url,[data],[callback])` 中方括号为可选项，其中，三个参数各自代表的含义如下:

| 参数名      | 参数类型     | 是否必选 | 说明           |
| :------- | :------- | :--- | :----------- |
| url      | string   | 是    | 要请求的资源地址     |
| data     | object   | 否    | 请求资源期间要携带的参数 |
| callback | function | 否    | 请求成功时的回调函数   |

#### 6.2.1 \$.get()发起不带参数的请求

使用\$.get(函数发起不带参数的请求时，直接提供请求的URL地址和请求成功之后的回调函娄 即可，示例代码如下:

    //JavaScript
    $.get('http://www.liulongbin.top:3006/api/getbooks', function(res) {
        console.log(res); // 这里的 res 是服务器返回的数据
    })

#### 6.2.2 \$.get()发起带参数的请求

使用 \$.get() 函数发起带参数的请求时，示例代码如下：

    //JavaScript
    $.get('http://www.liulongbin.top:3006/api/getbooks', { id: 1 }, function(res) {
        console.log(res);
     })

### 6.3 \$.post()函数的语法

jQuery 中 \$.post()函数的功能单一，专门用来发起post请求，从而向服务器提交数据。\$.post()函数的功能单一，专门用来发起post请求，从而向服务器提交数据。\$.post() 函数的语法如下：

`$.post(url, [data], [callback])`

其中，三个参数各自代表的含义如下：

| 参数名      | 参数类型     | 是否必选 | 说明           |
| :------- | :------- | :--- | :----------- |
| url      | string   | 是    | 提交数据的地址      |
| data     | object   | 否    | 要提交的数据       |
| callback | function | 否    | 数据提交成功时的回调函数 |

#### 6.3.1 \$.post()向服务器提交数据

使用 \$post() 向服务器提交数据的示例代码如下： 参数类型：对象

    //JavaScript
    $.post(   
        'http://www.liulongbin.top:3006/api/addbook', // 请求的URL地址
         { bookname: '水浒传', author: '施耐庵', publisher: '上海图书出版社' }, // 提交的数据
          function(res) { // 回调函数      
          console.log(res)；   
          } 
    )

### 6.4 \$.ajax()函数的语法

相比于 `$.get()` 和 `$.post()` 函数，jQuery 中提供的 `$.ajax()` 函数，是一个功能比较综合的函数，它允许我们对 Ajax 请求进行更详细的配置。 `$.ajax()` 函数的基本语法如下：

    $.ajax({
        type: '', // 请求的方式，例如 GET 或 POST
        url: '',  // 请求的 URL 地址
        data: { },// 这次请求要携带的数据
        success: function(res) { } // 请求成功之后的回调函数
    })

#### 6.4.1 使用\$.ajax()发起GET请求

用 \$.ajax() 发起 GET 请求时，只需要将 type 属性的值设置为 'GET' 即可

    //JavaScript
    $.ajax({
        type: 'GET', // 请求的方式
        url: 'http://www.liulongbin.top:3006/api/getbooks',  // 请求的 URL 地址
        data: { id: 1 },// 这次请求要携带的数据
        success: function(res) { // 请求成功之后的回调函数
        console.log(res)
        }
    })

#### 6.4.2 使用\$.ajax()发起POST请求

    //JavaScript
    $.ajax({
        type: 'POST', // 请求的方式
        url: 'http://www.liulongbin.top:3006/api/addbook',  // 请求的 URL 地址
        data: { // 要提交给服务器的数据
            bookname: '水浒传',
            author: '施耐庵',
            publisher: '上海图书出版社'
        },
        success: function(res) { // 请求成功之后的回调函数
            console.log(res)
        }
    }

## 7 接口

### 7.1 接口的概念

使用 Ajax 请求数据时，被请求的 URL 地址，就叫做数据接口（简称接口）。同时，每个接口必须有请求方式。 例如： `http://www.liulongbin.top:3006/api/getbooks`获取图书列表的接口(GET请求) `http://www.liulongbin.top:3006/api/addbook` 添加图书的接口（POST请求）

## 7.2 分析接口的请求过程

### 7.2.1 通过GET方式请求接口的过程

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4559147fe9e5403c81ec6d9c95f3bc4c~tplv-k3u1fbpfcp-zoom-1.image)

### 7.3 接口文档

#### 7.3.1.什么是接口文档

接口文档，顾名思义就是接口的说明文档，它是我们调用接口的依据。好的接口文档包含了对接口URL，参数以及输出内容的说明，我们参照接口文档就能方便的知道接口的作用，以及接口如何进行调用。

#### 7.3.2.接口文档的组成部分

接口文档可以包含很多信息，也可以按需进行精简，不过，一个合格的接口文档，应该包含以下6项内容，从而为接口的调用提供依据：

> 接口名称：用来标识各个接口的简单说明，如登录接口，获取图书列表接口等。
>
> 接口URL：接口的调用地址。
>
> 调用方式：接口的调用方式，如 GET 或 POST。
>
> 参数格式：接口需要传递的参数，每个参数必须包含参数名称、参数类型、是否必选、参数说明这4项内容。
>
> 响应格式：接口的返回值的详细描述，一般包含数据名称、数据类型、说明3项内容。
>
> 返回示例（可选）：通过对象的形式，例举服务器返回数据的结构。

## 8.案例

### 8.1 图书管理

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2b4dc7e171da456dbcfd357252780589~tplv-k3u1fbpfcp-zoom-1.image)

*   用到的 css 库 bootstrap.css
*   用到的 javascript 库 jquery.js
*   用到的 vs code 插件 Bootstrap 3 Snippets

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <link rel="stylesheet" href="./lib/bootstrap.css" />
  <script src="./lib/jquery.js"></script>
</head>

<body style="padding: 15px;">
  <!-- 添加图书的Panel面板 -->
  <div class="panel panel-primary">
    <div class="panel-heading">
      <h3 class="panel-title">添加新图书</h3>
    </div>
    <div class="panel-body form-inline">

      <div class="input-group">
        <div class="input-group-addon">书名</div>
        <input type="text" class="form-control" id="iptBookname" placeholder="请输入书名">
      </div>

      <div class="input-group">
        <div class="input-group-addon">作者</div>
        <input type="text" class="form-control" id="iptAuthor" placeholder="请输入作者">
      </div>

      <div class="input-group">
        <div class="input-group-addon">出版社</div>
        <input type="text" class="form-control" id="iptPublisher" placeholder="请输入出版社">
      </div>

      <button id="btnAdd" class="btn btn-primary">添加</button>

    </div>
  </div>


  <!-- 图书的表格 -->
  <table class="table table-bordered table-hover">
    <thead>
      <tr>
        <th>Id</th>
        <th>书名</th>
        <th>作者</th>
        <th>出版社</th>
        <th>操作</th>
      </tr>
    </thead>
    <tbody id="tb"></tbody>
  </table>

  <script>
  // 所有 jQuery 函数位于一个 document ready 函数中
  // 这是为了防止文档在完全加载（就绪）之前运行 jQuery 代码，即在 DOM 加载完成后才可以对 DOM 进行操作。
    $(function () {
      // 获取图书列表数据
      function getBookList() {
        $.get('http://www.liulongbin.top:3006/api/getbooks', function (res) {
          if (res.status !== 200) return alert('获取数据失败！')

          var rows = []
          $.each(res.data, function (i, item) {
            rows.push('<tr><td>' + item.id + '</td><td>' + 
            item.bookname + '</td><td>' + item.author + '</td<td>' 
            + item.publisher + '</td><td><a href="javascript:;"
            class="del" data-id="' + item.id + '">
            删除</a></td></tr>')
          })
          $('#tb').empty().append(rows.join(''))
        })
      }

      getBookList()

      /* $('.del').on('click', function () {
        console.log('ok')
      }) */

      // 通过代理的方式为动态添加的元素绑定点击事件
      $('tbody').on('click', '.del', function () {
        var id = $(this).attr('data-id')
        $.get('http://www.liulongbin.top:3006/api/delbook', { id: id }, function (res) {
          if (res.status !== 200) return alert('删除图书失败！')
          getBookList()
        })
      })

      $('#btnAdd').on('click', function () {
        var bookname = $('#iptBookname').val().trim()
        var author = $('#iptAuthor').val().trim()
        var publisher = $('#iptPublisher').val().trim()
        if (bookname.length <= 0 || author.length <= 0 || publisher.length <= 0) {
          return alert('请填写完整的图书信息！')
        }

        $.post('http://www.liulongbin.top:3006/api/addbook', { bookname: bookname, author: author, publisher: publisher }, function (res) {
          if (res.status !== 201) return alert('添加图书失败！')
          getBookList()
          $('#iptBookname').val('')
          $('#iptAuthor').val('')
          $('#iptPublisher').val('')
        })
      })
    })
  </script>

</body>

</html>
```

### 8.2 渲染图书列表（核心代码）

```js
function getBookList() {
    // 1. 发起 ajax 请求获取图书列表数据
    $.get('http://www.liulongbin.top:3006/api/getbooks', function(res) {
        // 2. 获取列表数据是否成功
        if (res.status !== 200) return alert('获取图书列表失败！')
        // 3. 渲染页面结构
        var rows = []
        $.each(res.data, function(i, item) { // 4. 循环拼接字符串
            rows.push('<tr><td>' + item.id + 
            '</td><td>' + item.bookname + '</td><td>' + 
            item.author + '</td><td>' + item.publisher + 
            '</td><td><a href="javascript:;" 
            class="del" data-id="'+ item.id +'">删除</a></td></tr>')
           })
        $('#bookBody').empty().append(rows.join('')) // 5. 渲染表格结构
    })
}
```

### 8.3 删除图书（核心代码)

W3C规范自定义属性 要以data-开头。

```js
//JavaScript
// 后期append的元素不能直接使用，因为可能还未被渲染上去
 //无法绑定 因为DOM元素.del（删除按钮）还未被渲染
     /**
     *  $('.del').on('click', function () {
     *       console.log('ok')
     *  })
     */

// 通过代理的方式为动态添加的元素绑定点击事件
$('tbody').on('click', '.del', function () {
//attr返回或设置一个属性 
var id = $(this).attr('data-id')
$.get('http://www.liulongbin.top:3006/api/delbook', { id: id }, function (res) {
  if (res.status !== 200) return alert('删除图书失败！')
  getBookList();
})
}
```

### 8.5 添加图书（核心代码）

```js
//JavaScript
// 1. 检测内容是否为空
var bookname = $('#bookname').val()
var author = $('#author').val()
var publisher = $('#publisher').val()
if (bookname === '' || author === '' || publisher === '') {
    return alert('请完整填写图书信息！')
}
// 2. 发起 ajax 请求，添加图书信息
$.post(
    'http://www.liulongbin.top:3006/api/addbook',
    { bookname: bookname, author: author, publisher: publisher },
        function(res) {
        // 3. 判断是否添加成功
        if (res.status !== 201) return alert('添加图书失败！')
            getBookList() // 4. 添加成功后，刷新图书列表
            $('input:text').val('') // 5. 清空文本框内容
            }    
)
```

## 9案例 – 聊天机器人

### 9.1 演示案例要完成的效果

> 实现步骤：
>
> 1.  梳理案例的代码结构
> 2.  将用户输入的内容渲染到聊天窗口
> 3.  发起请求获取聊天消息
> 4.  将机器人的聊天内容转为语音
> 5.  通过 `<audio>`播放语音
> 6.  使用回车键发送消息

### 9.2 梳理案例的代码结构

梳理页面的 UI 布局 将业务代码抽离到 chat.js 中

了解 resetui() 函数的作用

### 9.3 将用户输入的内容渲染到聊天窗口

```js
//JavaScript
// 为发送按钮绑定点击事件处理函数
$('#btnSend').on('click', function () {
    var text = $('#ipt').val().trim() // 获取用户输入的内容，trim去掉两端的空格
    if (text.length <= 0) { // 判断用户输入的内容是否为空
    // 如果为空，什么都不发送，清空输入框
       return $('#ipt').val('')
    }
    // 将用户输入的内容显示到聊天窗口中
    $('#talk_list').append('<li class="right_word"><img src="img/person02.png" /> <span>' + text + '</span></li>')
    resetui() // 重置滚动条的位置
    $(‘#ipt’).val('') // 清空输入框的内容
// TODO: 发起请求，获取机器人聊天消息
})    
```

### 9.4 发起请求获取机器人的聊天消息

```JavaScript
function getMsg(text) {
    $.ajax({
      method: 'GET',
      url: 'http://ajax.frontend.itheima.net:3006/api/robot',
      data: {
        spoken: text
      },
      success: function (res) {
        if (res.message === 'success') {
            var msg = res.data.info.text
            $('#talk_list').append('<li class="left_word"><img src="img/person01.png" /> <span>' + msg + '</span></li>')
            resetui()
            // TODO: 发起请求，将机器人的聊天消息转为语音格式
        }
      }
    })
```

### 9.5 将机器人的聊天内容转为语音

```JavaScript
function getVoice(text) {
    $.ajax({
      method: 'GET',
      url: 'http://ajax.frontend.itheima.net:3006/api/synthesize',
      data: {
        text: text
      },
      success: function (res) {
// 如果请求成功，则 res.voiceUrl 是服务器返回的音频 URL 地址
        if (res.status === 200) {
        // attr（key,value）设置一个属性的值
            $('#voice').attr('src', res.voiceUrl)
        }
      }
    })
  }
```

### 9.6 通过 `<audio>` 播放语音

`<audio src="" id="voice" autoplay style="display: none;"></audio>`

### 9.7 使用回车发送消息

```JavaScript
// 让文本输入框响应回车事件后，提交消息
$('#ipt').on('keyup', function (e) {
// e.keyCode 可以获取到当前按键的编码
    if (e.keyCode === 13) {
// 调用按钮元素的 click 函数，可以通过编程的形式触发按钮的点击事件
        $('#btnSend').click()
    }
})
```

# 二、form表单与模板引擎

## 1. form表单的基本使用

### 1.1 什么是表单

表单在网页中主要负责数据采集功能。HTML中的`<form>`标签，就是用于采集用户输入的信息，并通过`<form>`标签的提交操作，把采集到的信息提交到服务器端进行处理。

```html
 <form>
     <input type="text" name="email_or_mobile" />
     <input type="password" name="password" />
     <input type="checkbox" name="remember_me" checked />
     <button type="submit">提交</button>
 </form>
```

### 1.2表单的组成部分

> 表单由三个基本部分组成：
>
> 表单标签 form
>
> 表单域：包含了文本框、密码框、多行文本框、复选框
>
> 表单按钮

### 1.3 `<form>`标签的属性

`<form>标签用来采集数据，<form>标签的属性则是用来规定如何把采集到的数据发送到服务。`

| 属性      | 值                                                                | 描述                        |
| :------ | :--------------------------------------------------------------- | :------------------------ |
| action  | url地址                                                            | 规定当提交表单时，向何处发送表单数据        |
| method  | get或post                                                         | 规定以何种方式把表单数据提交到Action URL |
| enctype | application/x-www-form-urlencoded multipart/form-data text/plain | 规定在发送表单数据之前如何对其进行编码       |
| target  | \_blank \_self \_parent\_top framename                           | 规定在何处打开 action URL        |

```html
 <form action="/login" target="_blank">
     <input type="text" name="email_or_mobile" />
     <input type="password" name="password" />
     <input type="checkbox" name="remember_me" checked />
     <button type="submit">提交</button>
 </form>
```

#### 1.3.1 action

action属性用来规定当提交表单时，**向何处发送表单数据**。

action属性的值应该是后端提供的一个URL地址，这个URL地址专门负责接收表单提交过来的数据。当`<form>`表单在未指定 action属性值的情况下，action的默认值为当前页面的URL地址。

\==注意==: 当提交表单后，页面会立即跳转到action属性指定的URL地址

如果不指定action属性，表单的数据会提交到当前页面的url中。

#### 1.3.2 target

target属性用来规定在何处打开action URL。 它的可选值有5个，默认情况下，target 的值是\_self，表示在相同的框架中打开action URL

| 值         | 描述              |
| --------- | --------------- |
| \_blank   | 在新窗口中打开。        |
| \_self    | 默认。在相同的框架打开。    |
| \_parent  | 在父框架集中打开。(很少用)  |
| \_top     | 在整个窗口中打开。(很少用)  |
| framename | 在指定的框架中打开。(很少用) |

#### 1.3.3 method

*   method属性用来规定以**何种方式**把表单数据提交到action URL.
*   它的可选值有两个，分别是`get`和`post`。
*   默认情况下，method 的值为get，表示通过URL地址的形式，把表单数据提交到action URL。

注意:

get方式适合用来提交少量的、简单的数据. Post方式适合用来提交大量的、复杂的、或包含文件上传的数据。 在实际开发中，`<form>`表单的post提交方式用的最多，很少用get。例如登录、注册、添加数据等表单操作，都需要使用post方式来提交表单。

#### 1.3.4 enctype

> enctype属性用来规定在发送表单数据之前如何对数据进行编码。 它的可选值有三个，默认情况下，enctype 的值为 application/x-www-form-urlencoded, 表示在发送前编码所有的字符。

| 值                                 | 描述                              |
| --------------------------------- | ------------------------------- |
| application/x-www-form-urlencoded | 在发送前编码所有疗符(默认)                  |
| multipart/form-data               | 不对字符编码. 在使用包含文件上传控件的表单时，必须使用该值。 |
| text/plain                        | 空格转换为“+”加号，但不对特殊字符编码。(很少用)      |

注意:

在涉及到文件上传的操作时，必须将enctype 的值设置为multipart/form-data\
如果表单的提交不涉及到文件上传操作，则直接将enctype的值设置为 application/x-www-form-urlencoded即可!

### 1.4表单的同步提交及缺点

#### 1.4.1 什么是表单的同步提交

通过点击submit按钮，触发表单提交的操作，从而使页面跳转到action URL的行为，叫做表单的同步提交。

#### 1.4.2 表单同步提交的缺点

①`<form>`表单同步提交后，整个页面会发生跳转，跳转到action URL所指向的地址，用户体验很差。\
②`<form>`表单同步提交后，页面之前的状态和数据会丢失。

思考：如何解决表单提交的问题

#### 1.4.3 如何解决表单同步提交的缺点

如果使用表单提交数据，则会导致以下两个问题:

`①:页面会发生跳转` `②页面之前的状态和数据会丢失`

解决方案: **表单只负责采集数据，Ajax负责将数据提交到服务器**。

## 2.通过Ajax提交表单数据

### 2.1监听表单提交事件

在jQuery中，可以使用如下两种方式，监听到表单的提交事件:

```js
$('#form1').submit(function(e) {
   alert('监听到了表单的提交事件')
})

$('#form1').on('submit', function(e) {
   alert('监听到了表单的提交事件')
})
```

### 2.2 阻止表单默认提交行为

当监听到表单的提交事件以后，可以调用事件对象的event.preventDefault()函数，来阻止表单的提交和页面的跳转，示例码如下:

```js
$('#form1').submit(function(e) {
   // 阻止表单的提交和页面的跳转
   e.preventDefault()
})

$('#form1').on('submit', function(e) {
   // 阻止表单的提交和页面的跳转
   e.preventDefault()
})
```

### 2.3 快速获取表单中的数据

####  2.3.1 serialize()函数

为了简化表单中数据的获取操作，jQuery提供了serialize()函数，其语法格式如下: `$(selector).serialize()` serialize() 函数的好处：可以一次性获取到表单中的所有的数据。

#### 2.3.2 serialize()函数示例

    <!-- HTML -->
    <form id="form1">
        <input type="text" name="username" />
        <input type="password" name="password" />
        <button type="submit">提交</button>
    </form>

<!---->

    //JavaScript
    $('#form1').serialize()
    // 调用的结果：
    // username=用户名的值&password=密码的值

注意：在使用 serialize() 函数快速获取表单数据时，必须为每个表单元素添加 name 属性！

## 3 案例-评论列表

### 3.1 渲染UI结构

*   使用 `bs3-panel`生成一个panel面板

### 3.2 获取评论列表

```JavaScript
function getCmtList() {
    $.get('http://www.liulongbin.top:3006/api/cmtlist', function (res) {  
      if(res.status !== 200) {
        return alert('获取评论列表失败！')
      }
      var rows = []
      $.each(res.data, function (i, item) { // 循环拼接字符串
        rows.push('<li class="list-group-item">'+ item.content +'<span class="badge cmt-date">评论时间：'+ item.time +'</span><span class="badge cmt-person">评论人：'+ item.username +'</span></li>')
      })
      $('#cmt-list').empty().append(rows.join('')) // 渲染列表的UI结构
    })
  }
```

### 3.3 发表评论

```JavaScript
$('#formAddCmt').submit(function(e) {
    e.preventDefault() // 阻止表单的默认提交行为
    // 快速得到表单中的数据
    var data = $(this).serialize()
    $.post('http://www.liulongbin.top:3006/api/addcmt', data, function(res) {
      if (res.status !== 201) {
        return alert('发表评论失败！')
      }
      // 刷新评论列表
      getCmtList()
      // 快速清空表单内容  $('#formAddCmt')[0] JQuery对象转DOM对象 使用DOM对象的reset();
      $('#formAddCmt')[0].reset()
    })
  })
```

## 4.模板引擎的基本概念

###  4.1渲染U结构时遇到的问题

    //JavaScript
    var rows = []
    $.each(res.data, function (i, item) { // 循环拼接字符串
        rows.push('<li class="list-group-item">'+ item.content +'<span class="badge cmt-date">评论时间：'+ item.time +'</span><span class="badge cmt-person">评论人：'+ item.username +'</span></li>')
    })
    $('#cmt-list').empty().append(rows.join('')) // 渲染列表的UI结构

*   上述代码是通过`字符串拼接`的形式，来渲染UI结构。
*   如果UI结构比较复杂，则拼接字符串的时候需要格外注意`引号之前的嵌套`。且一旦需求发生变化，`修改起来也非常麻烦`。

***

### 4.2 什么是模板引擎

*   模板引擎，顾名思义，它可以根据程序员指定的模板结构和数据，自动生成一个完整的HTML页面。
*   Vue是前后端分离的，并且Vue的功能作为简化前端开发和实现前后端分离的一种工具，功能十分强大，包括但不仅限于数据的接收与渲染。而**模板引擎只是一个提供简单的数据解析和渲染语法的工具**。

## 5.art-template模板引擎

### 5.1 art-template简介

art-template 是一个简约、超快的模板引擎。中文官网首页为 [http://aui.github.io/art-template/zh-cn/index.html](https://gitee.com/link?target=http%3A%2F%2Faui.github.io%2Fart-template%2Fzh-cn%2Findex.html)

***

### 5.2 art-template的安装

在浏览器中访问 `http://aui.github.io/art-template/zh-cn/docs/installation.html`页面，找到下载链接后，鼠标右键，选择“链接另存为”，将 art-template 下载到本地，然后，通过 `<script>`标签加载到网页上进行使用。

### 5.3 art-template模板引擎的基本使用

#### 5.3.1. 使用传统方式渲染UI结构

用户信息 姓名︰zS年龄:20会员:否 注册时间:2019-10-28 爱好: 吃饭睡觉打豆豆

    var data = {
       title: '<h3>用户信息</h3>',
       name: 'zs',
       age: 20,
       isVIP: true,
       regTime: new Date(),
       hobby: ['吃饭', '睡觉', '打豆豆']
    }

*   传统方式存在的问题，程序员需要手动操作DOM。模板引擎可以减少DOM操作。

#### 5.3.2 art-template的使用步骤

*   导入 art-template
*   定义数据
*   定义模板
*   调用 template 函数
*   渲染HTML结构

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <!-- 1. 导入模板引擎 -->
  <!-- 在 window 全局，多一个函数，叫做 template('模板的Id', 需要渲染的数据对象) -->
  <script src="./lib/template-web.js"></script>
  <script src="./lib/jquery.js"></script>
</head>

<body>

  <div id="container"></div>

  <!-- 3. 定义模板 -->
  <!-- 3.1 模板的 HTML 结构，必须定义到 script 中 -->
  <script type="text/html" id="tpl-user">
    <h1>{{name}}    ------    {{age}}</h1>
    {{@ test}}

    <div>
      {{if flag === 0}}
      flag的值是0
      {{else if flag === 1}}
      flag的值是1
      {{/if}}
    </div>

    <ul>
      {{each hobby}}
      <li>索引是:{{$index}}，循环项是:{{$value}}</li>
      {{/each}}
    </ul>

    <h3>{{regTime | dateFormat}}</h3>
  </script>

  <script>
    // 定义处理时间的过滤器
    template.defaults.imports.dateFormat = function (date) {
      var y = date.getFullYear()
      var m = date.getMonth() + 1
      var d = date.getDate()

      return y + '-' + m + '-' + d
    }


    // 2. 定义需要渲染的数据
    var data = { name: 'zs', age: 20, test: '<h3>测试原文输出</h3>', flag: 1, hobby: ['吃饭', '睡觉', '写代码'], regTime: new Date() }

    // 4. 调用 template 函数
    var htmlStr = template('tpl-user', data)
    console.log(htmlStr)
    // 5. 渲染HTML结构
    $('#container').html(htmlStr)
  </script>
</body>

</html>
```

### 5.4 art-template标准语法

#### 5.4.1 什么是标准语法

art-template 提供了 `{{ }}` 这种语法格式，在 `{{ }}` 内可以进行变量输出，或循环数组等操作，这种 `{{ }}` 语法在 art-template 中被称为标准语法。

#### 5.4.2 标准语法 - 输出

    {{value}}  //输出该对象
    {{obj.key}} //输出对象.属性
    {{obj['key']}} //输出对象[]属性
    {{a ? b : c}}
    {{a || b}}
    {{a + b}}

在`{{ }}`语法中，可以进行变量的输出、对象属性的输出、三元表达式输出、逻辑或输出、加减乘除等表达式输出。

#### 5.4.3 标准语法 – 原文输出

`{{@ value }}` 如果要输出的 value 值中，包含了 **HTML** 标签结构，则需要使用原文输出语法，才能保证 HTML 标签被正常渲染。

#### 5.4.4 标准语法 – 条件输出

如果要实现条件输出，则可以在 `{{ }}` 中使用 if … else if … /if 的方式，进行按需输出。

    {{if value}} 按需输出的内容 {{/if}}

    {{if v1}} 按需输出的内容 {{else if v2}} 按需输出的内容 {{/if}}

#### 5.4.5 标准语法 – 循环输出

如果要实现循环输出，则可以在 `{{ }}` 内，通过 each 语法循环数组，当前循环的索引使用 `$index` 进行访问， 当前的循环项使用 `$value` 进行访问。

```js
    {{each arr}}
        {{$index}} {{$value}}
    {{/each}}
```
#### 5.4.6 标准语法--过滤器
![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a8bf74a299ba41edbcd02023bb3777c4~tplv-k3u1fbpfcp-zoom-1.image)
-   过滤器的本质，就是一个 function 处理函数。

* * *

`{{value | filterName}}`

过滤器语法类似管道操作符，它的上一个输出作为下一个输入。 定义过滤器的基本语法如下：

`template.defaults.imports.filterName = function(value){/*return处理的结果*/}`

* * *

`<div>注册时间：{{regTime | dateFormat}}</div>` 定义一个格式化时间的过滤器 dateFormat 如下：

```
 template.defaults.imports.dateFormat = function(date) {
    var y = date.getFullYear()
    var m = date.getMonth() + 1
    var d = date.getDate()

    return y + '-' + m + '-' + d // 注意，过滤器最后一定要 return 一个值
 }
```
## 1. XMLHttpRequest的基本使用

### 1.1 什么XMLHttpRequest

XMLHttpRequest（简称 xhr）是浏览器提供的 Javascript 对象，通过它，可以请求服务器上的数据资源。之前所学的 jQuery 中的 Ajax 函数，就是基于 xhr 对象封装出来的。

### 1.2 使用xhr发起GET请求

步骤：

1.  创建 xhr 对象
1.  调用 xhr.open() 函数
1.  调用 xhr.send() 函数
1.  监听 xhr.onreadystatechange 事件

```js
// 1. 创建 XHR 对象

var xhr = new XMLHttpRequest()
// 2. 调用 open 函数，指定 请求方式 与 URL地址
xhr.open('GET', 'http://www.liulongbin.top:3006/api/getbooks')
// 3. 调用 send 函数，发起 Ajax 请求
xhr.send()
// 4. 监听 onreadystatechange 事件
xhr.onreadystatechange = function() {
    // 4.1 监听 xhr 对象的请求状态 readyState ；与服务器响应的状态 status
    if (xhr.readyState === 4 && xhr.status === 200) {
        // 4.2 打印服务器响应回来的数据
        console.log(xhr.responseText)
    }
}
```
### 1.3 了解xhr对象的readyState属性

XMLHttpRequest 对象的 readyState 属性，用来表示当前 Ajax 请求所处的状态。每个 Ajax 请求必然处于以下状态中的一个：

| 值 | 状态               | 描述                                  |
| - | ---------------- | ----------------------------------- |
| 0 | UNSENT           | XMLHttpRequest 对象已被创建，但尚未调用 open方法。 |
| 1 | OPENED           | open() 方法已经被调用。                     |
| 2 | HEADERS_RECEIVED | send() 方法已经被调用，响应头也已经被接收。           |
| 3 | LOADING          | 数据接收中，此时 response 属性中已经包含部分数据。      |
| 4 | DONE             | Ajax 请求完成，这意味着数据传输已经彻底完成或失败。

### 1.4 使用xhr发起带参数的GET请求

使用 xhr 对象发起带参数的 GET 请求时，只需在调用 xhr.open 期间，为 URL 地址指定参数即可：

```js
// ...省略不必要的代码
xhr.open('GET', 'http://www.liulongbin.top:3006/api/getbooks?id=1')
// ...省略不必要的代码
```

这种在 URL 地址后面拼接的参数，叫做==查询字符串==。
### 1.5 查询字符串

#### 1.5.1 什么是查询字符串

定义：查询字符串（URL 参数）是指在 URL 的末尾加上用于向服务器发送信息的字符串（变量）。 

格式：将英文的 ? 放在URL 的末尾，然后再加上 参数＝值 ，想加上多个参数的话，使用 & 符号进行分隔。以这个形式，可以将想要发送给服务器的数据添加到 URL 中。

```
// 不带参数的 URL 地址
http://www.liulongbin.top:3006/api/getbooks
// 带一个参数的 URL 地址
http://www.liulongbin.top:3006/api/getbooks?id=1
// 带两个参数的 URL 地址
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=西游记
```

#### 1.5.2. GET请求携带参数的本质

无论使用 `$.ajax()`，还是使用 `$.get()`，又或者直接使用 xhr 对象发起 GET 请求，当需要携带参数的时候，本质上，都是直接将参数以查询字符串的形式，追加到 URL 地址的后面，发送到服务器的。

```
$.get('url', {name: 'zs', age: 20}, function() {})
// 等价于
$.get('url?name=zs&age=20', function() {})

$.ajax({ method: 'GET', url: 'url', data: {name: 'zs', age: 20}, success: function() {} })
// 等价于
$.ajax({ method: 'GET', url: 'url?name=zs&age=20', success: function() {} })
```
### 1.6 URL编码与解码

#### 1.6.1 什么是URL编码

-   URL 地址中，只允许出现英文相关的字母、标点符号、数字，因此，在 URL 地址中不允许出现中文字符。
-   如果 URL 中需要包含中文这样的字符，则必须对中文字符进行编码（转义）。
-   URL编码的原则：使用安全的字符（没有特殊用途或者特殊意义的可打印字符）去表示那些不安全的字符。
-   URL编码原则的通俗理解：使用英文字符去表示非英文字符。

```
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=西游记
// 经过 URL 编码之后，URL地址变成了如下格式：中文字符编码是三组百分号
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=%E8%A5%BF%E6%B8%B8%E8%AE%B0
```

####  1.6.2 如何对URL进行编码与解码

浏览器提供了 URL 编码与解码的 API，分别是： encodeURI() 编码的函数 decodeURI() 解码的函数

```js
encodeURI('黑马程序员')
// 输出字符串  %E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98
decodeURI('%E9%BB%91%E9%A9%AC')
// 输出字符串  黑马
```

####  1.6.3 URL编码的注意事项

由于浏览器会自动对 URL 地址进行编码操作，因此，大多数情况下，程序员不需要关心 URL 地址的编码与解码操作。

更多关于 URL 编码的知识，请参考如下博客： https://blog.csdn.net/Lxd_0111/article/details/78028889

### 1.7 使用xhr发起POST请求

步骤：

1.  创建 xhr 对象
1.  调用 xhr.open() 函数
1.  设置 Content-Type 属性（固定写法）
1.  调用 xhr.send() 函数，同时指定要发送的数据
1.  监听 xhr.onreadystatechange 事件

```js
// 1. 创建 xhr 对象
var xhr = new XMLHttpRequest()
// 2. 调用 open()
xhr.open('POST', 'http://www.liulongbin.top:3006/api/addbook')
// 3. 设置 Content-Type 属性（固定写法）
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
// 4. 调用 send()，同时将数据以查询字符串的形式，提交给服务器
xhr.send('bookname=水浒传&author=施耐庵&publisher=天津图书出版社')
// 5. 监听 onreadystatechange 事件
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(xhr.responseText)
    }
}
```
## 2. 数据交换格式

###  2.1 什么是数据交换格式

数据交换格式，就是服务器端与客户端之间进行数据传输与交换的格式。 前端领域，经常提及的两种数据交换格式分别是 XML 和 JSON。其中 XML 用的非常少，所以，我们重点要学习的数据交换格式就是 **JSON**。
### 2.2 XML

###  2.2.1 什么是XML

XML 的英文全称是 EXtensible Markup Language，即可扩展标记语言。因此，XML 和 HTML 类似，也是一种标记语言。

```
<!DOCTYPE html>
<html>
  <head>
    <title>Document</title>
  </head>
  <body></body>
</html>
```

```
<note>
  <to>ls</to>    //从谁
  <from>zs</from>  //到谁
  <heading>通知</heading> //标题
  <body>晚上开会</body>   //内容 
</note>
```

### 2.2.2 XML和HTML的区别

XML 和 HTML 虽然都是标记语言，但是，它们两者之间没有任何的关系。

-   HTML 被设计用来描述网页上的内容，是网页内容的载体
-   XML 被设计用来传输和存储数据，是数据的载体

### 2.2.3 XML的缺点


1.  XML 格式臃肿，和数据无关的代码多，体积大，传输效率低
1.  在 Javascript 中解析 XML 比较麻烦

### 2.3 JSON

#### 2.3.1 什么是JSON

-   概念：JSON 的英文全称是 JavaScript Object Notation，即“JavaScript 对象表示法”。简单来讲，JSON 就是 Javascript 对象和数组的字符串表示法，它使用文本表示一个 JS 对象或数组的信息，因此，**JSON 的本质是字符串**。
-   作用：JSON 是一种轻量级的文本数据交换格式，在作用上类似于 XML，专门用于存储和传输数据，但是 JSON 比 XML 更小、更快、更易解析。
-   现状：JSON 是在 2001 年开始被推广和使用的数据格式，到现今为止，JSON 已经成为了主流的数据交换格式。

#### 2.3.2 JSON的两种结构

JSON 就是用字符串来表示 Javascript 的对象和数组。所以，JSON 中包含对象和数组两种结构，通过这两种结构的相互嵌套，可以表示各种复杂的数据结构。

==对象结构==：对象结构在 JSON 中表示为 `{ }` 括起来的内容。数据结构为 `{ key: value, key: value, … }` 的键值对结构。其中，key 必须是使用英文的双引号包裹的字符串，value 的数据类型可以是数字、字符串、布尔值、null、数组、对象6种类型。

```json
//不合法的案例
{
    name: "zs",
    'age': 20,
    "gender": '男',
    "address": undefined,
    "hobby": ["吃饭", "睡觉", '打豆豆']
    say: function() {}
}
//标准的JSON案例
{
    "name": "zs",
    "age": 20,
    "gender": "男",
    "address": null,
    "hobby": ["吃饭", "睡觉", "打豆豆"]
}
```

==数组结构==：数组结构在 JSON 中表示为 [ ] 括起来的内容。数据结构为 [ "java", "javascript", 30, true … ] 。数组中数据的类型可以是数字、字符串、布尔值、null、数组、对象6种类型。

```
[ "java", "python", "php" ]
[ 100, 200, 300.5 ]
[ true, false, null ]
[ { "name": "zs", "age": 20}, { "name": "ls", "age": 30} ]
[ [ "苹果", "榴莲", "椰子" ], [ 4, 50, 5 ] ]
```
#### 2.3.3 JSON语法注意事项

1.  属性名必须使用双引号包裹
1.  字符串类型的值必须使用双引号包裹
1.  JSON 中不允许使用单引号表示字符串
1.  JSON 中不能写注释
1.  JSON 的最外层必须是对象或数组格式
1.  不能使用 undefined 或函数作为 JSON 的值

JSON 的作用：在计算机与网络之间存储和传输数据。 **JSON 的本质：用字符串来表示 Javascript 对象数据或数组数据。**

#### 2.3.4 JSON和JS对象的关系

JSON 是 JS 对象的字符串表示法，它使用文本表示一个 JS 对象的信息，本质是一个字符串。例如：

```js
//这是一个对象
var obj = {a: 'Hello', b: 'World'}

//这是一个 JSON 字符串，本质是一个字符串
var json = '{"a": "Hello", "b": "World"}'
```
#### 2.3.5 JSON和JS对象的互转

要实现从 JSON 字符串转换为 JS 对象，使用 JSON.parse() 方法：

```js
var obj = JSON.parse('{"a": "Hello", "b": "World"}')
//结果是 {a: 'Hello', b: 'World'}
```

要实现从 JS 对象转换为 JSON 字符串，使用 JSON.stringify() 方法：

```js
var json = JSON.stringify({a: 'Hello', b: 'World'})
//结果是 '{"a": "Hello", "b": "World"}'
```
#### 2.3.6 序列化和反序列化

把数据对象转换为字符串的过程，叫做序列化，例如：调用 JSON.stringify() 函数的操作，叫做 JSON 序列化。 把字符串转换为数据对象的过程，叫做反序列化，例如：调用 JSON.parse() 函数的操作，叫做 JSON 反序列化。
## 3. 封装自己的Ajax函数

###  3.1 要实现的效果

```js
<!-- 1. 导入自定义的ajax函数库 -->
<script src="./itheima.js"></script>

<script>
    // 2. 调用自定义的 itheima 函数，发起 Ajax 数据请求
    itheima({
        method: '请求类型',
        url: '请求地址',
        data: { /* 请求参数对象 */ },
        success: function(res) { // 成功的回调函数
            console.log(res)     // 打印数据
        }
    })
</script>
```

###  3.2 定义options参数选项

itheima() 函数是我们自定义的 Ajax 函数，它接收一个配置对象作为参数，配置对象中可以配置如下属性：

-   method 请求的类型
-   url 请求的 URL 地址
-   data 请求携带的数据
-   success 请求成功之后的回调函数

###  3.3 处理data参数

需要把 data 对象，转化成查询字符串的格式，从而提交给服务器，因此提前定义 resolveData 函数如下：

```js
/**
 * 处理 data 参数
 * @param {data} 需要发送到服务器的数据
 * @returns {string} 返回拼接好的查询字符串 name=zs&age=10
 */
function resolveData(data) {
  var arr = []
  for (var k in data) {
    arr.push(k + '=' + data[k])
  }
  return arr.join('&')
}
```

### 3.4 定义itheima函数

在 itheima() 函数中，需要创建 xhr 对象，并监听 onreadystatechange 事件：

```js
function itheima(options) {
  var xhr = new XMLHttpRequest()
  // 拼接查询字符串
  var qs = resolveData(options.data)

  // 监听请求状态改变的事件
  xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
      var result = JSON.parse(xhr.responseText)
      options.success(result)
    }
  }
}
```

###  3.5 判断请求的类型

不同的请求类型，对应 xhr 对象的不同操作，因此需要对请求类型进行 if … else … 的判断：

```js
 if (options.method.toUpperCase() === 'GET') {
    // 发起 GET 请求
    xhr.open(options.method, options.url + '?' + qs)
    xhr.send()
  } else if (options.method.toUpperCase() === 'POST') {
    // 发起 POST 请求
    xhr.open(options.method, options.url)
    xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
    xhr.send(qs)
  }
```

## 4. XMLHttpRequest Level2的新特性

###  4.1 认识XMLHttpRequest Level2

####  4.1.1 旧版XMLHttpRequest的缺点

1.  只支持文本数据的传输，无法用来读取和上传文件
1.  传送和接收数据时，没有进度信息，只能提示有没有完成

#### 4.1.2 XMLHttpRequest Level2的新功能

-   可以设置 HTTP 请求的时限
-   可以使用 FormData 对象管理表单数据
-   可以上传文件
-   可以获得数据传输的进度信息


## 6. axios

### 6.1 什么是axios

Axios 是专注于网络数据请求的库。 相比于原生的 XMLHttpRequest 对象，axios 简单易用。 相比于 jQuery，axios 更加轻量化，只专注于网络数据请求 

### 6.2 axios发起GET请求

axios 发起 get 请求的语法：

`axios.get('url', { params: { /*参数*/ } }).then(callback)`

具体的请求示例如下：
```js
 // 请求的 URL 地址
 var url = 'http://www.liulongbin.top:3006/api/get'
 // 请求的参数对象
 var paramsObj = { name: 'zs', age: 20 }
 // 调用 axios.get() 发起 GET 请求
 axios.get(url, { params: paramsObj }).then(function(res) {
     // res.data 是服务器返回的数据
     var result = res.data
     console.log(res)
 })
```
### 6.3 axios发起POST请求

axios 发起 post 请求的语法：

`axios.post('url', { /*参数*/ }).then(callback)`

具体的请求示例如下：

```js
 // 请求的 URL 地址
 var url = 'http://www.liulongbin.top:3006/api/post'
 // 要提交到服务器的数据
 var dataObj = { location: '北京', address: '顺义' }
 // 调用 axios.post() 发起 POST 请求
 axios.post(url, dataObj).then(function(res) {
     // res.data 是服务器返回的数据
     var result = res.data
     console.log(result)
 })
```

###  6.4 直接使用axios发起请求

axios 也提供了类似于 jQuery 中 $.ajax() 的函数，语法如下：

```js
 axios({
     method: '请求类型',
     url: '请求的URL地址',
     data: { /* POST数据 */ },
     params: { /* GET参数 */ }
 }) .then(callback)
```

####  6.4.1 直接使用axios发起GET请求

```js
 axios({
     method: 'GET',
     url: 'http://www.liulongbin.top:3006/api/get',
     params: { // GET 参数要通过 params 属性提供
         name: 'zs',
         age: 20
     }
 }).then(function(res) {
     console.log(res.data)
 })
```

####  6.4.2 直接使用axios发起POST请求

```js
 axios({
     method: 'POST',
     url: 'http://www.liulongbin.top:3006/api/post',
     data: { // POST 数据要通过 data 属性提供
         bookname: '程序员的自我修养',
         price: 666
     }
 }).then(function(res) {
     console.log(res.data)
 })
```