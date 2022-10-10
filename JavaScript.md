# JS的组成

ECMAScript（JavaScript语法）、DOM(页面文档对象模型)、BOM(浏览器对象模型)

# 输入输出语句

| alert(msg)         | 警示框     |
| ------------------ | ---------- |
| prompt(info)       | 输入框     |
| console.log（msg） | 控制台输出 |

 # 变量

变量是程序在内存中申请的一块用来存放数据的空间。

```javascript
//声明变量
var age;//声明一个名称为age的变量
//赋值
age = 18;
//输出变量
console.log(age);
//初始化
var age = 18;
//声明多个变量
var age = 18,myname = '张三';
//不声明直接使用是可以的
age = 18;
```

- 由字母，数字，下划线，美元符号组成。
- 严格区分大小写。
- 不能以数字开头
- 不能是关键字，保留字
- 变量名必须有意义
- 遵循驼峰命名法。首字母小写，后面单词的首字母需要大写 

## 数据类型

数据类型取决于赋值的取值类型，随取值的变化而变化。

**简单数据类型**

| 简单数据类型 | 说明                                           |
| ------------ | ---------------------------------------------- |
| Number       | 数字型，包含整形值和浮点型值。                 |
| Boolean      | 布尔值类型，如true,false,等价于1和0.           |
| String       | 字符串类型，如‘张三’。                         |
| Undefined    | var a;声明了变量a但没有给值，此时a = undefined |
| Null         | var a = null;声明了变量a为空值。               |

## 数字型 Number

```javascript
alert(Infinity);  //无穷大
alert(-Infinity);  // 无穷小
alert(NaN);       //代表一个非数值
var flag = isNaN(12);  //判断一个变量是否为非数字的类型
```

## 字符串型 String

字符串型可以是引号中的任意文本，其语法为双引号“ ”和单引号‘ ’。

```js
var str1 = "hellojs!";
var str2 = 'hellojs!';   //更推荐使用单引号
var str3 = 'hello"js"!';
var str4 = "hello'js'!";
```

### 字符串转义符

| 转义符 | 解释                     |
| ------ | ------------------------ |
| \n     | 换行符，n是newline的意思 |
| `\\`   | 斜杠\                    |
| `\'`   | '单引号                  |
| `\"`   | “双引号                  |
| `\t`   | tab缩进                  |
| `\b`   | 空格，b是blank的意思     |

### 字符串长度

字符串是由若干字符组成的，这些字符的数量就是字符串的长度。通过字符串的length属性可以获取整个字符串的长度。

```js
var str = "my name is andy";
console.log(str.length);	//15
```

### 字符串拼接

- 多个字符串之间可以使用+进行拼接，其拼接方法为字符串+任何类型=拼接之后的新字符串
- 拼接前会把字符串相加的任何类型转成字符串，再拼接成一个新的字符串

```js
alert('hello'+' '+'world'); //hello world
alert('100'+'100') //100100
alert('11'+12) //1112
```

## 布尔型 Boolean

布尔类型有两个值：true和false,其中true表示真，而false表示假。

布尔型和数字型相加的时候，true表示1，false表示0。

```js
console.log(true+1); //2
console.log(false+1); //1
```

## Undefined和Null

一个声明后没有被赋值的变量会有一个默认值undefined

```js
var str;
console.log(str); //undefined
console.log('你好'+str); //你好undefined
console.log(11+str); //NaN
console.log(true+str); //NaN
```

一个声明变量给null值，里面存的值为空。

```js
var str = null;
console.log(str); //null
console.log('你好'+str); //你好null
console.log(11+str); //11
console.log(true+str); //1
```

## 获取检测变量的数据类型

typeof可用来获取检测变量的数据类型。

```js
var num = 18;
console.log(typeof num); //number
var num = '18';
console.log(typeof num); //string
var num = true;
console.log(typeof num); //boolean
var num = undefined;
console.log(typeof num); //undefined
var num = null;
console.log(typeof num); //object
```

## 字面量

字面量是在源代码中的一个固定值的表示法，通俗来说，就是字面量表示如何表达这个值。

- 数字字面量：8，9，10
- 字符串字面量：’hello‘,'bangbangboom'
- 布尔字面量：true,flag

## 数据类型转换

### 转换为字符串

| 方式               | 说明                             |
| ------------------ | -------------------------------- |
| toString()         | 转成字符串                       |
| String()           | 转成字符串                       |
| **加号拼接字符串** | **和字符串拼接的结果都是字符串** |

- 更推荐第三种转换方式。

``` js
var num = 10;
var str1 = num.toString();
var str2 = String(num);
var str3 = num + ' ';
```

### 转换成数字型（重点）

| 方式                   | 说明                                 |
| ---------------------- | ------------------------------------ |
| **parseInt（string）** | **将string类型转换成整数数值类型**   |
| **parseFloat(string)** | **将string类型转换成浮点数数值类型** |
| Number()               | 将string类型转换成数值类型           |
| js隐式转换（- * /）    | 利用算数运算隐式转换成数值型         |

```js
console.log(parseInt('3.14')); //3
console.log(parseInt('3.94')); //3
console.log(parseInt('120px')); //120
console.log(parseInt('rem120px')); //NaN
console.log(parseFloat('3.14')); //3.14
console.log(parseFloat('120px')); //120
console.log(parseFloat('rem120px')); //NaN
```

### 转换成布尔型

| 方式      | 说明                 |
| --------- | -------------------- |
| Boolean() | 其他类型转换成布尔型 |

- 表示空、否定的值会被转换成false，如”0，NaN、null、undefined“.
- 其余的值都会被转换成true。

```js
console.log(Boolean('')); //false
console.log(Boolean(0)); //false
console.log(Boolean(NaN)); //false
console.log(Boolean(null)); //false
console.log(Boolean(undefined)); //false
console.log(Boolean('小黑')); //true
console.log(Boolean(12)); //true
```

# 运算符

## 算数运算符

| 运算符 | 描述   |
| ------ | ------ |
| +      | 加     |
| -      | 减     |
| *      | 乘     |
| /      | 除     |
| %      | 取余数 |

**浮点数的精度问题**

转成二进制再进行相加减会产生误差

```js
var result = 0.1 + 0.2; //0.30000000000000004
console.log(0.07*100); //7.00000000000000001
```

所以**不能直接判断两个浮点数是否相等。**

**表达式和返回值**

表达式：是由数字、运算符、变量等组成的式子

表达式最终会有一个结果，返回给我们，我们称为返回值。

## 递增递减运算符

递增(++)、递减(--)

**前置递增递减（++y/--y）**

先自加减后返回原值。

**后置递增递减(y++/y--)**

先返回原值后自加减。

## 比较运算符

比较运算符是连个数据进行比较时所使用的运算符，比较运算后，会返回一个布尔值作为比较运算的结果

有\>大于 、<小于 、>=大于等于、<=小于等于、==判等号、！=不等号和===全等等。

| 符号 | 作用 | 用法                                         |
| ---- | ---- | -------------------------------------------- |
| =    | 赋值 | 把右边给左边                                 |
| ==   | 判断 | 判断两边值是否相等（注意此时有**隐式转换**） |
| ===  | 全等 | 判断**两边的值和数据类型**是否完全相同       |

## 逻辑运算符

逻辑运算符是用来进行布尔值运算的运算符，其返回值也是布尔值。后面开发中经常用于多个条件的判断。

有&&逻辑与、||逻辑或、！逻辑非等。

**逻辑中断逻辑与**

- 表达式1 && 表达式2
- 如果表达时1为真，返回表达式2
- 如果表达时1为假，返回表达式1

**逻辑中断逻辑或**

- 表达式1 || 表达式2
- 如果表达时1为真，返回表达式1
- 如果表达时1为假，返回表达式2

```js
console.log(123 && 456); //456
console.log(0 && 123); //0
console.log(123 || 456); //123
console.log(0 || 123); //123
```

## 运算符优先级

| 优先级 | 运算符     | 顺序            |
| ------ | ---------- | --------------- |
| 1      | 小括号     | （）            |
| 2      | 一元运算符 | ++ -- ！        |
| 3      | 算术运算符 | 先 * / % 后 + - |
| 4      | 关系运算符 | > >= < <=       |
| 5      | 相等运算符 | == != === !==   |
| 6      | 逻辑运算符 | 先&& 后\|\|     |
| 7      | 赋值运算符 | =               |
| 8      | 逗号运算符 | ，              |



# 流程控制

控制我们的代码按照什么结构顺序来执行。三种结构：顺序结构、分支结构和循环结构。

## 顺序结构

## 分支结构

### if-else 语句

```js
if(num > 80) {
    alert("优秀");
}else if(num > 60) {
    alert("及格");
}else {
    alert("重修");
}
```

**三元表达式**

```js
var str = num > 60 ? '通过' : '挂科';
```

### Switch 语句

```js
switch(str){
    case '橘子':
        alert('2.5y/kg');
        break;
    case '苹果':
        alert('4.5y/kg');
        break;
    default:
        alert('不卖这种水果');
}
```

### if-else语句和switch语句的区别

- 一般情况下可以替换
- switch处理case值为确认的情况，if-else处理范围值
- switch直接判断，if-else语句要逐次判断
- 分支多的时候switch效率高，分支少的时候if-else效率高

## 循环结构

### for循环

```js
for (var i = 1; i <= 100;i++) {
    alert(i);
}
```

- 断点调试再srouce里面

### while循环

```js
while (num > 10) {
    alert(num--);
}
```

### do...while循环

 ```js
do {
    alert(num--);
}while (num > 10)
 ```

### continue break

continue : 跳出本次循环，继续下一次循环。

break：跳出整个循环。

### 标识符命名规范

- 变量、函数的命名必须要有意义
- 变量的名称一般用名词
- 函数的名称一般用动词
- 操作符的左右两侧各保留一个空格
- 单行注释前面有个空格
- 括号两头留空格

# 数组

一组数据的集合。

## 利用new创建数组

```js
var arr = new Array();
```

## 利用数组字面量创建数组

```js
var arr = [];
var arr = ['小白',1,true,10.1];
```

- 数组里面可以放任意类型的数据。

## 数组的索引

数组名[索引]

```js
console.log(arr[0]);
```

## 数组的长度

数组名.length

```js
var arr = [1,2,3];
alert(arr.length); //3
```

## 新增数组元素

**通过修改length**

```js
var arr = [1,2,3];
arr.length = 5;
console.log(arr[3]);
console.log(arr[4]);
```

**通过修改数组索引**

```js
var arr = [1,2,3];
arr[3] = 4;
arr[4] = 5;
```

# 函数

## 声明函数

```js
function 函数() {
	//    
}
```

## 调用函数

```js
函数名();
```

## 函数的参数

形参：形式上的参数（函数定义）

实参：实际上的参数（函数调用）

- 形参的默认值为undefined。

## 函数的返回值

**return语句**

```js
function 函数名() {
    return num1,num2;
}
var x = 函数名(); // x = num2;
```

- return只能返回一个值，若返回多个，则只能返回最后一个。

- 若没有return，则返回undefined;

## arguments的使用

当我们不确定有多少个参数传递的时候，可以用arguments来获取。在js中，arguments实际上它是当前函数的一个内置对象。所有函数都内置了一个arguments对象，arguments对象中储存了传递的所以实参。

arguments展示形式是一个伪数组，因此可以进行遍历。伪数组具有以下特点：

- 具有length属性
- 按索引方式存储数据
- 不具有数组的push,pop等方法

```js
function maxvalue() {
    var max = arguments[0];
    for (var i = 0; i < arguments.length;i++) {
        if (max < arguments[i]) {
            max = arguments[i];
        }
    }
    return max;
};
console.log(maxvalue(2,4,12,8));
```

## 函数的两种声明方式

**自定义函数方式(命名函数)**

利用函数关键字function自定义函数方式。

```js
function fn() {...};
fn();
```

- 因为有名字，称为命名函数
- 调用函数的代码可以放在声明函数的前面，也可以放在声明函数的后面

**函数表达式方式（匿名函数）**

```js
var fn = function() {...};
fn();                  
```

- 调用代码必须写到函数体的后面。

## 函数作用域

可用性的代码范围

es6前js的作用域有两种：

- 全局作用域
- 局部作用域（函数作用域）

### 块作用域

由{}包括。

- js没有块作用域（es6前）

### 变量作用域

- 全局变量
- 局部变量

### 作用域链

- 如果函数中还有函数，那么在这个作用域中就又可以诞生一个作用域。

- 采取就近原则

# js预解析

在js代码执行之前，浏览器会默认把带有var和function声明的变量在内存中进行提前声明或者定义。

## 变量预解析

变量提升：变量的声明会被提升到**当前作用域**的最上面，变量的赋值不会提升。

```js
console.log(num);
var num = 10;
// 相当于
var num;
console.log(num);
num = 10;
```

## 函数与解析

函数提升：函数的声明会被提升到**当前作用域**的最上面，但是不会调用函数。

```js
fn();
function fn() {
    console.log("打印");
}
//相当于
function fn() {
    console.log("打印");
}
fn();
```

# 对象

对象是由属性和方法组成的。

## 利用字面量创建对象

对象字面量：就是花括号{}里面包含了表达这个具体事物的属性和方法。

{}里面采用键值对的形式表示。

```js
var star {
    name: 'pink';
    age: 18;
    sex: '男';
    sayhi: function() {
        alert('hi');
    }
}
```

