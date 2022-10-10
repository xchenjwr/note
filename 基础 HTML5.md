#  Html简介

## Web标准

- 结构    html5

- 表现    css3
- 行为    javascript

## Html5声明

```html
<!DOTYPE>
```

## lang引用

- 英文页面

  ```html
  <html lang="en">
  ```

- 中文页面

  ```html
  <html lang="zh-CN">
  ```

## 字符集

- UTF-8 全球通用编码

- 使用方式

  ``` html
  <meta charset="UTF-8">
  ```

# 标签

## 段落标签

> 上下段中间有一段间隙

``` html
<p>这是一个段落</p>    
```

## 换行标签

> 上下行中间没有间隙

```html
<br />
```

## 文本格式化标签

- 粗体 

  ```html
  <strong>加粗文字</strong>
  <b>加粗文字</b>
  ```

- 斜体 

  ```html
  <em>斜体文字</em>
  <i>斜体文字</i>
  ```

- 下划线 

  ```html
  <ins>下划线</ins>
  <u>下划线</u>
  ```

- 删除线

  ```html
  <del>删除线</del>
  <s>删除线</s>
  ```

## 盒子标签

- 分区标签

  > 一行只有一个div 大盒子

  ```html
  <div>这是div标签</div>
  ```

- 跨距标签

  > 一行可以有多个span 小盒子

  ```html
  <span>结构</span>
  <span>表现</span>
  <span>行为</span>
  ```

## 图像标签

| 属性     | 属性值  | 说明                 |
| ------ | ---- | :----------------- |
| src    | 图片路径 | 必须属性               |
| alt    | 文本   | 替换文本。图像不能显示时的文字    |
| title  | 文本   | 提示文本。鼠标放到图像上，显示的文字 |
| width  | 像素   | 设置图像的宽度            |
| height | 像素   | 设置图像的高度            |
| border | 像素   | 设置图像的边框粗细          |

```html
<img src="img.jpg" alt="" title="" width="" heigh="" border=""/>
```

**注意点**

- 高度和宽度一般只用设置一个，另一个会等比收放。

- 属性之间要用空格分开

## 路径

- **相对路径**

  > 以引用文件所在位置为参考位置，而建立出的目录路径

  | 相对路径分类 | 符号   | 说明                         |
  | ------ | ---- | -------------------------- |
  | 同一级路径  |      | `<img src="p1.gif" />`     |
  | 下一级路径  | /    | `<img src="img/p1.gif />"` |
  | 上一级目录  | ../  | `<img src="../p1.gif" />`  |

- **绝对路径**

  > 指目录下的绝对位置，直接到达目标位置，通常是从盘符开始的路径   

  - 电脑文件路径

    ```html
    <img src="D:\web\img\logo.gif" />"
    ```

  - 完整网络路径

    ```html
    <img src="http://www.baidu.com/img/logo.gif" />
    ```

