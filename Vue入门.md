- [什么是 Vue](#什么是-vue)
  - [什么是构建用户界面](#什么是构建用户界面)
  - [什么是渐进式](#什么是渐进式)
  - [什么是框架](#什么是框架)
  - [Vue 的两种开发方式：](#vue-的两种开发方式)
- [创建 Vue 实例](#创建-vue-实例)
- [插值表达式 `{{}}`](#插值表达式-)
- [响应式特性](#响应式特性)
- [Vue 开发者工具安装](#vue-开发者工具安装)
- [Vue 中的常用指令](#vue-中的常用指令)
  - [内容渲染指令](#内容渲染指令)
  - [条件渲染指令](#条件渲染指令)
  - [事件绑定指令](#事件绑定指令)
  - [属性绑定指令](#属性绑定指令)
      - [v-bind:class](#v-bindclass)
      - [v-bind:style](#v-bindstyle)
  - [列表渲染指令](#列表渲染指令)
  - [双向绑定指令](#双向绑定指令)
- [指令修饰符](#指令修饰符)
  - [什么是指令修饰符？](#什么是指令修饰符)
  - [按键修饰符](#按键修饰符)
  - [v-model 修饰符](#v-model-修饰符)
  - [事件修饰符](#事件修饰符)
- [computed 计算属性](#computed-计算属性)
  - [语法](#语法)
  - [计算属性的优势](#计算属性的优势)
- [watch 侦听器](#watch-侦听器)
- [Vue 生命周期](#vue-生命周期)
  - [生命周期钩子](#生命周期钩子)
  - [`$nextTick`](#nexttick)
- [Vue CLI](#vue-cli)
  - [基本介绍](#基本介绍)
      - [好处](#好处)
      - [使用](#使用)
  - [项目目录介绍和运行流程](#项目目录介绍和运行流程)
      - [项目目录介绍](#项目目录介绍)
      - [入口文件](#入口文件)
- [组件](#组件)
  - [组件分类](#组件分类)
  - [根组件 App.vue](#根组件-appvue)
  - [普通组件的注册使用](#普通组件的注册使用)
      - [局部注册](#局部注册)
      - [全局注册](#全局注册)
  - [组件是由三部分构成](#组件是由三部分构成)
      - [scoped 解决样式冲突](#scoped-解决样式冲突)
        - [data 是一个函数](#data-是一个函数)
- [组件通信](#组件通信)
  - [组件关系分类和通信解决方案](#组件关系分类和通信解决方案)
      - [父向子通信示例](#父向子通信示例)
      - [子向父通信代码示例](#子向父通信代码示例)
      - [非父子通信-bus](#非父子通信-bus)
      - [非父子通信-provide\&inject](#非父子通信-provideinject)
  - [props 校验](#props-校验)
- [插槽](#插槽)
- [路由的基本使用](#路由的基本使用)
  - [VueRouter 的使用](#vuerouter-的使用)
      - [固定 5 个固定的步骤](#固定-5-个固定的步骤)
      - [两个核心步骤](#两个核心步骤)
  - [路由的封装抽离](#路由的封装抽离)
  - [vue-router](#vue-router)
      - [router-link 自带的两个样式](#router-link-自带的两个样式)
  - [Vue 路由的重定向](#vue-路由的重定向)
  - [Vue 路由 404](#vue-路由-404)
  - [Vue 路由的模式设置](#vue-路由的模式设置)
- [路由跳转](#路由跳转)
  - [声明式导航](#声明式导航)
      - [查询参数传参](#查询参数传参)
      - [动态路由传参](#动态路由传参)
      - [区别](#区别)
  - [编程式导航](#编程式导航)
      - [path 路径跳转](#path-路径跳转)
      - [name 命名路由跳转](#name-命名路由跳转)


# 什么是 Vue

概念：Vue (读音 /vjuː/) 是一套 **构建用户界面** 的 **渐进式** **框架**

Vue2官网：<https://v2.cn.vuejs.org/>

## 什么是构建用户界面

**基于数据**渲染出用户可以看到的**界面**

![68187588702](assets/1681875887026.png)

## 什么是渐进式

所谓渐进式就是循序渐进，不一定非得把Vue中的所有API都学完才能开发Vue，可以学一点开发一点

## 什么是框架

所谓框架：就是一套完整的解决方案

**举个栗子**	

如果把一个完整的项目比喻为一个装修好的房子，那么框架就是一个毛坯房

我们只需要在“毛坯房”的基础上，增加功能代码即可

提到框架，不得不提一下库

- 库，类似工具箱，是一堆方法的集合，比如 axios、lodash、echarts等
- 框架，是一套完整的解决方案，实现了大部分功能，我们只需要按照一定的规则去编码即可。

下图是 库 和 框架的对比

![68187662027](assets/1681876620277.png)

框架的特点：有一套必须让开发者遵守的**规则**或者**约束**

咱们学框架就是学习的这些规则 [官网](https://v2.cn.vuejs.org/)

## Vue 的两种开发方式：

1. Vue 核心包开发
   - 场景：局部模块改造

2. Vue 核心包 & Vue 插件 & 工程化
   - 场景：整站开发


# 创建 Vue 实例

Vue 框架可以基于数据帮助我们渲染出用户界面

**核心步骤**

1. 准备容器
2. 引包（官网）：开发版本/生产版本
3. 创建 Vue 实例 `new Vue()`
4. 指定配置项，渲染数据
   1. `el` 指定挂载点
   2. `data` 提供数据

```html
<!-- Vue所管理的范围 -->
<div id="app">
  <!-- 这里将来会编写一些用于渲染的代码逻辑 -->
  <h1>{{ msg }}</h1>
</div>

<!-- 引入的是开发版本包 - 包含完整的注释和警告 -->
<script src="https://cdn.jsdelivr.net/npm/vue@2.7.14/dist/vue.js"></script>

<script>
  // 一旦引入 VueJS 核心包，在全局环境，就有了 Vue 构造函数
  const app = new Vue({
    // 通过 el 配置选择器，指定 Vue 管理的是哪个盒子
    el: '#app',
    // 通过 data 提供数据
    data: {
      msg: 'Hello 传智播客',
      count: 666
    },
    methods: {
    }
  })
</script>
```

# 插值表达式 `{{}}`

插值表达式语法：`{{ 表达式 }}`

```js
<p>{{nickName.toUpperCase()}}</p>

<p>{{age >= 18 ? '成年':'未成年'}}</p>

<p>{{obj.name}}</p>

<p>{{fn()}}</p>
```

1. 在插值表达式中使用的变量必须在 data 中进行了提供
2. 支持的是表达式，而非语句，比如：`if for`
3. 不能在标签属性中使用 `{{ }}` 插值 (插值表达式只能标签中间使用)

```js
<p title="{{username}}">我是P标签</p>  # worry!
```


# 响应式特性

​简单理解就是数据变，视图对应变

data 中的数据, 最终会被添加到 vue 实例上

1. 访问数据： "实例.属性名"
2. 修改数据： "实例.属性名"= "值"

![68188853934](assets/1681888539340.png)


# Vue 开发者工具安装

Vue Devtools

安装之后可以 F12 后看到多一个 Vue 的调试面板

![68188948344](assets/1681889483446.png)


# Vue 中的常用指令

vue 中的指令按照不同的用途可以分为如下 6 大类

-  内容渲染指令（v-html、v-text）
-  条件渲染指令（v-show、v-if、v-else、v-else-if）
-  事件绑定指令（v-on）
-  属性绑定指令 （v-bind）
-  双向绑定指令（v-model）
-  列表渲染指令（v-for）

指令是 vue 开发中最基础、最常用、最简单的知识点

## 内容渲染指令

内容渲染指令用来渲染 DOM 元素的文本内容

- v-text
  - 使用语法：`<p v-text="uname">hello</p>`，意思是将 uname 值渲染到 p 标签中
  - 类似 innerText，使用该语法，会覆盖 p 标签原有内容


- v-html
  - 使用语法：`<p v-html="intro">hello</p>`，意思是将 intro 值渲染到 p 标签中
  - 类似 innerHTML，使用该语法，会覆盖 p 标签原有内容
  - 类似 innerHTML，使用该语法，能够将 HTML 标签的样式呈现出来

代码演示：

```js
<div id="app">
    <h2>个人信息</h2>
    // 既然指令是vue提供的特殊的html属性，所以咱们写的时候就当成属性来用即可
    <p v-text="uname">姓名：</p>
    <p v-html="intro">简介：</p>
</div>

<script>
    const app = new Vue({
        el: '#app',
        data: {
            uname: '张三',
            intro: '<h2>这是一个<strong>非常优秀</strong>的boy<h2>'
        }
    })
</script>
```

## 条件渲染指令

条件判断指令，控制 DOM 的显示与隐藏

条件渲染指令有如下两个，分别是：

1. v-show

   1. 作用：  控制元素显示隐藏
   2. 语法：  `v-show="exp"` 表达式值为 true 显示， false 隐藏
   3. 原理：  添加 `style="display:none"` 达到隐藏效果
   4. 场景：  频繁切换显示隐藏的场景

2. v-if

   1. 作用：  控制元素显示隐藏（条件渲染）
   2. 语法：  `v-if="exp"` 表达式值为 true 显示， false 隐藏
   3. 原理：  基于条件 创建 或 移除 元素节点
   4. 场景：  要么显示，要么隐藏，不频繁切换的场景

3. v-else 和 v-else-if

   1. 作用：辅助 v-if 进行判断渲染
   2. 语法：`v-else` `v-else-if="表达式"`

示例代码：

```html
<p v-if="score >= 90">成绩评定A</p>
<p v-else-if="score >= 70">成绩评定B</p>
<p v-else-if="score >= 60">成绩评定C</p>
<p v-else>成绩评定D</p>
```

## 事件绑定指令

使用 Vue 时，如需为 DOM 注册事件，及其的简单，语法如下

注册事件 = 添加监听 + 处理逻辑

- `<button v-on:监听事件="处理逻辑"> </button>`
- `v-on:` 简写为 `@`

1. 内联语句

    ```html
    <div id="app">
        <button v-on:click="count++">+</button>
        <span>{{ count }}</span>
        <button @click="count--">-</button>
    </div>
    ```

2. 事件处理函数
   - methods 中的函数内部的 this 指向它属于的 Vue 实例
   - 如果不传递任何参数，则 methons 无需加小括号

    ```html
    # fn 是 vue 实例中的一个 methods

    <div id="app">
        <button v-on:click="fn">切换显示隐藏</button>
        <h1 v-show="isShow">黑马程序员</h1>
    </div>
    ```

## 属性绑定指令

1. 作用：动态设置 html 的标签属性，比如：src、url、title
2. 语法：`v-bind:属性名="exp"`
3. `v-bind:` 简写成 `:`

比如，有一个图片，它的 `src` 属性值数据 data 的 url 变量中存储

则可以这样设置属性值：

- `url` 为 vue 示例中的 data
- `<img v-bind:src="url">`
- `<img :src="url">`

#### v-bind:class

1. 对象语法

    ​适用场景：一个类名，来回切换

    ```html
    <div class="box" :class="{ 类名1: 布尔值, 类名2: 布尔值 }"></div>
    ```


2. 数组语法

    使用场景:批量添加或删除类

    ```html
    <div class="box" :class="[ 类名1, 类名2, 类名3 ]"></div>
    ```

#### v-bind:style

语法

```html
<div :style="{ CSS属性名1:属性值, CSS属性名2:属性值 }"></div>
```

## 列表渲染指令

基于一个数组来循环渲染一个列表结构

v-for 指令使用 `(item, index) in arr` 语法，其中：

- item 是数组中的每一项
- index 是每一项的索引，可以省略
- arr 是被遍历的数组

```html
// 遍历数组
<li v-for="(item,index) in somelist">{{ item }} - {{ index }} </li>

// 遍历对象
<div v-for="(value, key, index) in object">{{value}}</div>

// 遍历数字
// item 从 1 开始
<p v-for="item in 10">{{item}}</p>
```

## 双向绑定指令

所谓双向绑定就是：

1. 数据改变后，呈现的页面会更新
2. 页面更新后，数据也会随之而变

语法：`v-model="var"`

需求：使用双向绑定实现以下需求

1. 点击登录按钮获取表单中的内容
2. 点击重置按钮清空表单中的内容

![68191312573](assets/1681913125738.png)

```js
<div id="app">
    账户：<input type="text" v-model="usernameV"> <br><br>
    密码：<input type="password" v-model="passwordV"> <br><br>
    <button>登录</button>
    <button>重置</button>
</div>
```

- 下拉菜单  `select` value  // 在标签中设置属性 `value`
- 文本域    `texrarea` value
- 输入框    `input:text` value
- 单选框    `input:radio` value  // 在标签中设置属性 `value`
- 复选框    `input:checkbox` checked 

# 指令修饰符

## 什么是指令修饰符？

形如 `v-on:keyup.enter` 中 `enter` 就是修饰符

## 按键修饰符

`@keyup.enter` 点击 enter 键的时候才触发，等价于

```js
if ( e.key === "Enter" )
{
    do something
}
```

## v-model 修饰符

- `v-model.trim` 去除首位空格
- `v-model.number` 转数字

## 事件修饰符

- `@事件名.stop` 阻止冒泡
- `@事件名.prevent` 阻止默认行为
- `@事件名.stop.prevent` 阻止冒泡也阻止默认行为，连用

# computed 计算属性

基于现有的数据，计算出来的新属性

依赖的数据变化，自动重新计算

## 语法

```js
computed: {
    name (){
        logism
        return result
    }
}
```

```js
computed: {
    name: {
        get() {
            logism
            return result
        }
        set() {
            logism
        }
    }
}
```

- 使用起来和普通属性一样使用 `{{ name }}`
- computed 中的计算属性不能和 data 中的属性同名
- this 依然指向的是 Vue 实例

## 计算属性的优势

缓存特性（提升性能）

计算属性会对计算出来的结果缓存，再次使用直接读取缓存

依赖项变化了，会自动重新计算，并再次缓存


# watch 侦听器

​数据变化，则执行一些操作

语法

1. watch 同样声明在跟 data 同级的配置项中
2. 简单写法： 简单类型数据直接监视
3. 完整写法：添加额外配置项

```js
# data 中 words 变化，调用 watch 中的 words

data: {
    words: '苹果',
    obj: {
        son: '苹果'
    }
},

watch: {
    words (newValue, oldValue) {
        logism
    },
    'obj.son'(newValue, oldValue) {
        logism
    }
}
```

```js
# 完整写法
# 一次性 watch 多个变量

watch: {
    someOBJname: {
        deep: ture,       # 深度监视
        immediate: ture,  # 初始化时执行一次 handler()
        handler(newValue, oldValue) {
            logism
        }
    }
}
```

例子

```html
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script>
  // 接口地址：https://applet-base-api-t.itheima.net/api/translate
  // 请求方式：get
  // 请求参数：
  // （1）words：需要被翻译的文本（必传）
  // （2）lang： 需要被翻译成的语言（可选）默认值-意大利
  // -----------------------------------------------

  const app = new Vue({
    el: '#app',
    data: {
      // words: ''
      obj: {
        words: ''
      },
      result: '', // 翻译结果
      // timer: null // 延时器id
    },

    watch: {
      'obj.words'(newValue) {

        clearTimeout(this.timer)

        this.timer = setTimeout(async () => {
          const res = await axios({
            url: 'https://applet-base-api-t.itheima.net/api/translate',
            params: {
              words: newValue
            }
          })
          this.result = res.data.data
          console.log(res.data.data)
        }, 300)
        
      }
    }
  })
</script>
```


# Vue 生命周期

思考：什么时候可以发送初始化渲染请求？（越早越好）什么时候可以开始操作dom？（至少dom得渲染出来）
 

生命周期四个阶段：

1. 创建阶段：创建响应式数据
2. 挂载阶段：渲染模板
3. 更新阶段：修改数据，更新视图
4. 销毁阶段：销毁 Vue 实例


## 生命周期钩子

Vue 生命周期过程中，会自动运行一些函数，被称为【生命周期钩子】

开发者可以在钩子中嵌入额外的逻辑

![68206604029](assets/1682066040295.png)

```js
// 与 data 平级

async created() {
  // 1. 发送请求获取数据
  const res = await axios.get('http://hmajax.itheima.net/api/news')
  // 2. 更新到 list 中，用于页面渲染 v-for
  this.list = res.data.data
}
```

```js
# mounted 获取焦点

// 核心思路：
// 1. 等 input 框渲染出来 mounted 钩子
// 2. 让 input 框获取焦点 inp.focus()
mounted() {
  document.querySelector('#inp').focus()
}
```

## `$nextTick`

等 DOM 更新后才会触发执行此方法里的函数体

```js
this.$nextTick(() => {
  // content
})
```

注意：`$nextTick` 内的函数体 一定是箭头函数，这样才能让函数内部的 this 指向 Vue 实例

# Vue CLI

## 基本介绍

Vue CLI 是 Vue 官方提供的一个全局命令工具

可以帮助我们快速创建一个开发 Vue 项目的标准化基础架子【集成了webpack配置】

#### 好处

1. 开箱即用，零配置
2. 内置 babel 等工具
3. 标准化的 webpack 配置

#### 使用

1. 全局安装 `npm install -g @vue/cli`
2. 创建项目架子：`vue create project-name` (项目名不能使用中文)
3. 启动项目：`npm run serve` ( 命令不固定，配置在 package.json )

## 项目目录介绍和运行流程

#### 项目目录介绍

![68209214852](assets/1682092148521.png)

虽然脚手架中的文件有很多，目前咱们只需人事三个文件即可

1. `main.js`  入口文件
2. `App.vue`  App根组件 
3. `index.html ` 模板文件

#### 入口文件

![68209403287](assets/1682094032876.png)

# 组件

## 组件分类

.vue 文件分为 2 类

- 页面组件 （配置路由规则时使用的组件）：详见路由章节
- 复用组件（多个组件中都使用到的组件）

【存放目录】 分类开来的目的就是为了更易维护

- src/views 文件夹
- src/components 文件夹

## 根组件 App.vue

整个应用最上层的组件，包裹所有普通小组件

![68216913168](assets/1682169131688.png)

## 普通组件的注册使用

#### 局部注册

只能在注册的组件内使用

语法

```js
# 在 components 文件夹中创建 testcom.vue

# 1. 导入 whatever.vue
import someFuckingVar from './components/testcom.vue'

# 2. 局部注册
export default { // 局部注册
  components: {
    someFuckingName:someFuckingVar
    // 或者只写一个 someFuckingVar，等价于 someFuckingVar:someFuckingVar
  }
}
```

使用方式：

`<someFuckingName> </someFuckingName>`

#### 全局注册

```js
# 1. 导入 main.js
import someFuckingVar from './components/testcom.vue'

# 2. 全局注册
Vue.component('someFuckingName',someFuckingVar)
```

## 组件是由三部分构成

- 三部分构成
  - `template` : 结构 （vue2 中有且只能一个根元素）
  - `script` : js逻辑 
  - `style` : 样式 (可支持less，需要装包)


- 让组件支持less
  1. style 标签，`lang="less"` 开启 less 功能 
  2. 装包 : `npm i less less-loader -D`

#### scoped 解决样式冲突

默认情况：写在组件中的样式会 **全局生效**

可以给组件加上 `scoped` 属性，让样式只作用于当前组件

`<style scoped>`


##### data 是一个函数

目的是为了：保证每个组件实例，维护独立的一份数据对象

```js
# BaseCount.vue

<script>
export default {
  data: function () {
    return {
      count: 100,
    }
  },
}
</script>
```


# 组件通信

组件通信，就是指组件与组件之间的数据传递

- 组件的数据是独立的，无法直接访问其他组件的数据
- 想使用其他组件的数据，就需要组件通信

## 组件关系分类和通信解决方案

1. 父子关系
   - `props`
   - `$emit`
2. 非父子关系
   - `provede & inject`
   - `eventbus`

#### 父向子通信示例

父组件通过 props 将数据传递给子组件

![68231871178](assets/1682318711785.png)

父向子传值步骤

1. 给子组件以添加属性的方式传值
2. 子组件内部通过 props 接收
3. 模板中直接使用 props 接收的值

#### 子向父通信代码示例

子组件利用 $emit 通知父组件，进行修改更新

![68231896563](assets/1682318965635.png)

子向父传值步骤

1. $emit触发事件，给父组件发送消息通知
2. 父组件监听$emit触发的事件
3. 提供处理函数，在函数的性参中获取传过来的参数

#### 非父子通信-bus

非父子组件之间进行简易消息传递 (复杂场景：Vuex)

【步骤】

1. 创建一个都能访问的事件总线（空 Vue 实例）

   ```js
   import Vue from 'vue'
   const Bus = new Vue()
   export default Bus
   ```

2. 接受方，监听 Bus 的 $on 事件

   ```js
   created () {
     Bus.$on('sendMsg', (msg) => {
       this.msg = msg
     })
   }
   ```

3. 发送方，触发 Bus 的 $emit 事件

   ```js
   Bus.$emit('sendMsg', '这是一个消息')
   ```

#### 非父子通信-provide&inject

跨层级共享数据

【场景】

![68232950551](assets/1682329516878.png)

【语法】

1. 父组件 `provide()` 提供数据

    ```js
    export default {
      provide () {
        return {
          // 普通类型【非响应式】
          color: this.color, 
          // 复杂类型【响应式】
          userInfo: this.userInfo, 
        }
      }
    }
    ```

2. 子/孙组件 inject() 获取数据

    ```js
    export default {
      inject: ['color','userInfo'],
      created () {
        console.log(this.color, this.userInfo)
      }
    }
    ```

【注意】

- provide提供的简单类型的数据不是响应式的，复杂类型数据是响应式。（推荐提供复杂类型数据）
- 子/孙组件通过 inject 获取的数据，不能在自身组件内修改

## props 校验

为组件的 prop 指定验证要求，不符合要求，控制台就会有错误提示

```html
<script>
export default {
  props: ['w'],
  //
  props: {
    w: Number
  }
  //
  props: {
    w: {
      type: ,                    // 类型校验
      required: ,               // 是否必填
      default: ,               // 默认
      validator (value) {    // value 为传来的值
        // 自定义校验逻辑
        return bool
      }
    }
  }
}
</script>
```


# 插槽

【作用】

让组件内部的一些  结构支持自定义

【基本语法】
1. slot 占位
2. 可以有默认内容
3. 为 slot 赋予唯一标识符 name
4. 可以传递参数，不过我没记相应的笔记

【代码】

```js
# MyDialog.vue

<template>
    <div>
        <slot name="test">默认内容</slot>
    </div>
</template>
```

```js
# App.vue

<template>
    <div>
        <MyDialog>
            <template v-slot:test> // v-slot: 可以简写为 #
                代替 slot
            </template>
        </MyDialog>
    </div>
</template>
```


# 路由的基本使用

[官网](https://v3.router.vuejs.org/zh/)

## VueRouter 的使用

#### 固定 5 个固定的步骤

1. 下载 VueRouter 模块到当前工程，版本3.6.5

   ```bash
   yarn add vue-router@3.6.5
   ```

2. main.js 中引入VueRouter

   ```js
   import VueRouter from 'vue-router'
   ```

3. 安装注册

   ```js
   Vue.use(VueRouter)
   ```

4. 创建路由对象

   ```js
   const router = new VueRouter()
   ```

5. 注入，将路由对象注入到 new Vue 实例中，建立关联

   ```js
   new Vue({
     render: h => h(App),
     router:router
   }).$mount('#app')

   ```

当我们配置完以上5步之后 就可以看到浏览器地址栏中的路由 变成了 `/#/` 的形式表示项目的路由已经被 Vue-Router 管理了

![68247920745](assets/1682479207453.png)

#### 两个核心步骤

1. 创建需要的组件 (views目录)，配置路由规则

    ```js
    # main.js

    const router = new VueRouter({
    // routes 路由规则们
    // route  一条路由规则 { path: 路径, component: 组件 }
    routes: [
      { path: '/find', component: Find },
      { path: '/my', component: My },
      { path: '/friend', component: Friend },
    ]
    })
    ```

2.  配置导航，配置路由出口(路径匹配的组件显示的位置)

    ```js
    # App.vue

    <div class="footer_wrap">
      <a href="#/find">发现音乐</a>
      <a href="#/my">我的音乐</a>
      <a href="#/friend">朋友</a>
    </div>

    <div class="top">
      <router-view></router-view>
    </div>
    ```

## 路由的封装抽离

问题：所有的路由配置都在 main.js 中合适吗？

目标：将路由模块抽离出来

好处：**拆分模块，利于维护**

![68248141030](assets/1682481410304.png)

路径简写：

脚手架环境下 `@` 指代 src 目录，可以用于快速引入组件

## vue-router

全局组件 `router-link` 取代 `a` 标签

它本质还是 a 标签

语法： `<router-link to="path">content</router-link>`

```html
<router-link to="/find">发现音乐</router-link>
<router-link to="/my">我的音乐</router-link>
```

#### router-link 自带的两个样式

使用 router-link 跳转后，我们发现，当前点击的链接默认加了两个 class 的值

- `router-link-exact-active`
  - 模糊匹配
- `router-link-active`
  - 精确匹配

我们可以给任意一个 class 属性添加高亮样式即可实现功能

这两个类名名字自定义

```js
const router = new VueRouter({
    routes: [...],
    linkActiveClass: "yourDesignName1",
    linkExactActiveClass: "yourDesignName1"
})
```

## Vue 路由的重定向

网页打开时， url 默认是 `/` 路径，未匹配到组件时，会出现空白

【解决方案】

重定向

【语法】

```js
{ path: '/', redirect: '/home' },
```

## Vue 路由 404

当路径匹配失败时的默认跳转

```js
# path: '*' 行应该写在最后，因为 router 是从上往下匹配

import NotFind from '@/views/NotFind'

const router = new VueRouter({
  routes: [
    ...,
    { path: '*', component: NotFind } //最后一个
  ]
})
```

## Vue 路由的模式设置

- hash路由(默认)
  - 例如:  http://localhost:8080/#/home
- history路由(常用)
  - 例如: http://localhost:8080/home  
  - 以后上线需要服务器端支持，开发环境 webpack 给规避掉了 history 模式的问题

```js
const router = new VueRouter({
    mode:'histroy', //默认是hash
    routes:[]
})
```

# 路由跳转

路由跳转时

- 原组件 destroy，返回时又 creat
- 目的组件开始 creat

## 声明式导航

router-link 跳转方式

我们可以通过两种方式，在跳转的时候把所需要的参数传到其他页面中

- 查询参数传参
- 动态路由传参

#### 查询参数传参

- 传出参数

`<router-link to="/path?arg1=val1&arg2=val2"></router-link>`

- 接受参数

`$route.query.arg`

#### 动态路由传参

- 配置动态路由

```js
const router = new VueRouter({
  routes: [
    ...,
    { 
      path: '/search/:arg?',      # 变化部分，其中 ? 表示可选符，即 arg='' 也行
      component: Search 
    }
  ]
})
```

- 配置导航链接

`to="/path/val"`

- 对应页面组件接受参数

`$route.params.arg`

#### 区别

1. 查询参数传参  (比较适合传**多个参数**) 
2. 动态路由传参 (**优雅简洁**，传单个参数比较方便)


注意：动态路由也可以传多个参数，但一般只传一个


## 编程式导航

点击按钮实现跳转

两种跳转方式

- path 路径跳转 （简易方便）
- name 命名路由跳转 (适合 path 路径长的场景)

两种传参方式

1. 查询参数 
2. 动态路由传参

#### path 路径跳转

```js
# 查询参数传参

//简单写法
this.$router.push('/pathString?arg1=val1&arg2=val2')

//完整写法
this.$router.push({
  path: '/pathString',
  query: {
    arg1: val1,
    arg2: val2
  }
})
```

#### name 命名路由跳转

- 路由规则，必须配置 name 配置项

```js
# 动态路由传参

{ name: 'routerName', path: '/xxx', component: XXX },
```

- 通过 name 来进行跳转

```js
this.$router.push({
  name: 'routerName',
  params: {
    arg1: val1,
    arg2: val2
  }
})
```