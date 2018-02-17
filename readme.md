# axios 拓展

#### 1、简介

- `Axios`是基于`promise`的`HTTP`库，可以用于浏览器和 node.js 的服务器端通信。

- 官网： [axios](https://github.com/axios/axios)

#### 2、使用方式：

- `script` 导入： `<script src="https://unpkg.com/axios/dist/axios.min.js"></script>` 
- `npm` 安装：`npm install axios` `npm install vue-axios`
- `import Axios from 'axios'`; `import VueAxios from 'vue-axios'`;
- `Vue.use(VueAxios,Axios)`;

#### 3、注意点：

- **`axios` 不支持跨域请求数据**

#### 4、Vue 中使用方法

- ** 与vue-resource 类似*

```javascript
    this.$http.get('http://localhost:16688/slides111')
        .then((res) => {
            this.list = res.data;
        })
```

#### 5、使用方法：

- 第一种使用方法：

```javascript
    axios({
         methods : 'get',
         url : 'http://localhost:16688/slides'
    }).then((res) => {
        this.list = res.data;
    })
```


- 第二种使用方法：

```javascript
    axios.get('http://localhost:16688/slides').then((res) => {
        this.list = res.data;
    })
```

- 第三使用方法(提取公用js)：

提取公用js文件

```javascript
    import axios from 'axios';
    export var HTTP = axios.create({
      baseURL: 'http://localhost:16688/'  // 提取域名
    });
```

调用公用js文件
```javascript
    import {HTTP} from '../kits/common.js'

    HTTP.get('slides').then((res) => {
        this.list = res.data;
    })
```



利用vue 使用 axios的 几种方式 
vue 使用axios 
axios   是 不 支持跨域请求的 
npm install axios --save 首先下载这个 包 


使用方式 一  

在main.js 中导入这个包 
import axios from 'axios'
Vue.prototype.$axios = axios 
发送 get 请求 

this.$axios.get(url).then((res) = > {
     res = res.data;
})


发送post 请求  
axios  发送post请求的时候 如果不进行设置请求头 是 不能获取到数据 的

    this.$axios.post(url,{},
    {
    headers: {
                                'Content-Type': 'application/x-www-form-urlencoded'
    }
    }).then((res)=>{
    res = res.data;
    })
 
 使用方式二 
  在main.js 中引入 

  import axios  from 'axios'
  post 请求 中 需要设置一下请求头  是必须的  
 axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
 Vue.prototype.$axios = axios.create({
  baseURL: 'http://vue.studyit.io',
  timeout: 10000,
  headers: { 'Content-Type': 'application/x-www-form-urlencoded' }
 });

 axios 的一些默认的配置  
axios.defaults.baseURL = 'https://api.example.com';
axios.defaults.headers.common['Authorization'] = AUTH_TOKEN;
axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
   如果将header  
 this.$axios.get(url).then((res)=>{
      res = res.data 
 })
 发送post 请求  
 参数二 是中间需要 提交给服务器的数据 如果 获取不到数据 需要设置一下请求头 
 第三个参数 需要加上去 也是 一个对象的形式
 headers: {
     'Content-Type': 'application/x-www-form-urlencoded'
    }
 this.$axios.post(url,{}).then((res)=>{
      是异步请求的数据 中间 只有这个能使用  res.data 
      res = res.data 
 })