- 注意

  - 绝对路径中电脑文件路径分隔符是**\\**
  - 相对路径和绝对路径中的完整网络路径分隔符是**/**

  - 每个人的电脑不一样，不建议使用绝对路径中的电脑文件路径

## 超链接标签

> 在HTML标签中，<a>标签用于定义超链接，作用是从一个页面链接到另一个页面

- 链接的语法格式

  ```html
  <a herf="跳转目标" target="目标窗口的弹出方式">文本或图像</a>
  ```

  | 属性     | 作用                                       |
  | ------ | ---------------------------------------- |
  | href   | 用于指定链接目标的url地址(必须属性)                     |
  | target | 用于指定连接页面的打开方式，其中\_self为默认值在当前页面打开，\_blank为在新窗口中打开方式。 |

- 链接的分类

  - 外部链接

    ```html
    <a href="http://www.baidu.com">百度</a>
    ```

  - 内部链接

    ```html
    <a href="index.html">主页</a>
    ```

  - 空链接

    ```html
    <a href="#">空链接</a>
    ```

  - 下载链接：地址内必须是一个文件或者压缩包

    ```html
    <a href="img.zip">下载</a>
    ```

  - 网页元素链接

    ```html
    <a href="http://www.baidu.com"><img src="img.gif" /></a>
    ```

  - 锚点链接：可以定位到页面的某个位置
    - 在链接文本的href属性中，设置属性值为 **#名字** 的形式，如`<a href="#two">第二集</a>`
    - 找到目标位置标签，里面添加一个id属性=刚才的名字，如`<h3 id="two">第二集介绍</h3>`

- 实际开发中，我们不会直接用链接a而是用li包含链接（li+a）的做法

- 阻止链接跳转`javascript:void(0);`或者`javascript:;`

## 注释标签

加注释和取消huo快捷键：ctrl + /

```html
<!--注释语句-->
```

## 特殊字符

| 特殊字符     | 描述      | 字符的代码        |
| -------- | ------- | ------------ |
|          | **空格符** | **`&nbsp;`** |
| **<**    | **小于号** | **`&lt;`**   |
| **>**    | **大于号** | **`&gt;`**   |
| &        | 和号      | `&amp`;      |
| ￥        | 人民币     | `&yen;`      |
| &copy;   | 版权      | `&copy;`     |
| &reg;    | 注册商标    | `&reg`;      |
| &deg;    | 摄氏度     | `&deg`;      |
| &plusmn; | 正负号     | `&plusmn;`   |
| &times;  | 乘号      | `&times;`    |
| &divide; | 除号      | `&divide;`   |
| &sup2;   | 平方2     | `&sup2`      |
| &sup3;   | 立方3     | `&sup3`      |

## 表格标签

- **表格的主要作用**

  > 显示、展示数据

- **表格的基本语法**

  ```html
  <table>
      <tr>
          <td>单元格内文字</td>
          ···
      </tr>
      ···
  </table>
  ```

  - `<table></table>`是用于定义表格的标签。
  - `<tr></tr>`用于定义表格中的行，必须嵌套在`<table></table>`标签中。
  - `<td></td>`用于定义表格中的单元格，必须嵌套在`<tr><tr>`中。

### 表头单元格标签

> 一般表头单元格位于表格的第一行或第一列，表头单元格里面的文本内容加粗居中显示

```html
<table>
    <tr>
        <th>姓名</th>
        ···
    </tr>
    ···
</table>
```

### 表格结构标签

- `<thead>`标签，表格的头部区域

- `<tbody>`标签，表格的主体区域

  ```html
  <table>
      <thead>
          <tr>
              <th></th>
              ···
          </tr>
          ···
      </thead>
      <tbody>
          <tr>
              <td></td>
              ···
          </tr>
          ···
      </tbody>
  </table>
  ```

> 以上两个标签都是放到table里面的

### 表格属性

> 这些属性要写到表格标签table中去

| 属性名         | 属性值               | 描述                        |
| ----------- | ----------------- | ------------------------- |
| align       | left、center、right | 规定表格相对周围元素的对齐方式           |
| border      | 1或者“”             | 规定表格单元是否拥有边框，默认为“”，表示没有边框 |
| cellpadding | 像素值               | 规定单元格边沿与内容之间的空白，默认1像素     |
| cellspacing | 像素值               | 规定单元格之间的空白，默认2像素          |
| width       | 像素值或百分比           | 规定表格的宽度                   |
| height      | 像素值或百分比           | 规定表格的高度                   |

### 合并单元格

- **合并单元格方式**
  - 跨行合并：rowspan="合并单元格个数"
  - 跨列合并：colspan="合并单元格个数"

- **目标单元格**
  - 跨行：最上测单元格为目标单元格，写合并代码
  - 跨列：最左侧单元格为目标单元格，写合并代码

- **合并单元格步骤**
  - 先确定跨行还是跨列合并
  - 找到目标单元格。写上合并方式=合并的单元格数量。比如：`<td colspan="2" ></td>`
  - 删除多余的单元格

## 列表标签

> 列表就是用来**布局**的
>
> 列表的最大的特点就是**整齐、整洁、有序**，它作为布局惠更加自由和方便
>
> 根据使用情景不同，列表可以分为三大类：**无序列表、有序列表和自定义列表**

### 无序列表

> `<ul>`标签标识HTML页面中的无序列表，一般会以项目符号呈现列表项，而列表项使用`<li>`标签定义。

```html
<ul>
    <li>列表项1</li>
    <li>列表项2</li>
    <li>列表项3</li>
    ···
</ul>
```

- 注意
  - 无序列表的各个列表项之间没有顺序级别之分，是并列的
  - `<ul></<ul>`只能嵌套`<li></li>`，直接在`<ul></ul>`标签中输入其他标签或者文字的做法是不被允许的
  - `<li></li>`之间相当于一个容器，可以容纳所有元素
  - 无序列表会带有自己的样式，但在实际使用时，我们会使用CSS来设置

###  有序列表

> `<ol>`标签用于定义有序列表，列表排序以数字来显示，并且使用`<li>`标签来定义列表项

```html
<ol>
    <li>列表项1</li>
    <li>列表项2</li>
    <li>列表项3</li>
    ···
</ol>
```

- 注意点跟无序列表类似

### 自定义列表

> 用于对术语或者名词进行解释和描述，定义列表的列表项前没有任何项目符号

```html
<dl>
    <dt>名词</dt>
    <dd>名词解释1</dd>
    <dd>名词解释2</dd>
    ··· 
</dl>
```

- 注意
  - `<dl></dl>里面只能包含<dt>和<dd>`
  - `<dt>`和`<dd>`个数没有限制，经常时一个`<dt>`对应多个`<dd>`

- 不要li前面的样式用`list-style: none;`

## 表单标签

> 用来**收集用户信息**的

> 表单组成通常由表单域、表单控件（表单元素）和提示信息组成

### 表单域

> 表单域是一个包含表单元素的区域。
>
> 在标签中，`<form>`标签用于定义表单域，以实现用户信息的收集和传递
>
> `<form>`会把它范围内的表单元素信息提交给服务器。

```html
<form action="url地址" method="提交方式" name="表单域名称">
    各种表单元素
</form>
```

| 属性     | 属性值      | 作用                           |
| ------ | -------- | ---------------------------- |
| action | url地址    | 用于指定接受并处理表单数据的服务器程序的url地址    |
| method | get/post | 用于设置表单元素数据的提交方式，其取值为get/post |
| name   | 名称       | 用于指定表单的名称，以区分同一个页面中的多个表单域    |

- 注意点
  - 在我们写表单元素之前，应该有个表单域把他们进行包含
  - 表单域时form标签

### input 输入表单标签

> `<input>`标签用于收集用户信息。
>
> 在`<input>`标签中，包含一个type属性，根据不同的type属性值，输入字段拥有很多种形式（可以是文本字段、复选框、掩码后的文本控件、单选按钮、按钮等）

```html
<input type="属性值" />
```

- type属性的属性值及其描述如下：

| 属性值      | 描述                             |
| -------- | ------------------------------ |
| button   | 定义可点击按钮                        |
| checkbox | 定义复选框                          |
| file     | 定义输入字段和“浏览”按钮，供文件上传            |
| hidden   | 定义隐藏的输入字段                      |
| image    | 定义图像形式的提交按钮                    |
| password | 定义密码字段，该字段中的字符被掩码              |
| radio    | 定义单选按钮                         |
| reset    | 定义重置按钮，重置按钮会清楚表单中的所有数据         |
| submit   | 定义提交按钮。提交按钮会把表单数据发送到服务器        |
| text     | 定义单行的输入字段，用户可在其中输入文本。默认宽度为20字符 |

- 除了type属性还有其他常用属性：

| 属性        | 属性值     | 描述                   |
| --------- | ------- | -------------------- |
| name      | 由用户自定义  | 定义input元素的名称         |
| value     | 由用户自定义  | 规定input元素的值          |
| checked   | checked | 规定此input元素首次加载时应当被选中 |
| maxlength | 正整数     | 规定输入字段中的字符的最大长度      |

```html
<form action="xxx.php" method="get">
    用户名:<input type="text" name="username" placeholder="请输入用户名"> <br>
    密码:<input type="password" name="pwd"> <br>
    性别:<label for="nan">男</label><input type="radio" name="sex" value="男" id="nan">
    <label for="nv">女</label><input type="radio" name="sex" value="女" id="nv"> <br>
    爱好:游戏<input type="checkbox" name="hobby" value="游戏"> 小说<input type="checkbox" name="hobby" value="小说"> <br>
    居住地:<select>
    	<option>湖北</option>
    	<option selected="selected">杭州</option>
    	<option>西安</option>
    </select>
    上传头像:<input type="file"> <br>
    验证码:<input type="text" maxlength="6"> <input type="button" value="获取短信验证码"> <br>
    <input type="checkbox" name="hobby" checked="checked">同意xx协议 <br>
    <input type="submit" value="免费注册">
    <input type="reset" value="重新填写">
</form>
```

- 注意点
  - name和value是每个表单元素都有的属性值，主要给后台人员使用
  - 单选框和复选框都要有相同的name值

### label 标签

> `<label>`为input元素标注。
>
> 用于绑定一个表单元素。但点击label标签内文本时，浏览器就会自动将焦点转到或者选择对应的表单元素上，用来增加用户体验。

```html
<label for="sex">男</label>
<input type="radio" name="sex" id="sex" />
```

- label的for要跟标签的id属性相同才可以定位

### select 下拉表单标签

> 在页面中，如果有多个选项让用户选择，并且想要节约页面空间时，我们可以使用`<select>`标签控件定义**下拉列表**

```html
<select>
    <option>湖北</option>
    <option>湖南</option>
    <option>杭州</option>
</select>
```

- 注意点
  - `<select>`中至少包含一对`<option>`
  - 在`<option>`中定义selected="selected"时，当前项即为默认选中项

### textarea 文本域标签

> 当用户输入内容较多的情况下，我们就不能使用文本框表单了，此时我们可以使用`<textarea>`标签
>
> 在表单元素中，`<textarea>`是用于定义多行文本输入的控件。例如评论

```html
评论:
<!--cols:每行中字符数，row:显示的行数-->
<textarea cols="20" rows="3">
    
</textarea>
```

- 不要使用cols、rows，尽量使用css

# 查阅文档

[百度](www.baidu.com)

[w3chool文档](https://www.w3school.com.cn/w3chool)

[MDN web文档](https://developer.mozilla.org/zh-CN/)

# HTML5新增

## 语义化标签

- `<header>`：头部标签
- `<nav>`：导航标签
- `<article`：内容标签
- `<section>`：定义文档某个区域
- `<aside>`：侧边栏标签
- `<footer>`：尾部标签
- 注意
  - 这种语义化标准主要是针对**搜索引擎**的
  - 这些新标签页面中可以使用**多次**
  - 在IE9中，需要把这些元素转换成**块级元素**
  - 其实，我们移动端更喜欢使用这些标签

## 多媒体标签

### 视频 video

> 当前video元素支持三种视频格式：尽量使用mp4格式

| 浏览器     | MP4  | WebM | Ogg  |
| ------- | ---- | ---- | ---- |
| IE      | yes  | no   | no   |
| Chrome  | yes  | yes  | yes  |
| Firefox | yes  | yes  | yes  |
| Safari  | yes  | no   | no   |
| Opera   | yes  | yes  | yes  |

```html
<video src="文件地址" controls="controls"></video>
/*解决兼容性*/
<video controls="controls" width="300">
    <source src="move.ogg" type="video/ogg">
    <source src="move.mp4" type="video/mp4">
    您的浏览器不支持video标签播放视频
