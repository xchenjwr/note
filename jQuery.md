# jQuery 教程
## jQuery语法

jQuery 语法是为 HTML 元素的选取编制的，可以对元素执行某些操作。

基础语法是：$(selector).action()
- 美元符号定义 jQuery
- 选择符（selector）“查询”和“查找” HTML 元素
- jQuery 的 action() 执行对元素的操作

### 文档就绪函数
```js
//第一种写法
$(document).ready(function() {
	
});
//第二种写法
$(function() {
	
});
```
## [jQuery 选择器](https://www.w3school.com.cn/jquery/jquery_ref_selectors.asp)
### jQuery 元素选择器

jQuery 使用 CSS 选择器来选取 HTML 元素。

- $("p") 选取 <p> 元素。

- $("p.intro") 选取所有 class="intro" 的 <p> 元素。

- $("p#demo") 选取所有 id="demo" 的 <p> 元素。

### jQuery 属性选择器

jQuery 使用 XPath 表达式来选择带有给定属性的元素。

- $("[href]") 选取所有带有 href 属性的元素。

- $("[href='#']") 选取所有带有 href 值等于 "#" 的元素。

- $("[href!='#']") 选取所有带有 href 值不等于 "#" 的元素。

- $("[href$='.jpg']") 选取所有 href 值以 ".jpg" 结尾的元素。

### jQuery CSS 选择器

```javascript
$("p").css("background-color","red");
```

### [jQuery事件](https://www.w3school.com.cn/jquery/jquery_ref_events.asp)

```javascript
$("button").click(function(){
    $("p").hide();
});
```

## [jQuery效果](https://www.w3school.com.cn/jquery/jquery_ref_effects.asp)

**隐藏、显示、切换，滑动，淡入淡出，以及动画，哇哦！**

### jQuery 显示和隐藏

- jQuery hide() 隐藏

- jQuery show() 显示

- jQuery toggle() 显示/隐藏

> $(selector).hide/show/toggle(speed,callback);
>
> 可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。
>
> 可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

### jQuery 淡入淡出

- jQuery fadeIn() 淡入已经隐藏的元素

- jQuery fadeOut() 淡出显示出的元素

- jQuery fadeToggle() 淡入/淡出

- jQuery fadeTo() 渐变为给定的不透明度（值介于 0 与 1 之间）。

> $(selector).fadeIn/fadeOut/fadeToggle/fadeTo(speed,callback);
>
> 可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>
> 可选的 callback 参数是 fading 完成后所执行的函数名称。

### jQuery 滑动

- jQuery slideDown()

- jQuery slideUp()

- jQuery slideToggle()

> $(selector).slideDown/slideUp/slideToggle(speed,callback);
>
> 可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>
> 可选的 callback 参数是滑动完成后所执行的函数名称。

### jQuery 动画

- jQuery animate()
  - 操作多个属性
  - 使用相对值
  - 使用预定义的值
  - 使用队列功能

> $(selector).animate({params},speed,callback);
>
> 必需的 params 参数定义形成动画的 CSS 属性。
>
> 可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>
> 可选的 callback 参数是动画完成后所执行的函数名称。

### jQuery stop() 方法

用于在动画或效果完成前对它们进行停止。

> $(selector).stop(stopAll,goToEnd);
>
> 可选的 stopAll 参数规定是否应该清除动画队列。默认是 false，即仅停止活动的动画，允许任何排入队列的动画向后执行。
>
> 可选的 goToEnd 参数规定是否立即完成当前动画。默认是 false。

### jQuery Callback

当动画 100% 完成后，即调用 Callback 函数。

### jQuery Chaining

直到现在，我们都是一次写一条 jQuery 语句（一条接着另一条）。

不过，有一种名为链接（chaining）的技术，允许我们在相同的元素上运行多条 jQuery 命令，一条接着另一条。

```javascript
$("#p1").css("color","red")
  .slideUp(2000)
  .slideDown(2000);
```

## jQuery HTML

### jQuery 获取和设置

- text() - 设置或返回所选元素的文本内容
- html() - 设置或返回所选元素的内容（包括 HTML 标记）
- val() - 设置或返回表单字段的值
- attr() 方法用于设置或返回属性值。可以设置回调函数。回调函数由两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。

```javascript
// 获取内容
alert($("text1").text());
alert($("text1").html());
alert($("text1").val());
alert($("text1").attr("herf"));
// 设置内容
$("text1").text("hello");
$("text1").html("<p>hello</p>");
$("text1").val("hello");
$("text1").attr(
    "herf":"http://www.w3school.com.cn/jquery",
    "title":"hello?"
);
// 设置回调函数
$("button").click(function(){
  $("#w3s").attr("href", function(i,origValue){
    return origValue + "/jquery";
  });
});
```

