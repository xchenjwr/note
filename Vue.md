 #  Vue.js


## MVC和MVVM区别


Node（后端）中的 MVC 与 前端中的 MVVM 之间的区别

 + MVC 是后端的分层开发概念；
 + MVVM是前端视图层的概念，主要关注于 视图层分离，也就是说：MVVM把前端的视图层，分	为了 三部分 Model, View , VM ViewModel
 + 为什么有了MVC还要有MVVM

## vue中的MVVM关系

Vue.js 基本代码 和 MVVM 之间的对应关系

```html
<!-- 将来 new 的Vue实例，会控制这个 元素中的所有内容 -->
<!-- Vue 实例所控制的这个元素区域，就是我们的 V  -->
<div id="app">
    <p>{{ msg }}</p>
</div>
<script>
// 2. 创建一个Vue的实例
// 当我们导入包之后，在浏览器的内存中，就多了一个 Vue 构造函数
//  注意：我们 new 出来的这个 vm 对象，就是我们 MVVM中的 VM调度者
    var vm = new Vue({
      el: '#app',  // 表示，当前我们 new 的这个 Vue 实例，要控制页面上的哪个区域
      // 这里的 data 就是 MVVM中的 M，专门用来保存 每个页面的数据的
      data: { // data 属性中，存放的是 el 中要用到的数据
        msg: '欢迎学习Vue' // 通过 Vue 提供的指令，很方便的就能把数据渲染到页面上，程序员不再手动操作DOM元素了【前端的Vue之类的框架，不提倡我们去手动操作DOM元素了】
      }
})
```

## 指令

### v-cloak
解决插值表达式闪烁的问题

### v-text
会覆盖元素中原本的内容

### v-html
可以插入html语句

### v-bind:  或者 :
要绑定的属性（只能实现M到V的单向数据绑定）
- 在绑定的时候，可以字符串拼接绑定内容
- 可以写合法的JS表达式

### v-on:  或者 @
事件绑定机制

```html
<style>
	[v-cloak] {
		display: none;
	}
</style>
<div id="app">
    <p v-cloak>{{ msg }}</p>
    <h4 v-text="msg"></h4>
    <div v-html="msg2"></div>
    <input type="button" value="按钮" v-bind:title="mytitle" v-on:click="show">
    <!--
    <input type="button" value="按钮" :title="mytitle + '我是多余的'" @click="show">
    -->
</div>
<script>
    var vm = new Vue({
      el: '#app',
      data: {
        msg: '123',
        msg2: '<h1>哈哈，我是一个大大的H1， 我大，我骄傲</h1>',
        mytitle: '这是一个自己定义的title'
      },
      methods: { 
        show() {
          alert('Hello')
        }
      }
    })
</script>
```

## 方法

vue中的方法要在vue构造函数下的methods{}对象中。里面的函数可以使用se6中方法定义。

```js
var vm = new Vue(){
	el: "#app"
	data: {
		
	}
	methods: {
		sayhi(){
		
		}
	}
}
```

## 数据访问

