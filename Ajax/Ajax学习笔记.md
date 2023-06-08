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

#### [](https://gitee.com/AuroraManito/note/blob/master/sgg/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98AJAX%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%88%B0%E7%B2%BE%E9%80%9A_%E6%95%B4%E5%90%88Git%E6%A0%B8%E5%BF%83%E5%86%85%E5%AE%B9%E5%85%A8%E5%A5%97%E6%95%99%E7%A8%8B/%E5%AD%A6%E4%B9%A0%E7%9B%AE%E6%A0%872-form%E8%A1%A8%E5%8D%95%E4%B8%8E%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.md#231-serialize%E5%87%BD%E6%95%B0)2.3.1 serialize()函数

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

### [](https://gitee.com/AuroraManito/note/blob/master/sgg/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98AJAX%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%88%B0%E7%B2%BE%E9%80%9A_%E6%95%B4%E5%90%88Git%E6%A0%B8%E5%BF%83%E5%86%85%E5%AE%B9%E5%85%A8%E5%A5%97%E6%95%99%E7%A8%8B/%E5%AD%A6%E4%B9%A0%E7%9B%AE%E6%A0%872-form%E8%A1%A8%E5%8D%95%E4%B8%8E%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.md#41%E6%B8%B2%E6%9F%93u%E7%BB%93%E6%9E%84%E6%97%B6%E9%81%87%E5%88%B0%E7%9A%84%E9%97%AE%E9%A2%98)4.1渲染U结构时遇到的问题

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