## 利用new Object创建对象

```js
var andy = new Object();
andy.name = 'pink';
andy.age = 18;
andy.sex = '男';
andy.sayhi = function() {
    alert('hi');
}
```

## 利用构造函数创建对象

```js
function Person(name,age,sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
    this.sayhi = function() {
        alert('hi');
    }
}
var bigbai = new Person('大白',100,'男');
console.log(bigbai.name);
```

- 构造函数约定首字母大写。
- 函数内的属性和方法前面需要添加this,表示当前的属性和方法。
- 构造函数中不需要return返回结果。

## 对象的调用

- 对象里面的属性用：对象.属性名
- 对象里面的属性调用：对象[‘属性名’]，注意方括号里面的属性必须加引号。
- 对象里面的方法调用：对象.方法()，注意这个方法名字一定要加括号。

```js
console.log(star.name);
console.log(star['name']);
star.sayHi();
```

## 遍历对象属性

for..in语句用于对**数组或者对象**的属性进行循环操作。

```js
for (var k in obj) {
    console.log(k); // 属性名
    console.log(obj[k]); // obj[k]是属性值
}
```

# 内置对象

对象分为三种：自定义对象、内置对象、浏览器对象。

- 前面两种对象是js基础内容，属于ECMAScript；第三个浏览器对象属于我们js独有的。
- 内置对象就是指js语言自带的一些对象，这些对象供开发者使用，并提供了一些常用的或是最基本而必要的功能。
- 内置对象对打的优点就是帮助我们快速开发。
- js提供了多个内置对象：Math、Date、Array、String等。

## Math对象

Math对象不是构造函数，它具有数学常数和函数的属性和方法。跟数学相关的运算（求绝对值，取整，最大值等）

```js
Math.PI // 圆周率
Math.floor(); // 向下取整
Math.ceil(); // 向上取整
Math.round(); // 四舍五入取整 就近取整 -3.5结果是 -3   .5 特殊 它往大了取 
Math.abs(); // 绝对值
Math.max();Math.min()  // 求最大和最小值
```

### 随机数random()

random()可以随机返回一个小数，其取值范围是[0,1)

```js
function getRandom(min,max) {
    return Math.floor(Math.random()*(max-min+1)) + min;
}
```

## Date 对象

- Date对象和Math对象不一样，他是一个构造函数，所以我们需要实例化后才能使用。
- Date实例用来处理日期和时间。

### 获取当前时间必须实例化

```js
var now = new Date();
console.log(now);
```

### Date()构造函数的参数

如果括号里面有时间，就返回参数里面的时间。例如日期格式字符串为‘2019-5-1’，可以写成new Date('2019-5-1')或者new Date('2019/5/1')

- 如果Date()不写参数，就返回当前时间
- 如果Date()里面写参数，就返回括号里面输入的时间

### 日期格式化

| 方法名        | 说明                     | 代码              |
| ------------- | ------------------------ | ----------------- |
| getFullYear() | 获取当年                 | obj.getFullYear() |
| getMonth()    | 获取当月0-11             | obj.getMonth()    |
| getDate()     | 获取当天日期             | obj.getDate()     |
| getDay()      | 获取星期几(周日0到周六6) | obj.getDay()      |
| getHours()    | 获取当前小时             | obj.getHours()    |
| getMinutes()  | 获取当前分钟             | obj.getMinutes()  |
| getSeconds()  | 获取当前秒钟             | obj.getSeconds()  |

### 获取日期的总的毫秒形式

```js
var now = new Date();
// 1 用于获取对象的原始值
console.log(data.valueOf());
console.log(data.getTime());
// 2 简单写可以这么做
var now = + new Date();
// 3 HTML5提供的方法有兼容性问题
var now = Date.now();
```

## 数组对象

### 检测是否为数组

- instanceof运算符，可以判断一个对象是否属于某种类型
- Array.isArray()用于判断一个对象是否为数组，isArray()是HTML5中提供的方法

```js
var arr = [1,23];
var obj = {};
console.log(arr instanceof Array); // true
console.log(obj instanceof Array); // false
console.log(Array.isArray(arr)); // true
console.log(Array.isArray(obj)); // false
```

### 添加删除数组元素的方法

| 方法名    | 说明                                                       | 返回值               |
| --------- | ---------------------------------------------------------- | -------------------- |
| push()    | 末尾添加一个或多个元素，注意修改原数组                     | 并返回新的长度       |
| pop()     | 删除数组的最后一个元素，并把数组长度减1 无参数、修改原数组 | 返回它删除的元素的值 |
| unshift() | 向数组的开头添加一个或更多元素，注意修改原数组             | 并返回新的长度       |
| shift()   | 删除数组的第一个元素，数组长度减1 无参数、修改原数组       | 并返回第一个元素的值 |

 ###  数组排序

| 方法名    | 说明                         | 是否修改原数组         |
| --------- | ---------------------------- | ---------------------- |
| reverse() | 颠倒数组中元素的顺序，无参数 | 改变原数组，返回新数组 |
| sort()    | 对数组的元素进行排序         | 改变原数组，返回新数组 |

### 数组索引方法

| 方法名        | 说明                           | 返回值                     |
| ------------- | ------------------------------ | -------------------------- |
| indexOf()     | 数组中查找给定元素的第一个索引 | 存在返回索引号，否则返回-1 |
| lastIndexOf() | 在数组中的最后一个的索引       | 存在返回索引号，否则返回-1 |

### 数组转换成字符串

| 方法名         | 说明                                       | 返回值         |
| -------------- | ------------------------------------------ | -------------- |
| toString()     | 把数组转换成字符串，逗号分隔每一项         | 返回一个字符串 |
| join('分隔符') | 方法用于把数组中的所有元素转换为一个字符串 | 返回一个字符串 |

### 数组操作方法

| 方法名       | 说明                                   | 返回值                              |
| ------------ | -------------------------------------- | ----------------------------------- |
| concat()     | 连接两个或多个数组 不影响原数组        | 返回一个新的数组                    |
| slice()      | 数组截取slice(begin,end)               | 返回被截取项目的新数组              |
| **splice()** | 数组删除splice(第几个开始，要删除个数) | 返回被删除项目的新数组 会影响原数组 |

slice(),splice()目的基本相同，建议splice()

## 字符串对象

### 基本包装类型

**基本包装类型**就是把简单数据类型包装成为复杂数据类型，这样基本数据类型就有了属性和方法。

```js
var str = 'andy';
console.log(str.length);
```

按道理基本数据类型是没有属性和方法的，而对象才有属性和方法，但上面代码却可以执行，这是因为js会把基本数据类型包装为复杂数据类型，其执行过程如下：

```js
// 1 生成临时变量，把简单类型包装为复杂数据类型
var temp = new String('andy');
// 2 赋值给我们声明的字符变量
str = temp;
// 3 销毁临时变量
temp = null;
```

### 字符串的不可变

值得是里面的值不可变，虽然看上去可以改变内容，但其实是地址变了，内存中新开辟了一个内存空间。

```js
var str = 'abc';
str = 'hello';
// 当重新给Str赋值的时候，常量'abc'不会被修改，依然在内存中
// 重新给字符串赋值，会重新在内存中开辟空间，这个特点就是字符串的不可变
// 由于字符串的不可变，在大量拼接字符串的时候会有效率问题
var str = '';
for (var i = 1;i < 10000; i++) {
    str += i;
}
console.log(str); // 这个结果需要花费大量时间，因为需要不断开辟新空间。
```

### 根据字符返回位置

| 方法名                             | 说明                                                         |
| ---------------------------------- | ------------------------------------------------------------ |
| indexOf('要查找的字符',开始的位置) | 返回指定内容在元字符串中的位置，如果找不到就返回-1，开始的位置是index索引号 |
| lastIndexOf()                      | 从后往前找，只找第一个匹配的                                 |

### 根据位置返回字符

| 方法名            | 说明                        | 使用                         |
| ----------------- | --------------------------- | ---------------------------- |
| charAt(index)     | 返回指定位置的字符          | str.charAt(0)                |
| charCodeAt(index) | 获取指定位置处字符的ascll码 | str.charCodeAt(0)            |
| str[index]        | 获取指定位置处字符          | Html5,ie8+支持和charAt()等效 |

### 字符串操作方法

| 方法名                    | 说明                                                         |
| ------------------------- | ------------------------------------------------------------ |
| concat(str1,str2,str3...) | concat用于连接连个或多个字符串。凭借字符串，等效于+，+更常用 |
| substr(start,length)      | 从start位置开始，length取得个数 重点                         |
| slice(start,end)          | 从start位置开始，截取到end位置，end取不到                    |
| substring(start,end)      | 从start位置开始，截取到end位置，end取不到 基本和slice相同，但是不接受负值 |

### replace()方法

用于在字符串中用一些字符替换另一些字符。前者可以是正则表达式。

```js
replace(被替换的,要替换的)
```

### split()方法

切分字符串成数组。

```js
var str = 'a,b,c,d';
console.log(str.split(',')); // [a,b,c,d]
```

### 转换大小写

- toUpperCase() //转换大写

- toLowerCase() //转换小写

# Web APIs和JS基础关联性

## JS基础阶段

- 我们学习的是 ECMAScript 标准规定的基本语法

- 要求同学们掌握 JS 基础语法

- 只学习基本语法，做不了常用的网页交互效果

- 目的是为了 JS 后面的课程打基础、做铺垫

## Web APIs 阶段

- Web APIs 是 W3C 组织的标准

- Web APIs 我们主要学习 DOM 和 BOM

- Web APIs 是我们 JS 所独有的部分

- 我们主要学习页面交互功能

- 需要使用 JS 基础的课程内容做基础

## API

**API** 是给程序员提供的一种工具，以便能更轻松的实现想要完成的功能。

## Web API

Web API 是浏览器提供的一套操作浏览器功能和页面元素的 API ( BOM 和 DOM )。

## 总结

- **API 是为我们程序员提供的一个接口，帮助我们实现某种功能，我们会使用就可以了，不必纠结内部如何实现**

- Web API 主要是针对于浏览器提供的接口，主要针对于浏览器做交互效果。

- Web API 一般都有输入和输出（函数的传参和返回值），Web API 很多都是方法（函数）

- 学习 Web API 可以结合前面学习内置对象方法的思路学习

# DOM

文档对象模型（Document Object Model，简称 **DOM**），是 W3C 组织推荐的处理可扩展标记语言（HTML或者XML）的标准**编程接口**。

W3C 已经定义了一系列的 DOM 接口，通过这些 DOM 接口可以改变网页的内容、结构和样式。

## DOM树

- 文档：一个页面就是一个文档，DOM 中使用 document 表示

- 元素：页面中的所有标签都是元素，DOM 中使用 element 表示

- 节点：网页中的所有内容都是节点（标签、属性、文本、注释等），DOM 中使用 node 表示

## 如何获取页面元素

### 根据 ID 获取

使用 getElementById() 方法可以获取带有 ID 的元素对象。

```html
<div id='time'>2018-08-08</div>
<script>
    //返回的是一个对象
    var timer = document.getElementById('time');
	console.dir(timer);
</script>
```

使用 console.dir() 可以打印我们获取的元素对象，更好的查看对象里面的属性和方法。

### 根据标签名获取

1 使用 getElementsByTagName() 方法可以返回带有指定标签名的**对象的集合。**(**返回的是伪数组行式储存的**)

```html
<ul>
    <li>愿得一人心</li>
    <li>愿得一人心</li>
    <li>愿得一人心</li>
    <li>愿得一人心</li>
</ul> 
<script>
	var lis = document.getElementsByTagName('li');
    console.log(lis);
</script>
```

- 因为得到的是一个**对象的集合**，所以我们想要操作里面的元素就需要遍历。

- 得到元素对象是动态的

- 如果获取不到元素,则返回为空的伪数组(因为获取不到对象)

2 还可以获取某个元素(父元素)内部**所有指定标签名的子元素**.

```html
<ol>
    <li>愿得一人心</li>
    <li>愿得一人心</li>
    <li>愿得一人心</li>
    <li>愿得一人心</li>
</ul> 
<script>
	var lis = element.getElementsByTagName('ol[0]');
    console.log(lis);
</script>
```

- 父元素必须是**单个对象(必须指明是哪一个元素对象)**. 获取的时候不包括父元素自己。

### 通过 HTML5 新增的方法获取

```html
<div class="box">盒子</div>
<div class="box">盒子</div>
<script>
    // 根据类名返回元素对象集合
    var boxs = document.getElementsByClassName('box');
    // 根据指定选择器返回第一个元素对象
    var firstbox = document.querySelector('.box');
    var nav = document.querySelector('#nav');   
    var lis = document.querySelector('li');   
    // 根据指定选择器返回所有的元素对象集合
    var Allbox = document.querySelectorAll('.box'); 
</script>
```

### 特殊元素获取

```js
// 返回body元素对象
var bodyEle = doucumnet.body;
// 返回html元素对象
var htmlEle = document.documentElement;  
```

## 事件

触发--响应机制。

### 三要素

- 事件源 （谁）

-  事件类型 （什么事件）

-  事件处理程序 （做啥）

### 执行事件的步骤

- 获取事件源

- 注册事件（绑定事件）

- 添加事件处理程序（采取函数赋值形式）