在vm实例中，如果想要获取data上的数据，或者想要调用methods中的方法，必须通过this.属性名，this.方法进行访问，这里的this，就表示我们new出来的 vm实例对象。(类似对象）
- vm实例会监听自身data的变化，只要数据一发生改变，就会自动化新数据同步到页面中去。【程序员只需要考虑逻辑变化，不需要考虑重新渲染】 

## 事件修饰符

+ .stop       阻止冒泡

+ .prevent    阻止默认事件

+ .capture    添加事件侦听器时使用事件捕获模式

+ .self       只当事件在该元素本身（比如不是子元素）触发时触发回调

+ .once       事件只触发一次

```html
<div id="app">
<!--必须添加给外层，当内层被触发同时触发外层时，本来执行的时冒泡模式改成捕获模式。-->
<div class="div1" @click.capture="f1">
	<!--stop阻止冒泡到div块-->
    <input type="button" value="点我" @click.stop="f2">
</div>
<!--阻止默认的链接跳转，并且只阻止一次-->
 <a href="http://www.baidu.com" @click.prevent.once="ddiv()">有问题，先去百度</a>
 <!-- .self 只会阻止自己身上冒泡行为的触发，并不会真正阻止 冒泡的行为 -->
 <div class="div1" @click.selp="f1">
    <input type="button" value="点我" @click="f2">
</div>
 </div>
```

## 双向数据绑定`v-model`

使用  v-model 指令，可以实现 表单元素和 Model 中数据的双向数据绑定，但只能运用在表单元素中。 

```html
<div id="app">
    <input type="text" v-model="msg">
</div>

<script src="vue-2.4.0.js"></script>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            msg: ""
        } 
    })
</script>
```

## [在Vue中使用样式](https://cn.vuejs.org/v2/guide/class-and-style.html)

### 使用class样式

1. 数组
```html
<h1 :class="['red', 'thin']">这是一个邪恶的H1</h1>
```

2. 数组中使用三元表达式
```html
<h1 :class="['red', 'thin', isactive?'active':'']">这是一个邪恶的H1</h1>
```

3. 数组中嵌套对象
```html
<h1 :class="['red', 'thin', {'active': flag}]">这是一个邪恶的H1</h1>
```

4. 直接使用对象
```html
<h1 :class="{red:true, italic:true, active:true, thin:true}">这是一个邪恶的H1</h1>
```

### 使用内联样式

1. 直接在元素上通过 `:style` 的形式，书写样式对象

```html
<h1 :style="{color: 'red', 'font-size': '40px'}">这是一个善良的H1</h1>
```

2. 将样式对象，定义到 `data` 中，并直接引用到 `:style` 中

 + 在data上定义样式：
```
data: {
        h1StyleObj: { color: 'red', 'font-size': '40px', 'font-weight': '200' }
}
```

 + 在元素中，通过属性绑定的形式，将样式对象应用到元素中：
```html
<h1 :style="h1StyleObj">这是一个善良的H1</h1>
```

3. 在 `:style` 中通过数组，引用多个 `data` 上的样式对象
 + 在data上定义样式：
```js
data: {
        h1StyleObj: { color: 'red', 'font-size': '40px', 'font-weight': '200' },
        h1StyleObj2: { fontStyle: 'italic' }
}
```

 + 在元素中，通过属性绑定的形式，将样式对象应用到元素中：
```html
<h1 :style="[h1StyleObj, h1StyleObj2]">这是一个善良的H1</h1>
```

## 循环`v-for`和`key`属性

1. 迭代数组

```html
// 遍历普通数组和对象数组
<ul>
  <li v-for="(item, i) in list">索引：{{i}} --- 姓名：{{item.name}} --- 年龄：{{item.age}}</li>
</ul>
```

2. 迭代对象中的属性

```html
<!-- 循环遍历对象身上的属性 -->

<div v-for="(val, key, i) in userInfo">{{val}} --- {{key}} --- {{i}}</div>
```

3. 迭代数字（从1开始）

```html
<p v-for="i in 10">这是第 {{i}} 个P标签</p>
```

> 2.2.0+ 的版本里，**当在组件中使用** v-for 时，key 现在是**必须的**。
```html
<p v-for="item in list" :key="item.id">{{item.name}}</p>
```
- 为了给 Vue 一个提示，**以便它能跟踪每个节点的身份，从而重用和重新排序现有元素**，你需要为每项提供一个唯一 key 属性。

## `v-if`和`v-show`

v-if每次都是重新删除或创建元素而v-show只是切换了元素的display样式。

```html
<input type="button" value="toggle" @click="flag=!flag" />
<h3 v-if="flag">v-if控制的</h3>
<h3 v-show="flag">v-show控制的</h3>
```

- 一般来说，v-if 有更高的切换消耗而 v-show 有更高的初始渲染消耗。因此，如果需要频繁切换 v-show 较好，如果在运行时条件不大可能改变 v-if 较好。

## 过滤器

概念：Vue.js 允许你自定义过滤器，**可被用作一些常见的文本格式化**。过滤器可以用在两个地方：**mustache 插值和 v-bind 表达式**。过滤器应该被添加在 JavaScript 表达式的尾部，由“管道”符指示；

### 全局过滤器

```js
// 定义一个全局过滤器
//Vue.filter('过滤器名称', function () {
	// 返回过滤内容
//})
Vue.filter('msgformat',function(msg,arg,arg2){
	return msg + arg + arg2;
})
```

### 私有过滤器

```js
var vm = new Vue(){
	el: "#app",
	datas: {},
	methods: {},
    filters: { // 私有局部过滤器，只能在 当前 VM 对象所控制的 View 区域进行使用
            dataFormat(参数1,参数2) {
                    // 返回过滤内
            } 
   }
}
```

**HTML元素应用**

```html
<p>{{item.ctime | dataFormat{'参数1','参数2'}}}</p>

```

> 注意：当有局部和全局两个名称相同的过滤器时候，会以就近原则进行调用，即：局部过滤器优先于全局过滤器被调用！

## 键盘修饰符

含有多种特殊案件的修饰符

```html
<input type="text" v-model="name" @keyup.enter="add">
```

## 自定义键盘修饰符

1. 通过`Vue.config.keyCodes.名称 = 按键值`来自定义案件修饰符的别名：

```js
Vue.config.keyCodes.f2 = 113;
```

2. 使用自定义的按键修饰符：

```html
<input type="text" v-model="name" @keyup.f2="add">
```

## 自定义指令

### 自定义全局指令

```js
    // 自定义全局指令 v-focus，为绑定的元素自动获取焦点：
    Vue.directive('focus', {
      inserted: function (el) { // inserted 表示被绑定元素插入父节点时调用
        el.focus();
      }
    });
```

### 自定义局部指令

```js
var vm = new Vue(){
	el: "#app",
	datas: {},
	methods: {},
    directives: { 
    'fontweight': { // 设置字体粗细的
          bind: function (el, binding) {
            el.style.fontWeight = binding.value
          }
        },
       'fontSize': function (el, binding) { // 注意：这个 function 等同于 把 代码写到了 bind 和 update 中去
          el.style.fontSize = parseInt(binding.value) + 'px'
   }
}

```

2. 自定义指令的使用方式：

```html

<input type="text" v-model="searchName" v-focus v-color="'red'" v-font-weight="900">

```
- 样式一般用bind钩子函数，行为一般用inserted钩子函数。

## [vue实例的生命周期](https://cn.vuejs.org/v2/guide/instance.html#%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E5%9B%BE%E7%A4%BA)

+ 什么是生命周期：从Vue实例创建、运行、到销毁期间，总是伴随着各种各样的事件，这些事件，统称为生命周期！
+ [生命周期钩子](https://cn.vuejs.org/v2/api/#选项-生命周期钩子)：就是生命周期事件的别名而已；
+ 生命周期钩子 = 生命周期函数 = 生命周期事件
+ 主要的生命周期函数分类：

  - 创建期间的生命周期函数：
    + beforeCreate：实例刚在内存中被创建出来，此时，还没有初始化好 data 和 methods 属性
    + created：实例已经在内存中创建OK，此时 data 和 methods 已经创建OK，此时还没有开始 编译模板
    + beforeMount：此时已经完成了模板的编译，但是还没有挂载到页面中
    + mounted：此时，已经将编译好的模板，挂载到了页面指定的容器中显示
  - 运行期间的生命周期函数：
    + beforeUpdate：状态更新之前执行此函数， 此时 data 中的状态值是最新的，但是界面上显示的 数据还是旧的，因为此时还没有开始重新渲染DOM节点
    + updated：实例更新完毕之后调用此函数，此时 data 中的状态值 和 界面上显示的数据，都已经完成了更新，界面已经被重新渲染好了！

  - 销毁期间的生命周期函数：
    + beforeDestroy：实例销毁之前调用。在这一步，实例仍然完全可用。
    + destroyed：Vue 实例销毁后调用。调用后，Vue 实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。

## [Vue.js Ajax(vue-resource)](https://www.runoob.com/vue2/vuejs-ajax.html)

```js
// 基于全局Vue对象使用http
Vue.http.get('/someUrl', [options]).then(successCallback, errorCallback);
Vue.http.post('/someUrl', [body], [options]).then(successCallback, errorCallback);

// 在一个Vue实例内使用$http
this.$http.get('/someUrl', [options]).then(successCallback, errorCallback);
this.$http.post('/someUrl', [body], [options]).then(successCallback, errorCallback);
```
- `get(url,[option])`
- `head(url,[option])`
- `delete(url,[option])`
- `jsonp(url,[option])`
- `post(url,[body],[option])`
-  `put(url,[body],[option])`
-  `patch(url,[body],[option])`

> 测试地址：http://jsonplaceholder.typicode.com/users



## [动画](https://cn.vuejs.org/v2/guide/transitions.html)

vue动画包含两个阶段，但如果只需要一个阶段要使用钩子函数。

## 组件

### 全局组件定义的三种方式

1. 使用 Vue.extend 配合 Vue.component 方法：

```
var login = Vue.extend({
      template: '<h1>登录</h1>'
    });
    Vue.component('login', login);
```

2. 直接使用 Vue.component 方法：

```
Vue.component('register', {
      template: '<h1>注册</h1>'
    });
```

3. 将模板字符串，定义到script标签中：

```
<script id="tmpl" type="x-template">
      <div><a href="#">登录</a> | <a href="#">注册</a></div>
    </script>
```

同时，需要使用 Vue.component 来定义组件：

```
Vue.component('account', {
      template: '#tmpl'
    });
```

> 注意： 组件中的DOM结构，有且只能有唯一的根元素（Root Element）来进行包裹！

### 组件中展示数据和响应事件

1. 在组件中，`data`需要被定义为一个方法，例如：

```
Vue.component('account', {
      template: '#tmpl',
      data() {
        return {
          msg: '大家好！'
        }
      },
      methods:{
        login(){
          alert('点击了登录按钮');
        }
      }
    });
```

2. 在子组件中，如果将模板字符串，定义到了script标签中，那么，要访问子组件身上的`data`属性中的值，需要使用`this`来访问；

### 使用`components`属性定义局部子组件

1. 组件实例定义方式：

```
<script>
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {},
      methods: {},
      components: { // 定义子组件
        account: { // account 组件
          template: '<div><h1>这是Account组件{{name}}</h1><login></login></div>', // 在这里使用定义的子组件
          components: { // 定义子组件的子组件
            login: { // login 组件
              template: "<h3>这是登录组件</h3>"
            }
          }
        }
      }
    });
  </script>
```

2. 引用组件：

```
<div id="app">
    <account></account>
  </div>
```

## 切换组件

1.使用`flag`标识符结合`v-if`和`v-else`

2.使用`component`标签，来引用组件，并通过`:is`属性来指定要加载的组件：

```
  <div id="app">
    <a href="#" @click.prevent="comName='login'">登录</a>
    <a href="#" @click.prevent="comName='register'">注册</a>
    <hr>
    <transition mode="out-in">
      <component :is="comName"></component>
    </transition>
  </div>
```

## 父组件向子组件传值

> 相当于向父组件插入了一个管子，吸取一个属性

1. 组件实例定义方式，注意：一定要使用`props`属性来定义父组件传递过来的数据

```
<script>
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {
        msg: '这是父组件中的消息'
      },
      components: {
        son: {
          template: '<h1>这是子组件 --- {{finfo}}</h1>',
          props: ['finfo']
        }
      }
    });
  </script>
```

2. 使用`v-bind`或简化指令，将数据传递到子组件中：

```
<div id="app">
    <son :finfo="msg"></son>
  </div>
```

- props传来的数据只读。

## 父组件向子组件传方法/子组件向父组件传值

​	1.使用事件绑定机制；自定义了 事件属性

```
<div id="app">
    <com2 @func="show"></com2>
</div>
```

​	2.this.$emit(方法名，方法参数)拿到子组件方法

```
// 定义了一个字面量类型的 组件模板对象
var com2 = {
	template: '#tmpl', 
	data() {
		return {
			sonmsg: { name: '小头儿子', age: 6 }
		}
    },
	methods: {
			myclick() {
				this.$emit('func', this.sonmsg)
			}
	}
}
```

3.通过调用父组件的show方法，传值给父组件

```
var vm = new Vue({
      el: '#app',
      data: {
        datamsgFormSon: null
      },
      methods: {
        show(data) {
          this.datamsgFormSon = data
        }
      },
      components: {
        com2
        // com2: com2
      }
});
```

## 使用 `this.$refs` 来获取元素和组件

```
  <div id="app">
    <div>
      <input type="button" value="获取元素内容" @click="getElement" />
      <!-- 使用 ref 获取元素 -->
      <h1 ref="myh1">这是一个大大的H1</h1>

      <hr>
      <!-- 使用 ref 获取子组件 -->
      <my-com ref="mycom"></my-com>
    </div>
  </div>

  <script>
    Vue.component('my-com', {
      template: '<h5>这是一个子组件</h5>',
      data() {
        return {
          name: '子组件'
        }
      }
    });

    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {},
      methods: {
        getElement() {
          // 通过 this.$refs 来获取元素
          console.log(this.$refs.myh1.innerText);
          // 通过 this.$refs 来获取组件
          console.log(this.$refs.mycom.name);
        }
      }
    });
  </script>
```

## 路由

### 什么是路由

1. **后端路由：**对于普通的网站，所有的超链接都是URL地址，所有的URL地址都对应服务器上对应的资源；

2. **前端路由：**对于单页面应用程序来说，主要通过URL中的hash(#号)来实现不同页面之间的切换，同时，hash有一个特点：HTTP请求中不会包含hash相关的内容；所以，单页面程序中的页面跳转主要用hash实现；

3. 在单页面应用程序中，这种通过hash改变来切换页面的方式，称作前端路由（区别于后端路由）；

### 在 vue 中使用 vue-router

1. 导入 vue-router 组件类库：
```
<!-- 1. 导入 vue-router 组件类库 -->
  <script src="./lib/vue-router-2.7.0.js"></script>
```
2. 使用 router-link 组件来导航
```
<!-- 2. 使用 router-link 组件来导航 -->
<router-link to="/login">登录</router-link>
<router-link to="/register">注册</router-link>
```
3. 使用 router-view 组件来显示匹配到的组件
```
<!-- 3. 使用 router-view 组件来显示匹配到的组件 -->
<router-view></router-view>
```
4. 创建使用`Vue.extend`创建组件
```
    // 4.1 使用 Vue.extend 来创建登录组件
    var login = Vue.extend({
      template: '<h1>登录组件</h1>'
    });

    // 4.2 使用 Vue.extend 来创建注册组件
    var register = Vue.extend({
      template: '<h1>注册组件</h1>'
    });
```
5. 创建一个路由 router 实例，通过 routers 属性来定义路由匹配规则
```
// 5. 创建一个路由 router 实例，通过 routers 属性来定义路由匹配规则
    var router = new VueRouter({
      routes: [
        { path: '/login', component: login },
        { path: '/register', component: register }
      ]
    });
```
6. 使用 router 属性来使用路由规则
```
// 6. 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      router: router // 使用 router 属性来使用路由规则
    });
```

### 使用tag属性指定router-link渲染的标签类型

```
 <!-- router-link 默认渲染为一个a 标签 -->
    <router-link to="/login" tag="span">登录</router-link>
```

### 设置路由重定向

```
 { path: '/', redirect: '/account/login' }, // 使用 redirect 实现路由重定向
```

### 路由样式修改

```
//.router-link-active 默认的路由样式，可通过linkActiveClass: 'myactive'来修改默认的样式
.router-link-active, 
    .myactive {
      color: red;
      font-weight: 800;
      font-style: italic;
      font-size: 80px;
      text-decoration: underline;
      background-color: green;
}

var routerObj = new VueRouter({
      routes: [
        { path: '/', redirect: '/login' }, // 这里的 redirect 和 Node 中的 redirect 完全是两码事
        { path: '/login', component: login },
        { path: '/register', component: register }
      ],
      linkActiveClass: 'myactive'
})
```

### 在路由中定义参数

#### 路由中定义参数

1.在路由中通过查询字符串定义参数：

```
<!-- 如果在路由中，使用 查询字符串，给路由传递参数，则 不需要修改 路由规则的 path 属性 -->
    <router-link to="/login?id=10&name=zs">登录</router-link>
    <router-link to="/register">注册</router-link>
```

2.使用$route.query.属性来获取

```

var login = {
    template: '<h1>登录 --- {{ $route.query.id }} --- {{ $route.query.name }}</h1>',
    data(){
    	return {
    		msg: '123'
    	}
    },
    created(){ // 组件的生命周期钩子函数
   		 console.log(this.$route)
    	 console.log(this.$route.query.id)
    }
}
```

#### 在路由规则中定义参数

1. 在规则中定义参数：
```
<!-- 如果在路由中，使用 查询字符串，给路由传递参数，则 不需要修改 路由规则的 path 属性 -->
     { path: '/login/:id/:name', component: login },
```
​	2.通过路由传递

```
<router-link to="/login/12/ls">登录</router-link>
```

​	3.通过 `this.$route.params`来获取路由中的参数：

```
var register = Vue.extend({
      template: '<h1>注册组件 --- {{this.$route.params.id}}</h1>'
    });
```

### 使用 `children` 属性实现路由嵌套

```
  <div id="app">
    <router-link to="/account">Account</router-link>

    <router-view></router-view>
  </div>

  <script>
    // 父路由中的组件
    const account = Vue.extend({
      template: `<div>
        这是account组件
        <router-link to="/account/login">login</router-link> | 
        <router-link to="/account/register">register</router-link>
        <router-view></router-view>
      </div>`
    });

    // 子路由中的 login 组件
    const login = Vue.extend({
      template: '<div>登录组件</div>'
    });

    // 子路由中的 register 组件
    const register = Vue.extend({
      template: '<div>注册组件</div>'
    });

    // 路由实例
    var router = new VueRouter({
      routes: [
        { path: '/', redirect: '/account/login' }, // 使用 redirect 实现路由重定向
        {
          path: '/account',
          component: account,
          children: [ // 通过 children 数组属性，来实现路由的嵌套
            { path: 'login', component: login }, // 注意，子路由的开头位置，不要加 / 路径符
            { path: 'register', component: register }
          ]
        }
      ]
    });

    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {},
      methods: {},
      components: {
        account
      },
      router: router
    });
  </script>
```

### 命名视图实现经典布局

1. 标签代码结构：
```
<div id="app">
    <router-view></router-view>
    <div class="content">
      <router-view name="a"></router-view>
      <router-view name="b"></router-view>
    </div>
  </div>
```
2. JS代码：
```
<script>
    var header = Vue.component('header', {
      template: '<div class="header">header</div>'
    });

    var sidebar = Vue.component('sidebar', {
      template: '<div class="sidebar">sidebar</div>'
    });

    var mainbox = Vue.component('mainbox', {
      template: '<div class="mainbox">mainbox</div>'
    });

    // 创建路由对象
    var router = new VueRouter({
      routes: [
        {
          path: '/', components: {
            default: header,
            a: sidebar,
            b: mainbox
          }
        }
      ]
    });

    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {},
      methods: {},
      router
    });
  </script>
```
3. CSS 样式：
```
  <style>
    .header {
      border: 1px solid red;
    }

    .content{
      display: flex;
    }
    .sidebar {
      flex: 2;
      border: 1px solid green;
      height: 500px;
    }
    .mainbox{
      flex: 8;
      border: 1px solid blue;
      height: 500px;
    }
  </style>
```

## `watch`属性的使用
考虑一个问题：想要实现 `名` 和 `姓` 两个文本框的内容改变，则全名的文本框中的值也跟着改变；（用以前的知识如何实现？？？）

1. 监听`data`中属性的改变：
```
<div id="app">
    <input type="text" v-model="firstName"> +
    <input type="text" v-model="lastName"> =
    <span>{{fullName}}</span>
  </div>

  <script>
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {
        firstName: 'jack',
        lastName: 'chen',
        fullName: 'jack - chen'
      },
      methods: {},
      watch: {
        'firstName': function (newVal, oldVal) { // 第一个参数是新数据，第二个参数是旧数据
          this.fullName = newVal + ' - ' + this.lastName;
        },
        'lastName': function (newVal, oldVal) {
          this.fullName = this.firstName + ' - ' + newVal;
        }
      }
    });
  </script>
```
2. 监听路由对象的改变：
```
<div id="app">
    <router-link to="/login">登录</router-link>
    <router-link to="/register">注册</router-link>

    <router-view></router-view>
  </div>

  <script>
    var login = Vue.extend({
      template: '<h1>登录组件</h1>'
    });

    var register = Vue.extend({
      template: '<h1>注册组件</h1>'
    });

    var router = new VueRouter({
      routes: [
        { path: "/login", component: login },
        { path: "/register", component: register }
      ]
    });

    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {},
      methods: {},
      router: router,
      watch: {
        '$route': function (newVal, oldVal) {
          if (newVal.path === '/login') {
            console.log('这是登录组件');
          }
        }
      }
    });
  </script>
```

## `computed`计算属性的使用
1. 默认只有`getter`的计算属性：
```
<div id="app">
    <input type="text" v-model="firstName"> +
    <input type="text" v-model="lastName"> =
    <span>{{fullName}}</span>
  </div>

  <script>
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {
        firstName: 'jack',
        lastName: 'chen'
      },
      methods: {},
      computed: { // 计算属性； 特点：当计算属性中所以来的任何一个 data 属性改变之后，都会重新触发 本计算属性 的重新计算，从而更新 fullName 的值
        fullName() {
          return this.firstName + ' - ' + this.lastName;
        }
      }
    });
  </script>
```
2. 定义有`getter`和`setter`的计算属性：
```
<div id="app">
    <input type="text" v-model="firstName">
    <input type="text" v-model="lastName">
    <!-- 点击按钮重新为 计算属性 fullName 赋值 -->
    <input type="button" value="修改fullName" @click="changeName">

    <span>{{fullName}}</span>
  </div>

  <script>
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {
        firstName: 'jack',
        lastName: 'chen'
      },
      methods: {
        changeName() {
          this.fullName = 'TOM - chen2';
        }
      },
      computed: {
        fullName: {
          get: function () {
            return this.firstName + ' - ' + this.lastName;
          },
          set: function (newVal) {
            var parts = newVal.split(' - ');
            this.firstName = parts[0];
            this.lastName = parts[1];
          }
        }
      }
    });
  </script>
```

## `watch`、`computed`和`methods`之间的对比
1. `computed`属性的结果会被缓存，除非依赖的响应式属性变化才会重新计算。主要当作属性来使用；
2. `methods`方法表示一个具体的操作，主要书写业务逻辑；
3. `watch`一个对象，键是需要观察的表达式，值是对应回调函数。主要用来监听某些特定数据的变化，从而进行某些具体的业务逻辑操作；可以看作是`computed`和`methods`的结合体；

## `nrm`的安装使用
作用：提供了一些最常用的NPM包镜像地址，能够让我们快速的切换安装包时候的服务器地址；
什么是镜像：原来包刚一开始是只存在于国外的NPM服务器，但是由于网络原因，经常访问不到，这时候，我们可以在国内，创建一个和官网完全一样的NPM服务器，只不过，数据都是从人家那里拿过来的，除此之外，使用方式完全一样；
1. 运行`npm i nrm -g`全局安装`nrm`包；
2. 使用`nrm ls`查看当前所有可用的镜像源地址以及当前所使用的镜像源地址；
3. 使用`nrm use npm`或`nrm use taobao`切换不同的镜像源地址；

## 相关文章

1. [vue.js 1.x 文档](https://v1-cn.vuejs.org/)
2. [vue.js 2.x 文档](https://cn.vuejs.org/)
3. [String.prototype.padStart(maxLength, fillString)](http://www.css88.com/archives/7715)
4. [js 里面的键盘事件对应的键码](http://www.cnblogs.com/wuhua1/p/6686237.html)
5. [Vue.js双向绑定的实现原理](http://www.cnblogs.com/kidney/p/6052935.html) 
6. [URL中的hash（井号）](http://www.cnblogs.com/joyho/articles/4430148.html)