# gshop

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).


## 笔记
2018.08.21 <br/>
### 1.页面模块拆分
路由页面 Msite.vue profile.vue Search.vue Order.vue  
router index.js中
```
import Vue from 'vue'
import Router from 'vue-router'
import MSite from '../pages/MSite/MSite.vue'

Vue.use(Router)
export default new Router({
   routes:[
   {
    path:'/msite',
    component:Miste
    },
    path:'/'
    redirect:'/msite'
   ]
})
```
### 2.公共头部 HeaderTop  
  <a href="https://www.cnblogs.com/-ding/p/6339737.html">利用插槽分发内容slot进行组件间通信</a>   
  HeaderTop.vue中
  ```
   <header class="header">
    <slot name="left"></slot>
    <span class="header_title">
      <span class="header_title_text ellipsis">{{title}}</span>
    </span>
    <slot name="right"></slot>
  </header> 
  ```
  具体页面
  ```
    <HeaderTop title="昌平区北七家宏福科技园(337省道北)">
      <span class="header_search" slot="left">
            <i class="iconfont icon-sousuo"></i>
      </span>
      <span class="header_login" slot="right">
            <span class="header_login_text">登录|注册</span>
      </span>
    </HeaderTop>
   ```

2018.08.25
### 1.轮播效果实现 swiper
 <a href="https://www.swiper.com.cn/api/start/new.html">Swiper官网</a>..
### 2.返回到前一个页面
```
 <a href="javascript:" class="go_back" @click="$router.back()">
 ```
### 3.部分一级路由显示底部导航
route中index.js添加meta元数据
```
 {
      path: '/msite',
      component: MSite,
      meta:{
        showFooter:true
      }
    },
 ```
 app.vue中用v-show控制显示
 ```
 <FooterGuide v-show="$route.meta.showFooter" />
 ```