</video>
```

| 属性       | 值                       | 描述                                |
| -------- | ----------------------- | --------------------------------- |
| autoplay | autoplay                | 视频就绪自动播放（谷歌播放器需要添加muted来解决自动播放问题） |
| controls | controls                | 向用户显示播放控件                         |
| width    | px                      | 设置播放器宽度                           |
| height   | px                      | 设置播放器高度                           |
| loop     | loop                    | 播放完是否继续播放该视频，循环播放                 |
| preload  | auto(预先加载视频)none(不加载视频) | 规定是否加载视频（如果有了autoplay就忽略该属性）      |
| src      | url                     | 视频url地址                           |
| poster   | imgurl                  | 加载等待的画面图片                         |
| muted    | muted                   | 静音播放                              |

### 音频 audio

| 浏览器     | MP3  | Wav  | Ogg  |
| ------- | ---- | ---- | ---- |
| IE      | yes  | no   | no   |
| Chrome  | yes  | yes  | yes  |
| Firefox | yes  | yes  | yes  |
| Safari  | yes  | yes  | no   |
| Opera   | yes  | yes  | yes  |

```html
<audio src="文件地址" controls="controls"></audio>
/*解决兼容性*/
<audio controls="controls">
    <source src="happy.mp3" type="audio/mpeg">
    <source src="happy.ogg" type="audio/ogg">
   	您的浏览器暂不支持audio标签
