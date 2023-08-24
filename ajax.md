- [AJAX](#ajax)
  - [实例](#实例)
  - [异步特性](#异步特性)
  - [axios 框架](#axios-框架)
      - [get 请求](#get-请求)
      - [post 请求](#post-请求)
      - [响应结构](#响应结构)
      - [拦截器](#拦截器)


# AJAX

Asynchronous Javascript and XML

使页面进行异步更新

## 实例

`readyState` 属性代表了 `XMLHttpRequest` 对象的状态

`onreadystatechange` 事件能够监听 `XMLHttpRequest` 对象的状态变化

`XMLHttpRequest` 对象的五种状态:
- 0-(未初始化) 还没有调用 `send()` 方法
- 1-(载入) 已调用 `send()` 方法，已建立服务器连接
- 2-(载入完成) `send()` 方法执行完成，已经接收到全部响应内容
- 3-(交互) 正在解析响应内容
- 4-(完成) 响应内容解析完成，可以在客户端调用了

```html
<script>
    // XMLHttpRequest 被内置，不用引包
    // 创建 XMLHttpRequest 核心对象
    let xhr = new XMLHttpRequest

    // 使用 open 方法创建 http 请求
    xhr.open('get', 'path')

    // 向服务器端发送请求
    xhr.send(null)

    // 监听 XMLHttpRequest 核心对象
    xhr.onreadystatechange = function () {
        if (xhr.readyState == 4) {
            if (xhr.status == 200) {
                console.log(xhr.responseText)
            }
        }
    }
</script>
```

## 异步特性

## axios 框架

[axios 官网](https://www.axios-http.cn/)

#### get 请求

显示请求

```html
<script>
    // 向 path 发起请求，参数为 params
    axios.get('/path', {
        params: {            // 携带的参数
            ID: 12345
        }
    })
        .then(function (response) {
            // 处理成功情况
            console.log(response);
        })
        .catch(function (error) {
            // 处理错误情况
            console.log(error);
        })
        .then(function () {
            // 总是会执行
        });  
</script>
```

#### post 请求

```html
<script>
    axios.post('/path', {   // 携带的参数
        firstName: 'Fred',
        lastName: 'Flintstone'
    })
        .then(function (response) {
            console.log(response);
        })
        .catch(function (error) {
            console.log(error);
        });
</script>
```

#### 响应结构

```java
{
  // `data` 由服务器提供的响应
  data: {},

  // `status` 来自服务器响应的 HTTP 状态码
  status: 200,

  // `statusText` 来自服务器响应的 HTTP 状态信息
  statusText: 'OK',

  // `headers` 是服务器响应头
  // 所有的 header 名称都是小写，而且可以使用方括号语法访问
  // 例如: `response.headers['content-type']`
  headers: {},

  // `config` 是 `axios` 请求的配置信息
  config: {},

  // `request` 是生成此响应的请求
  // 在node.js中它是最后一个ClientRequest实例 (in redirects)，
  // 在浏览器中则是 XMLHttpRequest 实例
  request: {}
}
```

#### 拦截器

在请求或响应被 then 或 catch 处理前拦截它们

```java
// 添加请求拦截器
axios.interceptors.request.use(function (config) {
    // 在发送请求之前做些什么
    return config;
  }, function (error) {
    // 对请求错误做些什么
    return Promise.reject(error);
  });

// 添加响应拦截器
axios.interceptors.response.use(function (response) {
    // 2xx 范围内的状态码都会触发该函数。
    // 对响应数据做点什么
    return response;
  }, function (error) {
    // 超出 2xx 范围的状态码都会触发该函数。
    // 对响应错误做点什么
    return Promise.reject(error);
  });
```