```js
var btn = document.getElementById('btn');
btn.onclick = function() {
  alert('你好吗');  
};
```

### 常见的鼠标事件

| 鼠标事件    | 触发条件         |
| ----------- | ---------------- |
| onclick     | 鼠标点击左键触发 |
| onmouseover | 鼠标经过触发     |
| onmouseout  | 鼠标离开触发     |
| onfocus     | 获取鼠标焦点触发 |
| onblur      | 失去鼠标焦点触发 |
| onmousemove | 鼠标移动触发     |
| onmouseup   | 鼠标弹起触发     |
| onmousedown | 鼠标按下触发     |

## 操作元素

我们可以利用 DOM 操作元素来改变元素里面的内容 、属性等。注意以下都是**属性**。

### 改变元素内容

从起始位置到终止位置的内容, 但它去除 html 标签， 同时空格和换行也会去掉`element.innerText`（老IE）

起始位置到终止位置的全部内容，包括 html 标签，同时保留空格和换行`element.innerHTML`（W3C标准）

- this指当前元素

```js
//通过点击获取时间
// 1. 获取元素 
        var btn = document.querySelector('button');
        var div = document.querySelector('div');
// 2.注册事件
        btn.onclick = function() {
            // div.innerText = '2019-6-6';
            div.innerHTML = getDate();
        }

        function getDate() {
            var date = new Date();
            // 我们写一个 2019年 5月 1日 星期三
            var year = date.getFullYear();
            var month = date.getMonth() + 1;
            var dates = date.getDate();
            var arr = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
            var day = date.getDay();
            return '今天是：' + year + '年' + month + '月' + dates + '日 ' + arr[day];
        }
```

### 常用元素的属性操作

- innerText、innerHTML 改变元素内容 普通盒子才能用
- src、href
- id、alt、title

```html
// 通过点击不同的图片显示不同内容
<button id="ldh">刘德华</button>
    <button id="zxy">张学友</button> <br>
    <img src="images/ldh.jpg" alt="" title="刘德华">

    <script>
        // 修改元素属性  src
        // 1. 获取元素
        var ldh = document.getElementById('ldh');
        var zxy = document.getElementById('zxy');
        var img = document.querySelector('img');
        // 2. 注册事件  处理程序
        zxy.onclick = function() {
            img.src = 'images/zxy.jpg';
            img.title = '张学友思密达';
        }
        ldh.onclick = function() {
            img.src = 'images/ldh.jpg';
            img.title = '刘德华';
        }
    </script>
```

### 表单元素的属性操作

 type、value、checked、selected、disabled

### 样式属性操作

我们可以通过 JS 修改元素的大小、颜色、位置等样式。

```js
element.style     行内样式操作
element.className 类名样式操作
```

```js
//通过点击隐藏盒子
// 1. 获取元素 
var btn = document.querySelector('.close-btn');
var box = document.querySelector('.box');
// 2.注册事件 程序处理
btn.onclick = function() {
    box.style.display = 'none';
}
```

```js
// 精灵图导入
var lis = document.querySelectorAll('li');
for (var i = 0; i < lis.length; i++) {
// 让索引号 乘以 44 就是每个li 的背景y坐标 index就是我们的y坐标
	var index = i * 44;
	lis[i].style.backgroundPosition = '0 -' + index + 'px';
}
```

- JS 里面的样式采取**驼峰命名法** 比如 fontSize、 backgroundColor

- JS 修改 style 样式操作，产生的是行内样式，CSS 权重比较高

- element.style适合修改样式比较少的情况。

```html
// 通过点击改变样式
<style>
    .change {
        color: #fff;
        font-size: 25px;
    }
</style>
<div>
    文本
</div>
<script>
    var test = document.querySeletor('div');
    test.onclick = function() {
        this.className = 'change';
    }
</script>
```

- 如果样式修改较多，可以采取操作类名方式更改元素样式
- class因为是个保留字，因此使用className来操作元素类名属性
- className 会直接更改元素的类名，会覆盖原先的类名。

- 如果想要保留原先的类名，我们可以这么做 多类名选择器

```js
this.className = 'first change';
```

### 排他思想

- 干掉其他人
- 留下我自己

### 自定义属性的操作

#### 获取属性值

```js
element.属性  // 获取属性值。
element.getAttribute('属性'); // 获取属性值
```

- 区别

```js
element.属性  // 获取内置属性值（元素本身自带的属性）
element.getAttribute('属性'); // 主要获得自定义的属性 （标准） 我们程序员自定义的属性
```

#### 设置属性值

```js
element.属性 = '值'  // 设置内置属性值。
element.setAttribute('属性', '值');  //属性赋值
```

- 区别

```js
element.属性  // 设置内置属性值
element.setAttribute(‘属性’);  // 主要设置自定义的属性 （标准）
```

#### 移除属性

```js
element.removeAttribute('属性');
```

```js
//导航栏题目
// 获取元素
var tab_list = document.querySelector('.tab_list');
var lis = tab_list.querySelectorAll('li');
var items = document.querySelectorAll('.item');
// for循环绑定点击事件
for (var i = 0; i < lis.length; i++) {
    // 开始给5个小li 设置索引号 
    lis[i].setAttribute('index', i);
    lis[i].onclick = function() {
        // 1. 上的模块选项卡，点击某一个，当前这一个底色会是红色，其余不变（排他思想） 修改类名的方式
        // 干掉所有人 其余的li清除 class 这个类
        for (var i = 0; i < lis.length; i++) {
            lis[i].className = '';
        }
        // 留下我自己 
        this.className = 'current';
        // 2. 下面的显示内容模块
        var index = this.getAttribute('index');
        console.log(index);
        // 干掉所有人 让其余的item 这些div 隐藏
        for (var i = 0; i < items.length; i++) {
            items[i].style.display = 'none';
        }
        // 留下我自己 让对应的item 显示出来
        items[index].style.display = 'block';
    }
}
```

### H5自定义属性

是为了保存并使用数据。有些数据可以保存到页面中而不用保存到数据库中。

#### 设置H5自定义属性

H5规定自定义属性data-开头做为属性名并且赋值。

```html
<div data-index=“1”></div>
// 使用 JS 设置  
element.setAttribute('data-index', 2)
```

#### 获取H5自定义属性

- 兼容性获取  element.getAttribute(‘data-index’);

- H5新增 element.dataset.index 或者 element.dataset[‘index’]  ie 11才开始支持

### 节点操作

利用DOM提供的方法获取元素逻辑性不强、繁琐。利用节点层级关系获取元素，逻辑性强，但兼容性稍差。

一般地，节点至少拥有nodeType（节点类型）、nodeName（节点名称）和nodeValue（节点值）这三个基本属性。

- 元素节点  nodeType 为 1

- 属性节点 nodeType 为 2

- 文本节点 nodeType 为 3 （文本节点包含文字、空格、换行等）

我们在实际开发中，节点操作主要操作的是**元素节点**。

#### 父级节点

```js
node.parentNode
```

- parentNode 属性可返回某节点的父节点，注意是最近的一个父节点

- 如果指定的节点没有父节点则返回 null 

```js
var erweima = document.querySelector('.erweima');
// 得到的是锂元素最近的父级节点，没有返回
console.log(erweima.parentNode);
```

#### 子节点

```js
// 返回包含指定节点的子节点的集合，该集合为即时更新的集合。
1.parent.childNodes（标准）
// 是一个只读属性，返回所有的子元素节点。它只返回子元素节点，其余节点不返回 （这个是我们重点掌握的）。虽然children 是一个非标准，但是得到了各个浏览器的支持，因此我们可以放心使用。
2.parentNode.children(非标准)
// 返回第一个子节点，找不到则返回null。同样，也是包含所有的节点。
3.parentNode.firstChild
// 返回最后一个子节点，找不到则返回null。同样，也是包含所有的节点。
4. parentNode.lastChild    
// 返回第一个子元素节点，找不到则返回null。 
5. parentNode.firstElementChild 
// 返回最后一个子元素节点，找不到则返回null。
6.parentNode.lastElementChild  
```

```js
// DOM里面的获取方法
var ul = document.querySelector('ul');
var lis = ul.querySelectorAll('li');
// 子节点包括了元素节点文本节点
var ul = document.querySelector('ul');
console.log(ul.childNodes);
```

- 返回值里面包含了所有的子节点，包括元素节点，文本节点等。
- 5、6方法有兼容性问题，IE9 以上才支持。
- **解决方案：**
  - 如果想要第一个子元素节点，可以使用 `parentNode.chilren[0] `

  - 如果想要最后一个子元素节点，可以使用`parentNode.chilren[parentNode.chilren.length - 1] `

如果只想要获得里面的元素节点，则需要专门处理。 **所以我们一般不提倡使用childNodes。**

```js
// 专门处理后
var ul = document. querySelector('ul');
for(var i = 0; i < ul.childNodes.length;i++) {
	if (ul.childNodes[i].nodeType == 1) {
    // ul.childNodes[i] 是元素节点
    	console.log(ul.childNodes[i]);
    }
}
```

#### 兄弟节点

```js
// 返回当前元素的下一个兄弟节点，找不到则返回null。同样，也是包含所有的节点
1. node.nextSibling
// 返回当前元素上一个兄弟节点，找不到则返回null。同样，也是包含所有的节点
2. node.previousSibling   
// 返回当前元素下一个兄弟元素节点，找不到则返回null。
3. node.nextElementSibling  
// 返回当前元素上一个兄弟元素节点，找不到则返回null。
4. node.previousElementSibling     
```

- 3、4方法有兼容性问题，ie9以上才支持。
  - **解决方案**：自己封装一个函数

```js
function getNextElementSibling(element) {
    var el = element;
    while (el = el.nextSibling) {
        if (el.nodeType === 1) {
            return el;
        }
    }
    return null;
}  
```

#### 创建节点

```js
// 方法创建由 tagName 指定的 HTML 元素。因为这些元素原先不存在，是根据我们的需求动态生成的，所以我们也称为动态创建元素节点
 document.createElement('tagName')
 document.write()
 element.innerHTML
```

- document.write 是直接将内容写入页面的内容流，但是文档流执行完毕，则它会导致页面全部重绘

- innerHTML 是将内容写入某个 DOM 节点，不会导致页面全部重绘

- innerHTML 创建多个元素效率更高（不要拼接字符串，采取数组形式拼接），结构稍微复杂

- createElement() 创建多个元素效率稍低一点点，但是结构更清晰

**总结**：不同浏览器下，innerHTML 效率要比 creatElement 高

#### 添加节点

```js
// 方法将一个节点添加到指定父节点的子节点列表末尾。类似于 CSS 里面的 after 伪元素。
 1. node.appendChild(child)
// 方法将一个节点添加到父节点的指定子节点前面。类似于 CSS 里面的 before 伪元素。
 2. node.insertBefore(child, 指定元素) 
```

```js
// 1.创建元素节点
var li = document.createElement('li');
// 2.添加节点 添加到指定父节点的子节点列表末尾
var ul = doucument.querySelector('ul');
ul.appendChild(li);
// 3.添加节点 添加到父节点的指定子节点前面
ul.insertBefore(li,ul.children[0]);
```

#### 删除节点

```js
// 方法从 DOM 中删除一个子节点，返回删除的节点
 node.removeChild(child) 
```

#### 复制节点

```js
// 方法返回调用该方法的节点的一个副本。 也称为克隆节点/拷贝节点
 node.cloneNode() 
```

- 如果括号参数为空或者为 **false ，则是浅拷贝**，即只克隆复制节点本身，不克隆里面的子节点。

- 如果括号参数为 **true ，则是深度拷贝**，会复制节点本身以及里面所有的子节点。

```js
// 1.先去准备好学生的数据
var datas = [{
    name: '魏璎珞',
    subject: 'JavaScript',
    score: 100
}, {
    name: '弘历',
    subject: 'JavaScript',
    score: 98
}];
// 2. 往tbody 里面创建行： 有几个人（通过数组的长度）我们就创建几行
var tbody = document.querySelector('tbody');
for (var i = 0; i < datas.length; i++) { // 外面的for循环管行 tr
    // 1. 创建 tr行
    var tr = document.createElement('tr');
    tbody.appendChild(tr);
    // 2. 行里面创建单元格(跟数据有关系的3个单元格) td 单元格的数量取决于每个对象里面的属性个数  for循环遍历对象 datas[i]
    for (var k in datas[i]) { // 里面的for循环管列 td
                // 创建单元格 
                var td = document.createElement('td');
                // 把对象里面的属性值 datas[i][k] 给 td  
                // console.log(datas[i][k]);
                td.innerHTML = datas[i][k];
                tr.appendChild(td);
            }
            // 3. 创建有删除2个字的单元格 
            var td = document.createElement('td');
            td.innerHTML = '<a href="javascript:;">删除 </a>';
            tr.appendChild(td);

        }
// 4. 删除操作 开始 
var as = document.querySelectorAll('a');
for (var i = 0; i < as.length; i++) {
    as[i].onclick = function() {
        // 点击a 删除 当前a 所在的行(链接的爸爸的爸爸)  node.removeChild(child)  
        tbody.removeChild(this.parentNode.parentNode)
    }
}
```

## 事件

### 注册事件

给元素添加事件，称为**注册事件**或者**绑定事件**。

注册事件有两种方式：传统方式和方法监听注册方式

