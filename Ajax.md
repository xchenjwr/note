# AJAX如何工作？

AJAX 使用的 XMLHttpRequest 的对象与服务器通信。

1.用户从 UI 发送请求，JavaScript 中调用 XMLHttpRequest 对象。
2.HTTP 请求由 XMLHttpRequest 对象发送到服务器。
3.服务器使用 JSP，PHP，Servlet，ASP.net 等与数据库交互。
4.检索数据。
5.服务器将 XML 数据或 JSON 数据发送到 XMLHttpRequest 回调函数。
6.HTML 和 CSS 数据显示在浏览器上。

# 向服务器发送请求
**XMLHttpRequest **对象用于和服务器交换数据。
当你的页面全部加载完毕后，客户端会通过 XMLHttpRequest 对象向服务器请求数据，服务器端接受数据并处理后，向客户端反馈数据。
如需将请求发送到服务器，我们使用 XMLHttpRequest 对象的open()和send()方法：

| 方法                   | 属性                                       |
| ---------------------- | ------------------------------------------ |
| open(method,url,async) | 规定请求的类型、URL 以及是否异步处理请求。method:请求的类型，url：请求文件的位置，async：true为异步，false为同步|
| send(string)           | 将请求发送到服务器。string：仅用于 POST 请求	    |
## GET请求

```js
xhr.open("get", "checkUsername.php?username=" + username, true);
xhr.send(null);
```

## POST请求

```js
// 不传数据
xmlhttp.open("POST","demo_post.html",true);
xmlhttp.send(null);
// 传数据
xmlhttp.open("POST","ajax_test.html",true);
xmlhttp.setRequestHeader("Content-type","application/x-www-form-urlencoded");
xmlhttp.send("fname=Henry&lname=Ford");
```
# onreadystatechange 事件

　当发送一个请求后，客户端需要确定这个请求什么时候会完成，因此，XMLHttpRequest对象提供了onreadystatechange事件机制来捕获请求的状态，继而实现响应。
当请求被发送到服务器时，我们需要执行一些基于响应的任务。
**每当**readyState改变时，就会触发onreadystatechange事件。
readyState属性存有 XMLHttpRequest 的状态信息。

| 方法               | 属性                                                         |
| ------------------ | ------------------------------------------------------------ |
| onreadystatechange | 存储函数（或函数名），每当`readyState`属性改变时，就会调用该函数。 |
| readyState         | 存有 XMLHttpRequest 的状态。从 0 到 4 发生变化。                                                                                            0: 请求未初始化  1: 服务器连接已建立 2: 请求已接收  3: 请求处理中 4: 请求已完成，且响应已就绪 |
| status             | 200: "OK" 404: 未找到页面                                    |

# ajax封装

```js
function myajax(obj) {
    // 设置默认值对象
    var defaults = {
        type: "get",
        url: "#",
        dataType: "json",
        data: {},
        async: true,
        success: function (result) {
            console.log(result);
        }
    };
    // 将obj中的属性覆盖到 defaults中的属性
    // 如果有一些属性只存在于obj中，那么会给defaults对象增加属性
    for (var key in obj) {
        defaults[key] = obj[key];
    }
    // 1 创建对象
    var xhr = null;
    if (window.XMLHttpRequest) {
        xhr = new XMLHttpRequest();
    } else {
        xhr = new ActiveXObject("Mircrosoft.XMLHTTP");
    }
    // 得到params
    var params = "";
    for (var attr in defaults.data) {
        params += attr + "=" + defaults.data[attr] + "&";
    }
    if (params) {
        params = params.substring(0, params.length - 1);
    }
    if (defaults.type == "get") {
        defaults.url += "?" + params;
    }
    // 2 连接服务器
    xhr.open(defaults.type, defaults.url, defaults.async);
    // 3 发送请求
    if (defaults.type == "get") {
        xhr.send(null);
    } else if (defaults.type == "post") {
        xhr.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
        xhr.send(params);
    }
    // 4 接受请求
    if (defaults.async) {
        xhr.onreadystatechange = function () {
            if (xhr.readyState == 4 && xhr.status) {
                var result = null;
                if (defaults.dataType == "json") {
                    result = responseText;
                    result = JSON.parse(result);
                } else if (defaults.dataType == "xml") {
                    result = responseXML;
                } else {
                    result = responseText;
                }
                defaults.success(result);
            }
        }
    } else {
        if (xhr.readyState == 4 && xhr.status) {
            var result = null;
            if (defaults.dataType == "json") {
                result = responseText;
                result = JSON.parse(result);
            } else if (defaults.dataType == "xml") {
                result = responseXML;
            } else {
                result = responseText;
            }
            defaults.success(result);
        }
    }
}
```

# 同源

协议、端口、域名三者都完全一样。

# 跨域的实现

访问非同源服务器下的数据，可以通过script标签引入外部文件。

```html
<head>
<script src="http://www.lisi.com/data.php?city=beijing"></script>
</head>
```