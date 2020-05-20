# 测试版哔哩哔哩

> 仿bilibili视频网站项目，非官方网站，本项目仅供学习和参考！！

## 项目进度
**首页**
 - switcher组件
 - 轮播图组件
 - scroll组件（better-scroll二次封装）
 - 视频推荐列表
 - loading组件
 - confirm组件

**视频播放页**
 - 视频播放器
 - 视频简介
 - 视频推荐
 - 视频评论

**搜索页**
 - 热门搜索标签
 - 历史搜索记录
 - 防抖搜索关键词及高亮显示
 - 搜索结果列表

**视频分区**
 - 分区分类视频列表

**视频分区排行榜**
 - 分区视频排行榜列表

## 真实数据来源
 - 通过自己研究获取的部分视频数据
 - 由GitHub上的[SocialSisterYi](https://github.com/SocialSisterYi/bilibili-API-collect)提供的部分视频数据（感谢给我节省了大量工作量）

本项目中所用的的数据接口：[项目数据接口](https://github.com/Lewage59/bili-video/blob/master/static/api.md)
 注：本项目所有使用到的api全部放在src/api文件夹中


## 目录结构
这里只了介绍src文件夹中的内容
```javascript
├─api               //数据请求接口、相关函数和基础配置
├─base              //基础UI组件
├─common            //通用样式、工具类函数和icon图标
├─components        //核心功能组件
├─router            //路由配置文件
└─store             //vuex状态管理文件
  App.vue           //根组件
  main.js           //入口文件
```

## 技术栈
 - `vue2.5`：一套用于构建用户界面的渐进式框架
 - `vue-router`： Vue.js 官方的路由管理器
 - `vue-lazyload`：在应用程序中懒散加载图像的Vue模块
 - `vue-awesome-swiper`：基于swiper封装的vue滑动特效插件
 - `fastclick`：消除物理点击和在移动浏览器上触发点击事件之间300毫秒的延迟
 - `better-scroll`：解决移动端各种滚动场景需求的插件
 - `axios`：请求后端api数据
 - `vuex`：专为 Vue.js 应用程序开发的状态管理模式

## 项目问题
 - 目前的项目性能较差，优化空间非常多，所以项目开发完成后会对性能进行优化
 - 搜索框的内容中不可带有空格如果带有空格，会导致搜索出的结果出现代码无法编译的问题
 - 搜索框需要清空文本框后输入才可显示搜索提示词
 - 播放器的播放功能在Safari浏览器不兼容，导致无法播放
 - 项目中的video-list模块设计思路错误

（以上问题是本菜鸡发现但还未解决的问题，后期会进行处理）

# 部分功能代码展示
## 搜索框防抖核心代码
```js
// 防抖
export function debounce (func, delay) {
  let timer
  return function (...args) {
    if (timer) {
      clearTimeout(timer)
    }
    timer = setTimeout(() => {
      func.apply(this, args)
    }, delay)
  }
}
```
## 高亮搜索词核心代码
```js
// 高亮关键词
export function setHighlight (keyword, item, className) {
  let s = new Set()
  for (let k of keyword) {
    s.add(k)
  }
  s.forEach(function (value) {
    item = item.replace(value, function () {
      return `<em class="${className}">${value}</em>`
    })
  })
  return item
}
```


# 未来期望
目前这个项目还有很多功能还未实现，所以在之后的时间里尽快将剩余功能实现，呈现出一个完善的webapp项目出来，同时我也非常乐意大家的star以及提pr的嘻嘻嘻，这个项目还在努力开发中。。。。

# Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```