```js
// 方法将指定的监听器注册到 eventTarget（目标对象）上，当该对象触发指定的事件时，就会执行事件处理函数。
eventTarget.addEventListener(type, listener[,useCapture])  
```

```js
var btns = document.querySelectorAll('button');
// 1. 传统方式注册事件
btns[0].onclick = function() {
    alert('hi');
}
btns[0].onclick = function() {
    alert('hao a u');
}
// 2. 事件侦听注册事件 addEventListener 
// (1) 里面的事件类型是字符串 必定加引号 而且不带on
// (2) 同一个元素 同一个事件可以添加多个侦听器（事件处理程序）
btns[1].addEventListener('click', function() {
    alert(22);
})
btns[1].addEventListener('click', function() {
    alert(33);
})
```

- 传统方法注册事件相同事件会后来者覆盖先前者，而事件侦听注册事件并不会，不过会有兼容性问题

### 删除事件

```js
// 传统删除事件方式
eventTarget.onclick = null;
// 方法监听删除事件方式
eventTarget.removeEventListener(type, listener[, useCapture]);
eventTarget.detachEvent(eventNameWithOn, callback);
```

```js
var divs = document.querySelectorAll('div');
divs[0].onclick = function() {
    alert(11);
    // 1. 传统方式删除事件
    divs[0].onclick = null;
}
// 2. removeEventListener 删除事件
divs[1].addEventListener('click', fn) // 里面的fn 不需要调用加小括号
function fn() {
    alert(22);
    divs[1].removeEventListener('click', fn);
}
```

### DOM事件流

**事件流**描述的是从页面中接收事件的顺序。

DOM 事件流分为3个阶段： **捕获阶段、当前目标阶段、 冒泡阶段** 

- JS 代码中只能执行捕获或者冒泡其中的一个阶段。
- onclick 和 attachEvent 只能得到冒泡阶段。
- addEventListener(type, listener[, useCapture])第三个参数如果是 true，表示在事件捕获阶段调用事件处理程序；如果是 false（不写默认就是false），表示在事件冒泡阶段调用事件处理程序。
- 实际开发中我们很少使用事件捕获，我们更关注事件冒泡。
- 有些事件是没有冒泡的，比如 onblur、onfocus、onmouseenter、onmouseleave

```js
// 以下捕获输出顺序为 father son
var son = document.querySelector('.son');
son.addEventListener('click', function() {
    alert('son');
}, true);
var father = document.querySelector('.father');
father.addEventListener('click', function() {
    alert('father');
}, true);
// 以下冒泡输出顺序为 son father document
var son = document.querySelector('.son');
son.addEventListener('click', function() {
    alert('son');
}, false);
var father = document.querySelector('.father');
father.addEventListener('click', function() {
    alert('father');
}, false);
document.addEventListener('click', function() {
    alert('document');
}) 
```

### 事件对象

事件发生后，跟事件相关的一系列信息数据的集合都放到这个对象里面，这个对象就是事件对象 event，它有很多属性和方法。

```js
eventTarget.onclick = function(event) {} 
eventTarget.addEventListener('click', function(event) {}）
// 这个 event 就是事件对象，我们还喜欢的写成 e 或者 evt       // 当我们注册事件时， event 对象就会被系统自动创建，并依次传递给事件监听器（事件处理函数）。
```

- 解决兼容性：e = e || window.event;

- e.target 和 this 的区别：

   this 是事件绑定的元素， 这个函数的调用者（绑定这个事件的元素） 

   e.target 是事件触发的元素。

```js
var div = document.querySelector('div');
div.addEventListener('click', function(e) {
    console.log(e.target);
    console.log(this);
})
```

### 阻止事件冒泡的两种方式

事件冒泡：开始时由最具体的元素接收，然后逐级向上传播到到 DOM 最顶层节点。

```js
 标准写法：利用事件对象里面的 stopPropagation()方法
 e.stopPropagation() 
 非标准写法：IE 6-8  利用事件对象 cancelBubble 属性 
 e.cancelBubble = true;
```

```js
// 本来点击son部分会出现 son father document 但son添加了组织冒泡方式后， 点击son，只会出现son
var son = document.querySelector('.son');
son.addEventListener('click', function(e) {
    alert('son');
    e.stopPropagation(); // stop 停止  Propagation 传播
    e.cancelBubble = true; // 非标准 cancel 取消 bubble 泡泡
}, false);

var father = document.querySelector('.father');
father.addEventListener('click', function() {
    alert('father');
}, false);
document.addEventListener('click', function() {
    alert('document');
})
```

### 事件委托

不是每个子节点单独设置事件监听器，而是事件监听器设置在其父节点上，然后利用冒泡原理影响设置每个子节点。

```html
<ul>
    <li>知否知否，点我应有弹框在手！</li>
    <li>知否知否，点我应有弹框在手！</li>
    <li>知否知否，点我应有弹框在手！</li>
    <li>知否知否，点我应有弹框在手！</li>
    <li>知否知否，点我应有弹框在手！</li>
</ul>
<script>
    // 事件委托的核心原理：给父节点添加侦听器， 利用事件冒泡影响每一个子节点
    var ul = document.querySelector('ul');
    ul.addEventListener('click', function(e) {
        // alert('知否知否，点我应有弹框在手！');
        // e.target 这个可以得到我们点击的对象
        e.target.style.backgroundColor = 'pink';


    })
</script>
```

### 常用的鼠标事件

| 鼠标事件    | 触发条件         |
| ----------- | ---------------- |
| onclick     | 鼠标点击左键触发 |
| onmouseover | 鼠标经过触发     |
| onmouseout  | 鼠标离开触发     |
| onfocus     | 获取鼠标焦点触发 |
| onblur      | 失去鼠标焦点触发 |
| onmousemove | 鼠标移动触发     |
| onmouseup   | 鼠标弹起触发     |
| onmousedown | 鼠标按下触发     |

#### 静止鼠标右键菜单

contextmenu主要控制应该何时显示上下文菜单，主要用于程序员取消默认的上下文菜单

```js
document.addEventListener('contextmenu', function(e) {
	e.preventDefault();
})
```

#### 禁止鼠标选中

（selectstart 开始选中）

```js
document.addEventListener('selectstart', function(e) {
    e.preventDefault();
})
```

```html
我是一段不愿意分享的文字
<script>
    // 1. contextmenu 我们可以禁用右键菜单
    document.addEventListener('contextmenu', function(e) {
        e.preventDefault();
    })
    // 2. 禁止选中文字 selectstart
    document.addEventListener('selectstart', function(e) {
        e.preventDefault();

    })
</script>
```

#### 鼠标事件对象

event对象代表事件的状态，跟事件相关的一系列信息的集合。现阶段我们主要是用鼠标事件对象 MouseEvent 和键盘事件对象 KeyboardEvent。

| 鼠标事件对象 | 说明                                   |
| ------------ | -------------------------------------- |
| e.clientX    | 返回鼠标相对于浏览器窗口可视区的X坐标  |
| e.clientY    | 返回鼠标相对于浏览器窗口可视区的Y坐标  |
| e.pageX      | 返回鼠标相对于文档页面的X坐标 IE9+支持 |
| e.pageY      | 返回鼠标相对于文档页面的Y坐标 IE9+支持 |
| e.screenX    | 返回鼠标相对于电脑屏幕的X坐标          |
| e.screenY    | 返回鼠标相对于电脑屏幕的Y坐标          |

```js
// 跟随鼠标的天使
var pic = document.querySelector('img');
document.addEventListener('mousemove', function(e) {
    var x = e.pageX;
    var y = e.pageY;
    pic.style.top = y - 40 + 'px';
    pic.style.left = x - 50 + 'px';
})
```

### 常用的键盘事件

| 键盘事件   | 触发条件                                    |
| ---------- | ------------------------------------------- |
| onkeyup    | 某个键盘按键被松开时触发                    |
| onkeydown  | 某个键盘按键被按下时触发                    |
| onkeypress | 某个键盘按键被按下时触发 但它不识别功能键。 |

**注意：**

- 如果使用addEventListener 不需要加 on

- onkeypress 和前面2个的区别是，它不识别功能键，比如左右箭头，shift 等。

- 三个事件的执行顺序是： keydown -- keypress --- keyup

- onkeydown 和 onkeyup 不区分字母大小写，onkeypress 区分字母大小写。

#### 键盘事件对象

| 键盘事件对象属性 | 说明              |
| ---------------- | ----------------- |
| keyCode          | 返回该键的ASCII值 |

```js
// 按下S键就让光标定位到搜索框
var search = document.querySelector('input');
document.addEventListener('keyup',function(e){
    if(e.keyCode === 83){
        search.focus();
    }
})
```

# BOM

BOM（Browser Object Model）即**浏览器对象模型**，它提供了独立于内容而**与浏览器窗口进行交互的对象**，其核心对象是 window。

BOM 缺乏标准，JavaScript 语法的标准化组织是 ECMA，DOM 的标准化组织是 W3C，BOM 最初是Netscape 浏览器标准的一部分。

- DOM是文档对象模型，BOM是浏览器对象模型 

- DOM 就是把「文档」当做一个「对象」来看待，BOM把「浏览器」当做一个「对象」来看待

- DOM 的顶级对象是 document，BOM 的顶级对象是 window

- DOM 主要学习的是操作页面元素，BOM 学习的是浏览器窗口交互的一些对象

- DOM 是 W3C 标准规范，BOM 是浏览器厂商在各自浏览器上定义的，兼容性较差

- BOM 比 DOM 更大，它包含 DOM。

## window对象的常见事件

### 窗口加载事件

