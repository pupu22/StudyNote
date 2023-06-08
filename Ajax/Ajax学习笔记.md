视频地址：[黑马ajax](https://www.bilibili.com/video/BV1zs411h74a/?p=2\&spm_id_from=pageDriver\&vd_source=c8b9ba4c470a783033f0287d1c7b102b)

笔记地址：[ajax笔记](https://gitee.com/AuroraManito/note/tree/master/sgg/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98AJAX%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%88%B0%E7%B2%BE%E9%80%9A_%E6%95%B4%E5%90%88Git%E6%A0%B8%E5%BF%83%E5%86%85%E5%AE%B9%E5%85%A8%E5%A5%97%E6%95%99%E7%A8%8B)

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
> 1.  将用户输入的内容渲染到聊天窗口
> 1.  发起请求获取聊天消息
> 1.  将机器人的聊天内容转为语音
> 1.  通过 `<audio>`播放语音
> 1.  使用回车键发送消息

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

``` JavaScript
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