</audio>
```

| 属性       | 值        | 描述         |
| -------- | -------- | ---------- |
| autoplay | autoplay | 音频就绪后马上播放  |
| controls | controls | 显示控件       |
| loop     | loop     | 结束后重新播放    |
| src      | url      | 要播放的音频的URL |

- 音频标签和视频标签使用方式基本一致
- 浏览器支持情况不同
- 谷歌浏览器把音频和视频自动播放禁止了
- 我们可以给视频标签添加muted属性来静音播放视频，音频不可以（可以js解决）
- 视频标签是重点，我们经常设置自动播放，不使用controls控件，循环和设置大小属性

## input表单

| 属性值               | 说明               |
| ----------------- | ---------------- |
| type="email"      | 限制用户输入必须为Email类型 |
| type="url"        | 限制用户输入必须为URL类型   |
| type="data"       | 限制用户输入必须为日期类型    |
| type="time"       | 限制用户输入必须为时间类型    |
| type="month"      | 限制用户输入必须为月类型     |
| type="week"       | 限制用户输入必须为周类型     |
| **type="number"** | 限制用户输入必须为数字类型    |
| **type="tel"**    | 手机号码             |
| **type="search"** | 搜索框              |
| type="color"      | 生成一个颜色选择表单       |

## input表单属性

| 属性           | 值         | 说明                                       |
| ------------ | --------- | ---------------------------------------- |
| required     | required  | 表单用于属性不能为空，必填                            |
| placeholder  | 提示文本      | 表单的提示信息，存在默认值将不显示                        |
| autofocus    | autofocus | 自动聚焦实行。页面加载完成自动聚焦到指定表单                   |
| autocomplete | off/on    | 当用户在字段开始键入时，浏览器基于之前键入过的值，应该显示在字段中填写的选项。默认已经打开，需要放在表单内，同时加上name属性，同时成功提交。 |
| multiple     | multiple  | 可以多选文件提交                                 |

## 拖放

抓取对象以后拖到另一个位置。

```
1 设置元素为可拖放
	draggable = "true";