window.onload 是窗口 (页面）加载事件,当文档内容完全加载完成会触发该事件(包括图像、脚本文件、CSS 文件等), 就调用的处理函数。

```js
1 window.onload = function(){}
2 window.addEventListener("load",function(){});
3document.addEventListener('DOMContentLoaded',function(){})
```

- 有了 window.onload 就可以把 JS 代码写到页面元素的上方，因为 onload 是等页面内容全部加载完毕，再去执行处理函数.
- window.onload 传统注册事件方式 只能写一次，如果有多个，会以最后一个 window.onload 为准。
-  如果使用 addEventListener 则没有限制

- DOMContentLoaded 事件触发时，仅当DOM加载完成，不包括样式表，图片，flash等等.**推荐使用**

### 调整窗口大小事件

```js
// window.onresize 是调整窗口大小加载事件,  当触发时就调用的处理函数。
1 window.onresize = function(){}
2 window.addEventListener("resize",function(){});
```

- 只要窗口大小发生像素变化，就会触发这个事件。
- 我们经常利用这个事件完成响应式布局。 window.innerWidth 当前屏幕的宽度

### 定时器

```js
// 两种设置定时器
// setTimeout() 方法用于设置一个定时器，该定时器在定时器到期后执行调用函数。也称为回调函数 callback
1 setTimeout(调用函数, [延迟的毫秒数]);
// setInterval() 方法重复调用一个函数，每隔这个时间，就去调用一次回调函数。
2 setInterval(回调函数, [间隔的毫秒数]);
// 两种停止定时器
// clearTimeout()方法取消了先前通过调用 setTimeout() 建立的定时器。
1 window.clearTimeout(定时器的标识符);
// clearInterval()方法取消了先前通过调用 setInterval()建立的定时器
2 window.clearInterval(intervalID);
```

- window 可以省略。

- 调用函数可以直接写函数，或者写函数名或者采取字符串 '函数名()'  三种形式。

- 间隔的毫秒数省略默认是 0，如果写，必须是毫秒，表示每隔多少毫秒就自动调用这个函数。

- 因为定时器可能有很多，所以我们经常给定时器赋值一个标识符。

```html
手机号码： <input type="number"> <button>发送</button>
<script>
    // 按钮点击之后，会禁用 disabled 为true 
    // 同时按钮里面的内容会变化， 注意 button 里面的内容通过 innerHTML修改
    // 里面秒数是有变化的，因此需要用到定时器
    // 定义一个变量，在定时器里面，不断递减
    // 如果变量为0 说明到了时间，我们需要停止定时器，并且复原按钮初始状态
    var btn = document.querySelector('button');
    var time = 59; // 定义剩下的秒数
    btn.addEventListener('click', function() {
        btn.disabled = true;
        var timer = setInterval(function() {
            if (time == 0) {
                // 清除定时器和复原按钮
                clearInterval(timer);
                btn.disabled = false;
                btn.innerHTML = '发送';
            } else {
                btn.innerHTML = '还剩下' + time + '秒';
                time--;
            }
        }, 1000);
    })
</script>
```

## JS执行机制

JavaScript 语言的一大特点就是**单线程**，也就是说，同一个时间只能做一件事。为了解决这个问题，利用多核 CPU 的计算能力，HTML5 提出 Web Worker 标准，允许 JavaScript 脚本创建多个线程。于是，JS 中出现了**同步和异步**。

### 同步

前一个任务结束后再执行后一个任务，程序的执行顺序与任务的排列顺序是一致的、同步的

### 异步

你在做一件事情时，因为这件事情会花费很长时间，在做这件事的同时，你还可以去处理其他事情

### 同步任务

同步任务都在主线程上执行，形成一个执行栈。

### 异步任务

JS 的异步是通过回调函数实现的。

一般而言，异步任务有以下三种类型:

- 普通事件，如 click、resize 等
- 资源加载，如 load、error 等
- 定时器，包括 setInterval、setTimeout 等

异步任务相关回调函数添加到**任务队列**中（任务队列也称为消息队列）。

### 执行机制

- 先执行执行栈中的同步任务。
- 异步任务（回调函数）放入任务队列中。
- 一旦执行栈中的所有同步任务执行完毕，系统就会按次序读取任务队列中的异步任务，于是被读取的异步任务结束等待状态，进入执行栈，开始执行。

第三步**一直循环执行**！由于主线程不断的重复获得任务、执行任务、再获取任务、再执行，所以这种机制被称为**事件循环**（ event loop）。

## location对象

window 对象给我们提供了一个 location 属性用于**获取或设置窗体的 URL**，并且可以用于解析 URL 。 因为这个属性返回的是一个对象，所以我们将这个属性也称为 location 对象。

### URL

统一资源定位符 (Uniform Resource Locator, URL) 是互联网上标准资源的地址。互联网上的每个文件都有一个唯一的 URL，它包含的信息指出文件的位置以及浏览器应该怎么处理它。

```
 protocol://host[:port]/path/[?query]#fragment
 http://www.itcast.cn/index.html?name=andy&age=18#link
```

| 组成     | 说明                                |
| -------- | ----------------------------------- |
| protocol | 通信协议 常用的http ftp maito等     |
| host     | 主机（域名）www.baidu.com           |
| port     | 端口号，可选                        |
| path     | 路径                                |
| query    | 参数 以键值对的形式 通过&符号分隔开 |
| fragment | 片段 #后面内容 常见于链接 锚点      |

### 属性

| 属性              | 返回值                             |
| ----------------- | ---------------------------------- |
| **location.href** | 获取或设置整个URL                  |
| location.host     | 返回主机（域名）                   |
| location.post     | 端口号，可选                       |
| location.pathname | 返回路径                           |
| **search**        | 返回参数                           |
| location.hash     | 返回片段 #后面内容 常见于链接 锚点 |

```html
// 页面之间传输数据
// login.html
<form action="index.html">
    用户：<input type='text' name='uname'>
    <input type='submit' value='登录'>
</form>
// index.html
<div></div>
<script>
    console.log(location.search); // ?uname=andy
	var params = location.search.substr(1); // uname=andy
    var arr = params.split('=');
    console.log(arr);
    var div = document.querySelector('div');
    div.innerHTML = 'hello ' + arr[1]; //hello ANDY    
</script>
```

### 方法

| 对象方法           | 返回值                                         |
| ------------------ | ---------------------------------------------- |
| location.assign()  | 跟href一样，可以跳转页面                       |
| location.replace() | 替换当前页面，因为不记录历史，所以不能后退页面 |
| location.reload()  | 重新加载页面，刷新                             |

## navigator对象

navigator 对象包含有关浏览器的信息，它有很多属性，我们最常用的是 userAgent，该属性可以返回由客户机发送服务器的 user-agent 头部的值。

```js
// 下面前端代码可以判断用户那个终端打开页面，实现跳转
if((navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i))) {
    window.location.href = "";     //手机
 } else {
    window.location.href = "";     //电脑
 }
```

## history对象

window 对象给我们提供了一个 history 对象，与浏览器历史记录进行交互。该对象包含用户（在浏览器窗口中）访问过的 URL。

| 对象方法  | 作用                                            |
| --------- | ----------------------------------------------- |
| back()    | 可以后退功能                                    |
| forward() | 前进功能                                        |
| go(参数)  | 前进后退功能 参数1前进1个页面 参数-1后退1个页面 |

## pc端网页特效

### 元素偏移量 offset

offset 翻译过来就是偏移量， 我们使用 offset 系列相关属性可以动态的得到该元素的位置（偏移）、大小等。

- 获得元素距离带有定位父元素的位置

- 获得元素自身的大小（宽度高度）

- 注意： 返回的数值都不带单位

| 属性                 | 作用                                                         |
| -------------------- | ------------------------------------------------------------ |
| element.offsetParent | 返回作为该元素带有定位的父级元素 如果父级都没有定位则返回body |
| element.offsetTop    | 返回元素相对带有定位父元素上方的偏移                         |
| element.offsetLeft   | 返回元素相对带有定位父元素左边框的偏移                       |
| element.offsetWidth  | 返回自身包括padding、边框、内容区的宽度，不带单位            |
| element.offsetHeight | 返回自身包括padding、边框、内容区的高度，不带单位            |

- offset 可以得到任意样式表中的样式值，style 只能得到行内样式表中的样式值
- offset 系列获得的数值是没有单位的，style.width 获得的是带有单位的字符串
- offsetWidth 包含padding+border+width,style.width 获得不包含padding和border 的值
- offsetWidth 等属性是只读属性，只能获取不能赋值.style.width 是可读写属性，可以获取也可以赋值

```js
// 获取鼠标在盒子内的坐标
var box = document.querySelector('.box');
box.addEventListener('mousemove', function(e) {
var x = e.pageX - this.offsetLeft;
var y = e.pageY - this.offsetTop;
this.innerHTML = 'x坐标是' + x + ' y坐标是' + y;
})
```

### 元素可视区 client

client 翻译过来就是客户端，我们使用 client 系列的相关属性来获取元素可视区的相关信息。通过 client 系列的相关属性可以动态的得到该元素的边框大小、元素大小等。

| 属性                 | 作用                                                         |
| -------------------- | ------------------------------------------------------------ |
| element.clientTop    | 返回元素上边框的大小                                         |
| element.clientLeft   | 返回元素左边框的大小                                         |
| element.clientWidth  | 返回自身包括padding、内容区的宽度，不含边框，返回值不带单位  |
| element.clientHeight | 返回自身包括padding、内容区的高度度，不含边框，返回值不带单位 |

### 立即执行函数

主要作用： 创建一个独立的作用域。 避免了命名冲突问题

```js
(function() {})();  
(function(){}());
```

```js
(function flexible(window, document) {
    // 获取的html 的根元素
    var docEl = document.documentElement
        // dpr 物理像素比
    var dpr = window.devicePixelRatio || 1

    // adjust body font size  设置我们body 的字体大小
    function setBodyFontSize() {
        // 如果页面中有body 这个元素 就设置body的字体大小
        if (document.body) {
            document.body.style.fontSize = (12 * dpr) + 'px'
        } else {
            // 如果页面中没有body 这个元素，则等着 我们页面主要的DOM元素加载完毕再去设置body
            // 的字体大小
            document.addEventListener('DOMContentLoaded', setBodyFontSize)
        } 
    }
    setBodyFontSize();

    // set 1rem = viewWidth / 10    设置我们html 元素的文字大小
    function setRemUnit() {
        var rem = docEl.clientWidth / 10
        docEl.style.fontSize = rem + 'px'
    }

    setRemUnit()

    // reset rem unit on page resize  当我们页面尺寸大小发生变化的时候，要重新设置下rem 的大小
    window.addEventListener('resize', setRemUnit)
        // pageshow 是我们重新加载页面触发的事件
    window.addEventListener('pageshow', function(e) {
        // e.persisted 返回的是true 就是说如果这个页面是从缓存取过来的页面，也需要从新计算一下rem 的大小
        if (e.persisted) {
            setRemUnit()
        }
    })

    // detect 0.5px supports  有些移动端的浏览器不支持0.5像素的写法
    if (dpr >= 2) {
        var fakeBody = document.createElement('body')
        var testElement = document.createElement('div')
        testElement.style.border = '.5px solid transparent'
        fakeBody.appendChild(testElement)
        docEl.appendChild(fakeBody)
        if (testElement.offsetHeight === 1) {
            docEl.classList.add('hairlines')
        }
        docEl.removeChild(fakeBody)
    }
}(window, document))
```

### 元素滚动 scroll

scroll 翻译过来就是滚动的，我们使用 scroll 系列的相关属性可以动态的得到该元素的大小、滚动距离等。

| 属性                 | 作用                                           |
| -------------------- | ---------------------------------------------- |
| element.scrollTop    | 返回被卷曲的上侧距离，返回数值不带单位         |
| element.scrollLeft   | 返回被卷曲的左侧距离，返回数值不带单位         |
| element.scrollWidth  | 返回自身实际的宽度，不含边框，返回数值不带单位 |
| element.scrollHeight | 返回自身实际的高度，不含边框，返回数值不带单位 |

如果浏览器的高（或宽）度不足以显示整个页面时，会自动出现滚动条。当滚动条向下滚动时，页面上面被隐藏掉的高度，我们就称为页面被卷去的头部。滚动条在滚动时会触发 onscroll 事件。

- 页面被卷去的头部：可以通过window.pageYOffset 获得 如果是被卷去的左侧 window.pageXOffset

- 注意，元素被卷去的头部是 element.scrollTop , 如果是页面被卷去的头部 则是 window.pageYOffset
- 卷去的部分可以用盒子的 offsetTop 

**总结**

| 大小对比            | 作用                                                        |
| ------------------- | ----------------------------------------------------------- |
| element.offsetWidth | 返回自身包括padding、边框、内容区的宽度，不带单位           |
| element.clientWidth | 返回自身包括padding、内容区的宽度，不含边框，返回值不带单位 |
| element.scrollWidth | 返回自身实际的宽度，不含边框，返回数值不带单位              |

- offset系列 经常用于获得元素位置  offsetLeft offsetTop

- client 经常用于获取元素大小 clientWidth clientHeight

- scroll 经常用于获取滚动距离 scrollTop scrollLeft 

- 注意页面滚动的距离通过 window.pageXOffset  获得

###  mouseenter鼠标事件

- 当鼠标移动到元素上时就会触发 mouseenter 事件

- 类似 mouseover，它们两者之间的差别是

- mouseover 鼠标经过自身盒子会触发，经过子盒子还会触发。 mouseenter 只会经过自身盒子触发

- 之所以这样，就是因为mouseenter不会冒泡

- 跟mouseenter搭配 鼠标离开 mouseleave 同样不会冒泡

### 动画函数封装

#### 动画实现原理

通过定时器 setInterval() 不断移动盒子位置。

实现步骤：

1. 获得盒子当前位置

2. 让盒子在当前位置加上1个移动距离

3. 利用定时器不断重复这个操作

4. 加一个结束定时器的条件

5. 注意此元素需要添加定位，才能使用element.style.left

#### 动画函数简单封装

注意函数需要传递2个参数，**动画对象**和**移动到的距离。**

如果多个元素都使用这个动画函数，每次都要var 声明定时器。我们可以给不同的元素使用不同的定时器（自己专门用自己的定时器）。

#### 缓慢效果原理

缓动动画就是让元素运动速度有所变化，最常见的是让速度慢慢停下来

思路：

- 让盒子每次移动的距离慢慢变小，速度就会慢慢落下来。

- 核心算法： (目标值 - 现在的位置 )  /  10  做为每次移动的距离 步长

- 停止的条件是： 让当前盒子位置等于目标位置就停止定时器 

- 注意步长值需要取整 

#### 动画函数添加回调函数

回调函数原理：函数可以作为一个参数。将这个函数作为参数传到另一个函数里面，当那个函数执行完之后，再执行传进去的这个函数，这个过程就叫做回调。

回调函数写的位置：定时器结束的位置。

```js
function animate(obj,target,callback) {
    clearInterval(obj.timer);
    obj.timer = setInterval(function () {
        var step = Math.ceil((target - obj.offsetLeft) / 10);
        if (obj.offsetLeft == target) {
            clearInterval(obj.timer);
            if (callback) {
                callback();
            }
        }
        obj.style.left = obj.offsetLeft + step + 'px';
    }, 15);
};
```

### 手动调用事件

元素.事件()直接触发。eg：arrow_r.click()

### 节流阀

防止轮播图按钮连续点击造成播放过快。

节流阀**目的**：当上一个函数动画内容执行完毕，再去执行下一个函数动画，让事件无法连续触发。

核心实现**思路**：利用回调函数，添加一个变量来控制，锁住函数和解锁函数。

### 窗口滚动到指定位置

滚动窗口至文档中的特定位置。

window.scroll(x, y) 

注意，里面的x和y 不跟单位，直接写数字

## 移动端网页特效

### 触屏事件

移动端浏览器兼容性较好，我们不需要考虑以前 JS 的兼容性问题，可以放心的使用原生 JS 书写效果，但是移动端也有自己独特的地方。比如**触屏事件** touch（也称触摸事件），Android 和 IOS 都有。

| 触屏touch事件 | 说明                          |
| ------------- | ----------------------------- |
| touchstart    | 手指触摸到一个DOM元素时触发   |
| touchmove     | 手指在一个DOM元素上滑动时触发 |
| touchend      | 手指在一个DOM元素上移开时触发 |

#### 触摸事件对象 TouchEvent

TouchEvent 是一类描述手指在触摸平面（触摸屏、触摸板等）的状态变化的事件。这类事件用于描述一个或多个触点，使开发者可以检测触点的移动，触点的增加和减少，等等.

touchstart、touchmove、touchend 三个事件都会各自有事件对象

| 触摸列表          | 说明                                             |
| ----------------- | ------------------------------------------------ |
| touches           | 正在触摸屏幕的所有手指的一个列表                 |
| **targetTouches** | 正在触摸当前DOM元素上的手指的一个列表            |
| changedTouches    | 手指状态发生了改变的列表，从无到有，从有到无变化 |

### 移动端拖动元素

1. touchstart、touchmove、touchend 可以实现拖动元素

2. 但是拖动元素需要当前手指的坐标值 我们可以使用 **targetTouches[0] 里面的pageX 和 pageY** 

3. 移动端拖动的原理：  手指移动中，计算出手指移动的距离。然后用盒子原来的位置 + 手指移动的距离

4. 手指移动的距离：  手指滑动中的位置 减去 手指刚开始触摸的位置

**拖动元素三步曲：**

（1） 触摸元素 touchstart： 获取手指初始坐标，同时获得盒子原来的位置

（2） 移动手指 touchmove： 计算手指的滑动距离，并且移动盒子

（3） 离开手指 touchend。

**注意**： 手指移动也会触发滚动屏幕所以这里要**阻止默认的屏幕滚动** e.preventDefault();

# 面向对象

在面向对象程序开发思想中，每一个对象都是功能中心，具有明确分工。

面向对象的特性：封装性、继承性、多态性。

## 对象

在 JavaScript 中，对象是一组无序的相关属性和方法的集合，所有的事物都是对象，例如字符串、数值、数组、函数等。

对象是由属性和方法组成的：

- 属性：事物的**特征，**在对象中用**属性**来表示（常用名词）
- 方法：事物的**行为，**在对象中用**方法**来表示（常用动词）

## 类

类抽象了对象的公共部分，它泛指某一大类（class）

对象特指某一个，通过类实例化一个具体的对象  

面向对象的思维特点: 

1.抽取（抽象）对象共用的属性和行为组织(封装)成一个**类**(模板)

2.对类进行实例化, 获取类的**对象**

### 创建类

```js
class name {
  // class body
}       
var xx = new name();     
```

- 注意： 类必须使用 new 实例化对象

### 类的constructor构造函数

constructor() 方法是类的构造函数(默认方法)，用于传递参数,返回实例对象，通过 new 命令生成对象实例时，自动调用该方法。如果没有显示定义, 类内部会自动给我们创建一个constructor()

```js
class Person {
    // constructor 构造方法或者构造函数
  constructor(name,age) {   
      this.name = name;
      this.age = age;
    }
}       
var ldh = new Person('刘德华', 18); 
console.log(ldh.name)    
```

### 类添加方法

```js
class Person {
  constructor(name,age) {   // constructor 构造器或者构造函数
      this.name = name;
      this.age = age;
    }
   say() {
      console.log(this.name + '你好');
   }
}     
var ldh = new Person('刘德华', 18); 
ldh.say()   
```

- 注意： 方法之间不能加逗号分隔，同时方法不需要添加 function 关键字。

## 类的继承

程序中的继承：子类可以继承父类的一些属性和方法。

```js
class Father {
      constructor(surname) {
        this.surname= surname;
      }
      say() {
        console.log('你的姓是' + this.surname);

       }
}
class Son extends Father{  // 这样子类就继承了父类的属性和方法

}
var damao= new Son('刘');
damao.say();          
```

- 就近原则，先查找子类。

### super关键字

super 关键字用于访问和调用对象父类上的函数。可以调用父类的构造函数，也可以调用父类的普通函数。

```js
 class Father {
    constructor(surname) {
        this.surname = surname;
     }
    saySurname() {
      console.log('我的姓是' + this.surname);
    }
}
class Son extends Father { // 这样子类就继承了父类的属性和方法
    constructor(surname, fristname) {
         super(surname);   // 调用父类的constructor(surname)
         this.fristname = fristname;
     }
    sayFristname() {
         console.log("我的名字是：" + this.fristname);

    }
}
var damao = new Son('刘', "德华");
damao.saySurname();
damao.sayFristname();            
```

-  注意: 子类在构造函数中使用super, **必须放到 this 前面** (必须先调用父类的构造方法,在使用子类构造方法)

**总结：**

- 在 ES6 中类没有变量提升，所以必须先定义类，才能通过类实例化对象

- 类里面的共有属性和方法一定要加this使用。

- 事件调用类的方法时方法不用加()，不然会立即执行。

  ```js
  this.btn = document.querySelector('button');
  this.btn.onclink = this.sing;
  //用this.sing();不管按钮点击是否都会立即执行。
  ```


- 类里面的this指向的是调用其的对象。

# tab案例增加知识

## 把创建的元素追加到对应的父元素中.

1.以前的做法: 动态创建元素 createElement , 但是元素里面内容较多, 需要innerHTML赋值,在 appendChild 追加到父元素里面.

2.现在高级做法:  利用 insertAdjacentHTML() 可以直接把字符串格式元素添加到父元素中

3.**appendChild 不支持追加字符串的子元素**, insertAdjacentHTML 支持追加字符串的元素

4.insertAdjacentHTML(追加的位置,‘要追加的字符串元素’) 

5.追加的位置有: **beforeend** 插入元素内部的最后一个子节点之后

## 双击禁止选择文字

window.getSelection ? window.getSelection().removeAllRanges() : document.selection.empty();

# 构造函数和原型

在 ES6之前 ，对象不是基于类创建的，而是用一种称为构建函数的特殊函数来定义对象和它们的特征。

创建对象可以通过以下三种方式：

1. 对象字面量

2. new Object()

3. 自定义构造函数

## 构造函数

**构造函数**是一种特殊的函数，主要用来初始化对象，即为对象成员变量赋初始值，它总与 new 一起使用。我们可以把对象中一些公共的属性和方法抽取出来，然后封装到这个函数里面。

- 静态成员：在构造函数本上添加的成员称为静态成员，只能由构造函数本身来访问

- 实例成员：在构造函数内部创建的对象成员称为实例成员，只能由实例化的对象来访问

```js
function Star(uname, age) {
    this.uname = uname;
    this.age = age;
    this.sing = function() {
        console.log('我会唱歌');

    }
}
var ldh = new Star('刘德华', 18);
ldh.sing();
// 内部定义的实例成员 不能使用Star.sing()构造函数来访问
Star.sex = '男';
// 静态成员只能通过构造函数来访问 不能通过对象来访问ldh.sex来访问
console.log(Star.sex);
```

## 构造函数原型 prototype

原因：构造函数方法很好用，但是存在浪费内存的问题。每一个对象的方法（相同作用）都占去一块内存。

构造函数通过原型分配的函数是所有对象所**共享的**。

JavaScript 规定，**每一个构造函数都有一个 prototype 属性**，指向另一个对象。注意这个 prototype 就是一个对象，这个对象的所有属性和方法，都会被构造函数所拥有。

**我们可以把那些不变的方法，直接定义在 prototype 对象上，这样所有对象的实例就可以共享这些方法。**

```js
function Star(uname, age) {
    this.uname = uname;
    this.age = age;
}
Star.prototype.sing = function() {
    console.log('我会唱歌');
}
var ldh = new Star('刘德华', 18);
var zxy = new Star('张学友', 19);
console.log(ldh.sing === zxy.sing);  // ｔｒｕｅ
ldh.sing();
zxy.sing();
```

## 对象原型 `__proto__`

对象都会有一个属性 `__proto__` **指向**构造函数的 prototype 原型对象.

方法查找规则：首先先看对象身上是否有对应方法，如果有就执行这个对象上的对应方法。如果没有对应方法，因为有`__proto__`的存在，就去构造函数原型对象prototype身上去查找对应方法。

```js
function Star(uname, age) {
    this.uname = uname;
    this.age = age;
}
Star.prototype.sing = function() {
    console.log('我会唱歌');
}
var ldh = new Star('刘德华', 18);
var zxy = new Star('张学友', 19);
ldh.sing();
console.log(ldh); // 对象身上系统自己添加一个 __proto__ 指向我们构造函数的原型对象 prototype
console.log(ldh.__proto__ === Star.prototype); // true
```

## constructor 构造函数

**一般情况下，对象的方法都在构造函数的原型对象中设置**。如果有多个对象的方法，我们可以给原型对象采取对象形式赋值，但是这样就会覆盖构造函数原型对象原来的内容，这样修改后的原型对象 constructor 就不再指向当前构造函数了。此时，我们可以在修改后的原型对象中，添加一个constructor 指向原来的构造函数。

```js
function Star(uname, age) {
    this.uname = uname;
    this.age = age;
}
Star.prototype = {
    constructor: Star,
    sing: function() {
        console.log('我会唱歌');
    },
    movie: function() {
        console.log('我会演电影');
    }
}
var ldh = new Star('刘德华', 18);
var zxy = new Star('张学友', 19);
console.log(Star.prototype);
console.log(ldh.__proto__);
console.log(Star.prototype.constructor);
console.log(ldh.__proto__.constructor);
```

- 如果使用`Star.prototype = {}`形式会覆盖构造函数原型对象原来的内容，但如果使用`Star.prototype.sing = function(){}`就会在构造函数原型对象原来的内容上增加这个方法。

## 原型链

![image-20210411133303266](C:\Users\12418\AppData\Roaming\Typora\typora-user-images\image-20210411133303266.png)

## js的成员查找机制

①当访问一个对象的属性（包括方法）时，首先查找这个对象自身有没有该属性。

②如果没有就查找它的原型（也就是 __proto__指向的 prototype 原型对象）。

③如果还没有就查找原型对象的原型（Object的原型对象）。

④依此类推一直找到 Object 为止（null）。

⑤__proto__对象原型的意义就在于为对象成员查找机制提供一个方向，或者说一条路线。

## 原型对象this指向

构造函数中的this 指向我们实例对象.原型对象里面放的是方法, 这个方法里面的this 指向的是 这个方法的**调用者**, 也就是这个**实例对象**.

## 扩展内置对象

可以通过原型对象，对原来的内置对象进行扩展自定义的方法。比如给数组增加自定义求偶数和的功能。

```js
Array.prototype.sum = function() {
    var sum = 0;
    for (var i = 0; i < this.length; i++) {
        sum += this[i];
    }
    return sum;
};
var arr = [1, 2, 3];
console.log(arr.sum());
```

- 注意：数组和字符串内置对象不能给原型对象覆盖操作 Array.prototype = {} ，只能是 Array.prototype.xxx = function(){} 的方式。

## 继承

ES6之前并没有给我们提供 extends 继承。我们可以通过**构造函数+原型对象**模拟实现继承，被称为**组合继承。**

### call()

调用这个函数, 并且修改函数运行时的 this 指向  

```js
fun.call(thisArg, arg1, arg2, ...) 
```

- thisArg ：当前调用函数 this 的指向对象

- arg1，arg2：传递的其他参数

### 借用构造函数继承父类型属性

核心原理： 通过 call() 把父类型的 this 指向子类型的 this ，这样就可以实现子类型继承父类型的属性。  

```js
// 父类
function Person(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
}
// 子类
function Student(name, age, sex, score) {
    Person.call(this, name, age, sex);  // 此时父类的 this 指向子类的 this，同时调用这个函数
    this.score = score;
}
var s1 = new Student('zs', 18, '男', 100);
console.dir(s1); 
```

### 借用原型对象继承父类型方法

一般情况下，对象的方法都在构造函数的原型对象中设置，通过构造函数无法继承父类方法。 

 核心原理： 

①将子类所共享的方法提取出来，让子类的 prototype 原型对象 = new 父类() 

②本质：子类原型对象等于是实例化父类，因为父类实例化之后另外开辟空间，就不会影响原来父类原型对象

③将子类的 constructor 从新指向子类的构造函数

```js
function Father(uname, age) {
    this.uname = uname;
    this.age = age;
}
Father.prototype.money = function() {
    console.log(100000);
};
function Son(uname, age, score) {
    Father.call(this, uname, age);
    this.score = score;
}
// Son.prototype = Father.prototype;  这样直接赋值会有问题,如果修改了子原型对象,父原型对象也会跟着一起变化
Son.prototype = new Father();
// 如果利用对象的形式修改了原型对象,别忘了利用constructor 指回原来的构造函数
Son.prototype.constructor = Son;
// 这个是子构造函数专门的方法
Son.prototype.exam = function() {
    console.log('孩子要考试');

}
var son = new Son('刘德华', 18, 100);
console.log(son);
console.log(Father.prototype);
console.log(Son.prototype.constructor);
```

## 类的本质

-  class本质还是function.

- 类的所有方法都定义在类的prototype属性上

- 类创建的实例,里面也有__proto__ 指向类的prototype原型对象

- 所以ES6的类它的绝大部分功能，ES5都可以做到，新的class写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。

- 所以ES6的类其实就是语法糖.语法糖:语法糖就是一种便捷写法.  简单理解, 有两种方法可以实现同样的功能, 但是一种写法更加清晰、方便,那么这个方法就是语法糖

# ES5 中新增的方法

ES5 中给我们新增了一些方法，可以很方便的操作数组或者字符串，这些方法主要包括：数组方法、字符串方法、对象方法。

## 数组方法

迭代(遍历)方法：forEach()、map()、filter()、some()、every()；

```js
// currentValue：数组当前项的值 index：数组当前项的索引 arr：数组对象本身
array.forEach(function(currentValue, index, arr))
array.filter(function(currentValue, index, arr))
array.some(function(currentValue, index, arr))
```

```js
var arr = [1, 2, 3];
var sum = 0;
arr.forEach(function(value, index, array) {
    sum += value;
})
var newarr = arr.filter(function(value,index,array){
    return value >= 2;
})
var flag = arr.some(function(value,index,array){
    return value >=2;
})
console.log(sum); // 6
console.log(newarr); // [2,3]
console.log(flag); // true
```

- filter() 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素,主要用于筛选数组,注意它直接**返回一个新数组**。

- some() 方法用于检测数组中的元素是否满足指定条件.  通俗点 查找数组中是否有满足条件的元素 。注意**它返回值是布尔值**, 如果查找到这个元素, 就返回true ,  如果查找不到就返回false。如果找到第一个满足条件的元素,则终止循环. 不在继续查找.**适用于查找唯一元素**

## 字符串方法

trim() 方法会从一个字符串的两端删除空白字符。

```js
var str = ' hello , js! ';
console.log(str);  // ' hello , js! '
str = str.trim()
console.log(str);	// 'hello , js!'
```

- trim() 方法并不影响原字符串本身，它返回的是一个新的字符串。

## 对象方法

### Object.keys() 用于获取对象自身所有的属性

```js
var obj = {
    id: 1,
    pname: '小米',
    price: 1999,
    num: 2000
};
var arr = Object.keys(obj);
console.log(arr); 	// array(4);
arr.forEach(function(value) {
    console.log(value);	// id pname price num
})
```

- 效果类似 for…in

- 返回一个由属性名组成的数组

### Object.defineProperty() 定义对象中新属性或修改原有的属性。(了解)

```js
// obj：必需。目标对象 prop：必需。需定义或修改的属性的名字 descriptor：必需。目标属性所拥有的特性
Object.defineProperty(obj, prop, descriptor{})
```

- value: 设置属性的值 默认为undefined

- writable: 值是否可以重写。true | false 默认为false

- enumerable: 目标属性是否可以被枚举。true | false 默认为 false

- configurable: 目标属性是否可以被删除或是否可以再次修改特性 true | false 默认为false

```js
var obj = {
    id: 1,
    pname: '小米',
    price: 1999
};
// 1. 以前的对象添加和修改属性的方式
// obj.num = 1000;
// obj.price = 99;
// console.log(obj);
// 2. Object.defineProperty() 定义新属性或修改原有的属性
Object.defineProperty(obj, 'address', {
    value: '中国山东蓝翔技校xx单元',
    writable: false,
    enumerable: false,
    configurable: false
});
```

# 函数进阶

## 函数的定义和调用

### 函数的定义方式

1. 函数声明方式 function 关键字 (命名函数)

2. 函数表达式 (匿名函数)

3. new Function()  

```js
var fn = new Function('参数1','参数2'..., '函数体')
```

- Function 里面参数都必须是字符串格式
- 第三种方式执行效率低，也不方便书写，因此较少使用
- 所有函数都是 Function 的实例(对象) 
- 函数也属于对象

### 函数的调用方式

```js
// 1. 普通函数
function fn() {
    console.log('人生的巅峰');

}
fn();   fn.call()
// 2. 对象的方法
var o = {
    sayHi: function() {
        console.log('人生的巅峰');

    }
}
o.sayHi();
// 3. 构造函数
function Star() {};
new Star();
// 4. 绑定事件函数
btn.onclick = function() {};   // 点击了按钮就可以调用这个函数
// 5. 定时器函数
setInterval(function() {}, 1000);  // 这个函数是定时器自动1秒钟调用一次
// 6. 立即执行函数
(function() {
    console.log('人生的巅峰');
})();
```

## 函数内的this指向

这些 this 的指向，是当我们调用函数的时候确定的。 调用方式的不同决定了this 的指向不同，一般指向我们的调用者.

| 调用方式     | this指向                                  |
| ------------ | ----------------------------------------- |
| 普通函数调用 | window                                    |
| 构造函数调用 | 实例对象 原型对象里面的方法也指向实例对象 |
| 对象方法调用 | 该方法所属对象                            |
| 事件绑定方法 | 绑定事件对象                              |
| 定时器函数   | window                                    |
| 立即执行函数 | window                                    |

## 改变函数内部的this指向

JavaScript 为我们专门提供了一些函数方法来帮我们更优雅的处理函数内部 this 的指向问题，常用的有 bind()、call()、apply() 三种方法。

### call()

call() 方法调用一个对象。简单理解为调用函数的方式，但是它可以改变函数的 this 指向。

```js
fun.call(thisArg, arg1, arg2, ...) 
```

- thisArg：在 fun 函数运行时指定的 this 值

- arg1，arg2：传递的其他参数

- 返回值就是函数的返回值，因为它就是调用函数

- 因此当我们想改变 this 指向，同时想调用这个函数的时候，可以使用 call，比如继承

### apply()

apply() 方法**调用一个函数**。简单理解为调用函数的方式，但是它可以改变函数的 this 指向。

```js
fun.apply(thisArg, [argsArray])
```

- thisArg：在fun函数运行时指定的 this 值

- argsArray：传递的值，必须包含在数组里面

- 返回值就是函数的返回值，因为它就是**调用函数**

- 因此 apply 主要跟数组有关系，比如使用 Math.max() 求数组的最大值

### bind()

bind() 方法**不会调用函数**。但是能改变函数内部this 指向 

```js
fun.bind(thisArg, arg1, arg2, ...) 
```

- thisArg：在 fun 函数运行时指定的 this 值

- arg1，arg2：传递的其他参数

- 返回由指定的 this 值和初始化参数改造的**原函数拷贝**

- 因此当我们只是想改变 this 指向，并且不想调用这个函数的时候，可以使用 bind

**总结**

1.call 经常做继承. 

2.apply 经常跟数组有关系. 比如借助于数学对象实现数组最大值最小值

3.bind 不调用函数,但是还想改变this指向. 比如改变定时器内部的this指向. 

## 严格模式

严格模式对正常的 JavaScript 语义做了一些更改： 

1.消除了 Javascript 语法的一些不合理、不严谨之处，减少了一些怪异行为。

2.消除代码运行的一些不安全之处，保证代码运行的安全。

3.提高编译器效率，增加运行速度。

4.禁用了在 ECMAScript 的未来版本中可能会定义的一些语法，为未来新版本的 Javascript 做好铺垫。比如一些保留字如：class, enum, export, extends, import, super 不能做变量名

### 开启严格模式

严格模式可以应用到**整个脚本**或**个别函数**中。

#### 为脚本开启严格模式

1 为整个脚本文件开启严格模式，需要在所有语句之前放一个特定语句“use strict”;（或‘use strict’;）。

2 有的 script 基本是严格模式，有的 script 脚本是正常模式，这样不利于文件合并，所以可以将整个脚本文件放在一个立即执行的匿名函数之中。这样独立创建一个作用域而不影响其他 script 脚本文件。

```js
// 1  
"use strict";
console.log("这是严格模式。");
// 2
(function(){
    "use strict";
    var num = 10;
    function fn() {}
})();
```

- 因为"use strict"加了引号，所以老版本的浏览器会把它当作一行普通字符串而忽略。

#### 为函数开启严格模式

要给某个函数开启严格模式，需要把“use strict”; (或 'use strict'; ) 声明放在函数体所有语句之前。

```js
function fn(){
　　"use strict";
　　return "这是严格模式。";
}
```

### 严格模式中的变化

#### 变量规定

①在正常模式中，如果一个变量没有声明就赋值，默认是全局变量。严格模式禁止这种用法，变量都必须先用var 命令声明，然后再使用。

②严禁删除已经声明变量。例如，delete x; 语法是错误的。

#### 严格模式下this指向问题

①以前在全局作用域函数中的 this 指向 window 对象。

②严格模式下全局作用域中函数中的 this 是 undefined。

③以前构造函数时不加 new也可以 调用,当普通函数，this 指向全局对象

④严格模式下,如果 构造函数不加new调用, this 指向的是undefined 如果给他赋值则 会报错

⑤new 实例化的构造函数指向创建的对象实例。

⑥定时器 this 还是指向 window 。

⑦事件、对象还是指向调用者。

#### 函数变化

①函数不能有重名的参数。

②函数必须声明在顶层.新版本的 JavaScript 会引入“块级作用域”（ ES6 中已引入）。为了与新版本接轨，不允许在非函数的代码块内声明函数。 



## 高阶函数

**高阶函数**是对其他函数进行操作的函数，它接收函数作为参数或将函数作为返回值输出。

```js
// 函数作为参数
function fn(callback){
  callback&&callback();
}
fn(function(){alert('hi')})
// 函数作为返回值
function fn(){
    return function() {}
}
fn();
```

## 闭包

**闭包（closure）**指有权访问另一个函数作用域中变量的**函数**。

简单理解就是 ，一个作用域可以访问另外一个函数内部的局部变量。 

```js
// 不经意间的闭包
function fn1(){    // fn1 就是闭包函数
　　　　var num = 10;
　　　　function fn2(){
　　　　　　console.log(num); // 10
　　　　}
       fn2();
　}
  fn1();
```

```js
// 如何在函数外面访问函数内的局部变量
// 利用高阶函数中的返回函数方法
function fn() {　　　　
    var num = 10;　　　　
    return function {　　　　　　
         console.log(num); // 10         　　　　
     }
  }
  var f = fn();
  f();
```

- 闭包作用：延伸变量的作用范围。

### 变量作用域

变量根据作用域的不同分为两种：全局变量和局部变量。

1. 函数内部可以使用全局变量。

2. **函数外部不可以使用局部变量。**

3. 当函数执行完毕，本作用域内的局部变量会销毁。

### 调试闭包

1. 打开浏览器，按 F12 键启动 chrome 调试工具。

2. 设置断点。

3. 找到 Scope 选项（Scope 作用域的意思）。

4. 当我们重新刷新页面，会进入断点调试，Scope 里面会有两个参数（global 全局作用域、local 局部作用域）。

5. 当执行到 fn2() 时，Scope 里面会多一个 Closure 参数 ，这就表明产生了闭包。

### 案例

```js
 // 为每一个小li设置事件
for (var i = 0; i < lis.length; i++) {
    (function(i) {
        lis[i].onclick = function() {
            console.log(i);
        }
    })(i);
}
```

## 递归

如果**一个函数在内部可以调用其本身**，那么这个函数就是递归函数。

简单理解:函数内部自己调用自己, 这个函数就是递归函数

递归函数的作用和循环效果一样

由于递归很容易发生“栈溢出”错误（stack overflow），所以**必须要加退出条件 return。**

```js
var datas = [{
    id: 1,
    name: '家电',
    goods: [
        {
            id: 11,
            name: '电视'
    	},
        {
            id: 12,
            name: '冰箱'
          }
    ]}, 
    {
    id: 2,
    name: '手机'
}]
function getId(json,id){
    var o = {};
    json.forEach(function(item){
        if(item.id == id){
            o = item;
        }else if(item.goods && item.goods.length > 0){
            o = getId(item.goods,id);
        }
    });
    return o;
}
console.log(getId(datas,11));
```

## 浅拷贝和深拷贝

1.浅拷贝只是拷贝一层, 更深层次对象级别的只拷贝引用.

2.深拷贝拷贝多层, 每一级别的数据都会拷贝.

Object.assign(*target*, ...*sources*)  es6 新增方法可以浅拷贝

### 浅拷贝

浅拷贝的深层是将被拷贝对象的第一层地址拷贝，所以修改拷贝后的对象，被拷贝对象也会被修改。

```js
var obj = {
    id: 1,
    name: 'andy',
    msg: {
        age: 18
    }
};
var o = {};
for (var k in obj) {
    o[k] = obj[k];
}
o.msg.age = 20;
console.log(o);		// age : 20;
console.log(obj);  // age : 20;
// es6 的新增方法
Object.assign(o,obj);
```

### 深拷贝

深拷贝深层是将被拷贝对象重新开辟一个内存空间存储，然后赋值给新对象。此时修改拷贝对象，原对象不会有变化。

```js
var obj = {
    id: 1,
    name: 'andy',
    msg: {
        age: 18
    },
    color: ['pink', 'blue']
};
var o = {};
function deepcopy(newobj, oldobj) {
    for (var k in oldobj) {
        var item = oldobj[k];
        if (item instanceof Array) {
            newobj[k] = [];
            deepcopy(newobj[k], item);
        } else if (item instanceof Object) {
            newobj[k] = {};
            deepcopy(newobj[k], item);
        } else {
            newobj[k] = item;
        }
    }
}
deepcopy(o, obj)
console.log(o);
o.msg.age = 20;
console.log(obj);
```

- **这里先判断数组是因为数组也是对象的一种，如果向判断对象，数组也被判定为对象。**

# 正则表达式

**正则表达式（** Regular Expression **）**是用于匹配字符串中字符组合的模式。在 JavaScript中，正则表达式也是对象。多用于**匹配、替换、提取**。

## 创建正则表达式

1 通过调用RegExp对象的构造函数创建

```js
// 1 通过调用RegExp对象的构造函数创建
var 变量名 = new RegExp(/表达式/);
// 2 通过字面量创建
var 变量名 = /表达式/;
```

## 测试正则表达式 test

test() 正则对象方法，用于检测字符串是否符合该规则，该对象会返回 true 或 false，其参数是测试字符串。

```js
// 1.regexObj 是写的正则表达式
// 2.str 我们要测试的文本
regexObj.test(str) 
```

```js
var reg = /abc/;
console.log(reg.test('abc'));  // true 
console.log(reg.test(123));  // false
```

## 正则表达式的组成

一个正则表达式可以由**简单的字符构成**，比如 /abc/，也可以是简单和特殊字符的组合，比如 /ab*c/ 。其中特殊字符也被称为元字符，在正则表达式中是具有特殊意义的专用符号，如 ^ 、$ 、+ 等。

### 边界符

正则表达式中的边界符（位置符）用来**提示字符所处的位置**，主要有两个字符。

| 边界符 | 说明               |
| ------ | ------------------ |
| ^      | 表示匹配行首的文本 |
| $      | 表示匹配行尾的文本 |

- 如果 ^ 和 $ 在一起，表示必须是精确匹配。

### 字符类

字符类表示有一系列字符可供选择，只要**匹配其中一个**就可以了。**所有可供选择的字符都放在方括号内。**

```js
// 1. []  方括号   
   /[abc]/.test('andy')     // true 
// 后面的字符串只要包含方括号内中任意一个字符，都返回 true
// 2. [-]  方括号内部 范围符-   
   /^[a-z]$/.test(c')     // true
// 方括号内部加上 - 表示范围，这里表示 a 到 z 26个英文字母都可以。
// 3. [^]  方括号内部 取反符^   
   /[^abc]/.test('andy')     // false
// 方括号内部加上 ^ 表示取反，只要包含方括号内的字符，都返回 false
// 4. 字符组合
   /[a-z1-9]/.test('andy')     // true
// 方括号内部可以使用字符组合，这里表示包含 a 到 z 的26个英文字母和 1 到 9 的数字都可以。
// 5. 确定优先级
	/[(abc)*{3}]/
// 优先级使abc先成为一个整体
```

### 量词符

量词符用来设定**某个模式出现的次数**。

| 量词  | 说明            |
| ----- | --------------- |
| *     | 重复0次或更多次 |
| +     | 重复1次或更多次 |
| ？    | 重复0次或1次    |
| {n}   | 重复n次         |
| {n,}  | 重复n次或更多次 |
| {n,m} | 重复n次到m次    |

### 预定义类

预定义类指的是**某些常见模式的简写方式。**

| 预定类 | 说明                 |
| ------ | -------------------- |
| \d     | [0-9]                |
| \D     | [^0-9]               |
| \w     | [A-Za-z0-9_]         |
| \W     | [^A-Za-z0-9_]        |
| \s     | 匹配空格[\t\r\n\v\f] |
| \S     | [^\t\r\n\v\f]        |

## 正则表达式中的替换

replace() 方法可以实现替换字符串操作，用来替换的参数可以是一个字符串或是一个正则表达式。

```js
// replace() 方法可以实现替换字符串操作，用来替换的参数可以是一个字符串或是一个正则表达式。
   stringObject.replace(regexp/substr,replacement)
// 第一个参数:   被替换的字符串 或者  正则表达式
// 第二个参数:   替换为的字符串
// 返回值是一个替换完毕的新字符串
```

  ## 正则表达式参数

```js
   /表达式/[switch]
// switch(也称为修饰符) 按照什么样的模式来匹配. 有三种值：
// g：全局匹配 
// i：忽略大小写 
// gi：全局匹配 + 忽略大小写
```

**案例:**

```js
// 替换 replace
 var str = 'andy和red';
 // var newStr = str.replace('andy', 'baby'); // 之前用法
 var newStr = str.replace(/andy/, 'baby');
 console.log(newStr);
// 参数案例
var text = document.querySelector('textarea');
var btn = document.querySelector('button');
var div = document.querySelector('div');
btn.onclick = function() {
    div.innerHTML = text.value.replace(/激情|gay/g, '**');
}
```

# ES6

## 声明函数

不用function 声明了

```js
sayhi(){
    //
}
```

## let

ES6中新增的用于声明变量的关键字。

- let声明的变量只在所处于的块级有效

```js
 if (true) { 
     let a = 10;
 }
console.log(a) // a is not defined
```

- 不存在变量提升

```js
 console.log(a); // a is not defined 
 let a = 20;
```

- 暂时性死区

```js
 var tmp = 123;
 if (true) { 
     tmp = 'abc';
     let tmp; 
 } 
```

**经典面试题**

```js
 var arr = [];
 for (var i = 0; i < 2; i++) {
     arr[i] = function () {
         console.log(i); 
     }
 }
 arr[0]();
 arr[1]();
```

- 此题的关键点在于变量i是全局的，函数执行时输出的都是全局作用域下的i值。

```js
 let arr = [];
 for (let i = 0; i < 2; i++) {
     arr[i] = function () {
         console.log(i); 
     }
 }
 arr[0]();
 arr[1]();
```

- 此题的关键点在于每次循环都会产生一个块级作用域，每个块级作用域中的变量都是不同的，函数执行时输出的是自己上一级（循环产生的块级作用域）作用域下的i值.

## const

作用：声明常量，常量就是值（内存地址）不能变化的量。

- 具有块级作用域

```js
 if (true) { 
     const a = 10;
 }
console.log(a) // a is not defined
```

- 声明常量时必须赋值

```js
const PI; // Missing initializer in const declaration
```

- 常量赋值后，值不能修改。 但是单独修改数组中值却是可以。

```js
 const PI = 3.14;
 PI = 100; // Assignment to constant variable. 
// 单独修改数组值
 const ary = [100, 200];
 ary[0] = 'a';
 ary[1] = 'b';
 console.log(ary); // ['a', 'b']; 
 ary = ['a', 'b']; // Assignment to constant variable.
```

## 解构赋值

ES6中允许从数组中提取值，按照对应位置，对变量赋值。对象也可以实现解构。

### 数组解构

```js
 let [a, b, c] = [1, 2, 3];
 console.log(a)
 console.log(b)
 console.log(c) 
// 如果解构不成功，变量的值为undefined
```

### 对象解构

```js
 let person = { name: 'zhangsan', age: 20 }; 
 let { name, age } = person;
 console.log(name); // 'zhangsan' 
 console.log(age); // 20
// 对象解构可以赋值给其他变量
 let {name: myName, age: myAge} = person; // myName myAge 属于别名
 console.log(myName); // 'zhangsan' 
 console.log(myAge); // 20
```

## 箭头函数

```js
() => {} 
const fn = () => {}
```

- 函数体中只有一句代码，且代码的执行结果就是返回值，可以省略大括号

```js
 function sum(num1, num2) { 
     return num1 + num2; 
 }
 const sum = (num1, num2) => num1 + num2; 
```

- 如果形参只有一个，可以省略小括号

```js
 function fn (v) {
     return v;
 } 
 const fn = v => v;
```

- 箭头函数不绑定this关键字，箭头函数中的this，指向的是函数定义位置的上下文this。

```js
 const obj = { name: '张三'} 
 function fn () { 
     console.log(this);
     return () => { 
         console.log(this)
     } 
 } 
 const resFn = fn.call(obj); 
 resFn();  // 值得式fn里面的this =>obj
```

## 剩余参数

剩余参数语法允许我们将一个不定数量的参数表示为一个数组。

```js
 function sum (first, ...args) {
     console.log(first); // 10
     console.log(args); // [20, 30] 
 }
 sum(10, 20, 30)
```

## Array的扩展方法

### 扩展运算符

- 扩展运算符可以将数组或者对象转为用逗号分隔的参数序列。

```js
 let ary = [1, 2, 3];
 ...ary  // 1, 2, 3
 console.log(...ary);    // 1 2 3
 console.log(1, 2, 3)
```

- 扩展运算符可以应用于合并数组。

```js
// 方法一 
 let ary1 = [1, 2, 3];
 let ary2 = [3, 4, 5];
 let ary3 = [...ary1, ...ary2];
 // 方法二 
 ary1.push(...ary2);
```

- 将类数组或可遍历对象(伪数组)转换为真正的数组

```js
let oDivs = document.getElementsByTagName('div'); 
oDivs = [...oDivs];
```

### Array.from()

将类数组或可遍历对象转换为真正的数组

```js
let arrayLike = {
    '0': 'a',
    '1': 'b',
    '2': 'c',
    length: 3
}; 
let arr2 = Array.from(arrayLike); // ['a', 'b', 'c']
```

- 方法还可以接受第二个参数，作用类似于数组的map方法，用来对每个元素进行处理，将处理后的值放入返回的数组。

```js
 let arrayLike = { 
     "0": 1,
     "1": 2,
     "length": 2
 }
 let newAry = Array.from(aryLike, item => item *2)
```

### find()

用于找出第一个符合条件的数组成员，如果没有找到返回undefined

```js
 let ary = [{
     id: 1,
     name: '张三‘
 }, { 
     id: 2,
     name: '李四‘
 }]; 
 let target = ary.find((item, index) => item.id == 2);
```

### findIndex()

用于找出第一个符合条件的数组成员的位置，如果没有找到返回-1

```js
let ary = [1, 5, 10, 15];
let index = ary.findIndex((value, index) => value > 9); 
console.log(index); // 2
```

### includes()

表示某个数组是否包含给定的值，返回布尔值。

```js
[1, 2, 3].includes(2) // true 
[1, 2, 3].includes(4) // false
```

## String的扩展方法

### 模板字符串

ES6新增的创建字符串的方式，使用反引号定义。

```js
 let name = `zhangsan`;
```

- 模板字符串中可以解析变量。

```js
 let name = '张三'; 
 let sayHello = `hello,my name is ${name}`; // hello, my name is zhangsan
```

- 模板字符串中可以换行

```js
 let result = { 
     name: 'zhangsan', 
     age: 20, 
     sex: '男' 
 } 
 let html = ` <div>
     <span>${result.name}</span>
     <span>${result.age}</span>
     <span>${result.sex}</span>
 </div> `;
```

- 在模板字符串中可以调用函数。

```js
 const sayHello = function () { 
    return '哈哈哈哈 追不到我吧 我就是这么强大';
 }; 
 let greet = `${sayHello()} 哈哈哈哈`;
 console.log(greet); // 哈哈哈哈 追不到我吧 我就是这么强大 哈哈哈哈
```

### startsWith() 和 endsWith()

- startsWith()：表示参数字符串是否在原字符串的头部，返回布尔值

- endsWith()：表示参数字符串是否在原字符串的尾部，返回布尔值

```js
 let str = 'Hello world!';
 str.startsWith('Hello') // true 
 str.endsWith('!')       // true
```

### repeat()

repeat方法表示将原字符串重复n次，返回一个新字符串。

```js
'x'.repeat(3)      // "xxx" 
'hello'.repeat(2)  // "hellohello"
```
### prototype.padStart和prototype.padEnd
都能补全字符串，前者表示前面填充，后者表示后面填充
```
String.prototype.padStart(maxLength, fillString='填充的字符') 或
String.prototype.padEnd(maxLength, fillString=' 填充的字符')
```

## Set数据结构

ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。

```js
// Set本身是一个构造函数，用来生成  Set  数据结构。
const s = new Set();
// Set函数可以接受一个数组作为参数，用来初始化。
const set = new Set([1, 2, 3, 4, 4]);
```

### 实例方法

- add(value)：添加某个值，返回 Set 结构本身
- delete(value)：删除某个值，返回一个布尔值，表示删除是否成功
- has(value)：返回一个布尔值，表示该值是否为 Set 的成员
- clear()：清除所有成员，没有返回值

```js
 const s = new Set();
 s.add(1).add(2).add(3); // 向 set 结构中添加值 
 s.delete(2)             // 删除 set 结构中的2值 
 s.has(1)                // 表示 set 结构中是否有1这个值 返回布尔值 
 s.clear()               // 清除 set 结构中的所有值
```

### 遍历

Set 结构的实例与数组一样，也拥有forEach方法，用于对每个成员执行某种操作，没有返回值。

```js
s.forEach(value => console.log(value))
```

# JSON

由于js对象只有js自己认识，其他语言不认识。JSON就是一个特殊格式的字符串，这个字符串可以被任意语言所识别，并且可以转换成任意语言中的对象，JSON在开发中主要用来数据的交互。

- JSON - JavaScript Object Notation JS对象表示法

- JSON和JS对象的格式一样，只不过JSON字符串中的**属性名必须加双引号**，其他和JS语法一致。
- JSON分类：对象{}数组[]

```js
// js的对象
var obj = {"id":1,"name":"xiaowang"};
// 转成json对象
var newobj = '{"id":1,"name":"xiaowang"}';
// var arr = '[1,2,true,"hello"]';
```

- JSON中允许的值：**字符串，数值，布尔值，NULL，对象，数组**。

## JSON工具

将JSON字符串转换成JS中的对象，也可以将JS对象转成JSON字符串。

### JSON.parse()

将JSON字符串转换成JS中的对象。

```js
var json = '{"name":"xiaowang","age":18}';
var o = JSON.parse(json);
console.log(o);
console.log(o.name);
```

- 需要将JSON字符串作为参数，返回一个对象。

### JSON.stringify()

将JS对象转成JSON字符串.

```js
var json = { name: "xiaowang", "age": 18 };
var o = JSON.stringify(json);
console.log(o);
```

- 需要将JS对象作为参数，返回一个JSON对象。

## eval()

执行一段字符串形式的JS代码，并将执行结果返回。

```js
var str = "alert('hello')";
console.log(str);
```

- 性能低
- 具有安全隐患
- 可以用来解决ie低版本兼容性问题，但不建议用，真要兼容可以使用外部js（切字符串达到JSON工具效果）引入。

