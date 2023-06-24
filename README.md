<!-- logo -->
<p align="center">
    <img src="https://img2.baidu.com/it/u=2821710197,1569160826&fm=253&fmt=auto&app=138&f=PNG?w=600&h=421" />
</p>

# Vue学习

## vue3cli axios配置

### 一、npm 安装axios

```shell
在vue3cli 项目更目录下的命令行中输入以下代码
npm install axios
```

### 二、在main.js中引入

```js
在main.js中写入一下代码
import axios from 'axios';
 
axios.defaults.baseURL='接口的http前缀'
Vue.prototype.$axios = axios
```

### 三、配置跨域

```js
在vue.config.js中输入以下代码
module.exports = {
    /* 部署生产环境和开发环境下的URL：可对当前环境进行区分，baseUrl 从 Vue CLI 3.3 起已弃用，要使用publicPath */
    publicPath: process.env.NODE_ENV === 'production' ? './' : '/',
    /* 输出文件目录：在npm run build时，生成文件的目录名称 */
    outputDir: 'dist',
    /* 放置生成的静态资源 (js、css、img、fonts) 的 (相对于 outputDir 的) 目录 */
    assetsDir: "assets",
    /* 是否在构建生产包时生成 sourceMap 文件，false将提高构建速度 */
    productionSourceMap: false,
    /* 默认情况下，生成的静态资源在它们的文件名中包含了 hash 以便更好的控制缓存，你可以通过将这个选项设为 false 来关闭文件名哈希。(false的时候就是让原来的文件名不改变) */
    filenameHashing: false,
    /* 代码保存时进行eslint检测 */
    lintOnSave: true,
    /* webpack-dev-server 相关配置 */
    devServer: {
      /* 自动打开浏览器 */
      open: false,
      port: 8080, //本地端口号
      https: false,
      hotOnly: false,
      /* 使用代理 */
      proxy: {
        '/api': {
        target: 'http://47.106.241.182:8082',//服务器协议、ip和端口号
        secure: false,  // 如果是https接口，需要配置这个参数
        ws: true,//是否代理websockets
        changeOrigin: true,
        pathRewrite:{
          '^/api':''
       }
      }
    },
  }
}


或者在vite.config.js中加入以下代码
 server: {
    port: '3000',
    proxy: {
      '/api': {
        target: 'http://localhost:8080/',
        changeOrigin: true,
        rewrite: (path) => path.replace(/^\/api/, '') // 不可以省略rewrite
      }
    }
  }
```

### 四、统一配置token

```js
在main.js 中加入以下代码
axios.interceptors.request.use(config => {
    // 在发送请求之前做些什么

    // 判断是否存在token,如果存在将每个页面header添加token
    if (sessionStorage.getItem("token")) {
        //  ↓↓↓注意此处要与后端设置的变量名相统一
        config.headers.token = sessionStorage.getItem("token");
    }

    return config
})
```

# python学习

## 1.python基础学习
> pip requriments.txt
> 1.下载相关包命令 ```pip install -r requriments.txt```

### *学习基本语法和数据类型
###* 学习基本语法和数据类型

### * 学习基本语法和数据类型

## 2.python进阶学习
> this is a 3.3 python study

## 3.python蓝桥杯学习

## 4.python机器学习