### jQeury 添加元素

- append() - 在被选元素的结尾插入内容
- prepend() - 在被选元素的开头插入内容
- after() - 在被选元素之后插入内容
- before() - 在被选元素之前插入内容

```js
function appendText(){
    var txt1="<p>Text.</p>";         
    var txt2=$("<p></p>").text("Text."); 
    var txt3=document.createElement("p"); 
    txt3.innerHTML="Text.";
    $("p").append(txt1,txt2,txt3);    
}
```

### jQuery 删除元素

- remove() - 删除被选元素（及其子元素）
- empty() - 从被选元素中删除子元素

- remove(”css“)过滤被删掉的元素

### jQuery css类

- addClass() - 向被选元素添加一个或多个类
- removeClass() - 从被选元素删除一个或多个类
- toggleClass() - 对被选元素进行添加/删除类的切换操作
- css() - 设置或返回样式属性 设置多个时需对象

### jQuery 尺寸 方法

- width() 方法设置或返回元素的宽度（不包括内边距、边框或外边距）
- height() 方法设置或返回元素的高度（不包括内边距、边框或外边距）
- innerWidth() 方法返回元素的宽度（包括内边距）
- innerHeight() 方法返回元素的高度（包括内边距）
- outerWidth() 方法返回元素的宽度（包括内边距和边框）
- outerHeight()  方法返回元素的高度（包括内边距和边框）

- outerWidth(true) 方法返回元素的宽度（包括内边距、边框和外边距）
- outerHeight(true) 方法返回元素的高度（包括内边距、边框和外边距）

### 参考手册

- [jQuery 文档操作](https://www.w3school.com.cn/jquery/jquery_ref_manipulation.asp)
- [jQuery 属性操作](https://www.w3school.com.cn/jquery/jquery_ref_attributes.asp)
- [jQuery CSS 操作](https://www.w3school.com.cn/jquery/jquery_ref_css.asp)

## [jQuery 遍历](https://www.w3school.com.cn/jquery/jquery_ref_traversing.asp)

### jQuery 祖先

- parent() 方法返回被选元素的直接父元素。
- parents() 方法返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (<html>)。
- parentsUntil() 方法返回介于两个给定元素之间的所有祖先元素。

### jQuery 后代

- children() 方法返回被选元素的所有直接子元素。
- find(空/标签) 方法返回被选元素的符合条件后代元素，一路向下直到最后一个后代。

### jQuery 同胞

- siblings() 返回被选元素的所有同胞元素。
- next() 返回被选元素的下一个同胞元素。
- nextAll() 返回被选元素的所有跟随(后面)的同胞元素。
- nextUntil() 返回介于两个给定参数之间的所有跟随的同胞元素。
- prev() 与上面相反
- prevAll()
- prevUntil()

### jQuery 过滤

- first() 方法返回被选元素的首个元素。
- last() 方法返回被选元素的最后一个元素。
- eq() 方法返回被选元素中带有指定索引号的元素。
- filter() 方法允许您规定一个标准。不匹配这个标准的元素会被从集合中删除，匹配的元素会被返回。
- not() 方法返回不匹配标准的所有元素。

## [jQuery AJAX](https://www.w3school.com.cn/jquery/jquery_ref_ajax.asp)

### jQuery 加载

load() 方法从服务器加载数据，并把返回的数据放入被选元素中。

```
$(selector).load(URL,data,callback);
function(responseTxt,statusTxt,xhr){}；
```

- 必需的 *URL* 参数规定您希望加载的 URL。

- 可选的 *data* 参数规定与请求一同发送的查询字符串键/值对集合。

- 可选的 *callback* 参数是 load() 方法完成后所执行的函数名称。
  - *responseTxt* - 包含调用成功时的结果内容
  - *statusTXT* - 包含调用的状态
  - *xhr* - 包含 XMLHttpRequest 对象

### jQuery Get/Post

>  $.get() 方法通过 HTTP GET 请求从服务器上请求数据。

```
$.get(URL,callback);
function(data,status){}
```

- 必需的 *URL* 参数规定您希望请求的 URL。

- 可选的 *callback* 参数是请求成功后所执行的函数名。

>  $.post() 方法通过 HTTP POST 请求从服务器上请求数据。

```
$.post(URL,data,callback);
function(data,status){}
```

- 必需的 *URL* 参数规定您希望请求的 URL。
- 可选的 *data* 参数规定连同请求发送的数据。
- 可选的 *callback* 参数是请求成功后所执行的函数名。