2 拖动什么
	ondragstart 和 setData()
3 放到何处
	ondragover
4 进行放置
	ondrop
```

```html
<style>
#div1 {
    width: 300px;
    height: 300px;
    border: 1px solid #aaabbb;
}
</style>
<script>
    function allowDrop(ev) {
        ev.preventDefault();
    }
    function drag(ev) {
        ev.dataTransfer.setData("Text", ev.target.id);
    }
    function drop(ev) {
        ev.preventDefault();
        var data = ev.dataTransfer.getData("Text");
      ev.target.appendChild(document.getElementById(data));
    }
</script>
<div id="div1" ondrop="drop(event)" ondragover="allowDrop(event)"></div>
<img id="drag1" src="1.jpg" draggable="true" ondragstart="drag(event)">
```

## 画布

画布是一个矩形区域，可以控制其每一像素。canvas拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。

```html
<script>
    var c = document.getElementById("canvas");
    var cxt = c.getContext("2d");
    cxt.fillStyle = "#ff0000";
    cxt.fillRect(0,0,100,100);
</script>
<canvas id="canvas" width="400px" height="400px"></canvas>
```

## SVG

SVG指可伸缩矢量图形。

```html
<?xml version="1.0"?>
<svg viewBox="0 0 120 120" version="1.1"
  xmlns="http://www.w3.org/2000/svg">
  <circle cx="60" cy="60" r="50"/>
</svg>
```

- 一般外部文件用iframe来引入。

## 地理位置

HTML5 API 用于获得用户的地理位置。

## Web存储

- 没有时间限制的数据存储
- 针对一个session的数据存储