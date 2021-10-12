# Black horse buy Project

## 小程序的第三发框架

1.腾讯 wepy	类似vue

2.美团 mpvue 	类似vue

3.京东 taro	类似react

4.滴滴 chameeleon

5.uni-app	类似vue

## 小程序引入字体图标库

首先进入字体图标库网址[iconfont-阿里巴巴矢量图标库](https://www.iconfont.cn/?spm=a313x.7781069.1998910419.d4d0a486a)

 在搜索框中搜索自己所需要的图标，添加至购物车，在购物车中，将字体图标添加至项目，选择Font Class，并生成在线连接，打开在线链接之后，复制看到的代码，在微信小程序中的

styles中创建icon.wxss文件，将复制的代码放进去，最后在全局样式文件app.wxss中引入 @import ‘路径’

## 使用异步请求是的相关报错

说现在小程序的开发中添加可信任url

初始化的方法 success：function（）{}这种方法是无法是同this.setData的

需要使用success：（）=》{}这种方法
