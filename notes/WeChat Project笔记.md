# WeChat Project笔记

微信小程序官方文档[微信开放文档 (qq.com)](https://developers.weixin.qq.com/miniprogram/dev/framework/)

## 准备环境

```html
进入微信小程序下载程序的网址选择下载需要的文件
//网址：https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html
```

```html
下载之后进行安装，之后用个人的微信账号进行登录，按着提示完成操作步骤即可
```

## 项目的基本目录

![image-20210712114114821](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712114114821.png)



## 创建模板

```
//1.创建模板文件 templates
//2.创建模板所用的公共头和公共底部
//3.在创建的公共头公共底中添加公共组件
//4.在所需要的公共页面上进行引入 <include src="引入的模板路径" />
//5.此处的/是必须添加的  否者会有报错信息或者不显示添加的公共模板内容
```

```
使用template创建的模板需要使用import进行引入
例：在公共模板header中使用template进行创建
<template name=“t1”>
	头部模板的信息
</template>
<template name=“t2”>
	头部模板的信息
</template>
在需要引入模板的试图页中需要使用import进行引入
例：<import src="引入的路径" />
<template is="模板name的命名">
```

## 底部导航栏

![image-20210712125012300](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712125012300.png)

配置方法：

![image-20210712125038427](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712125038427.png)

```
list中至少需要两项才不会有报错提示
"pagePath": "pages/demo1/demo1",//点击跳转的路径
"text": "demo1",//在图标下显示的文字
"iconPath": "./icon/闹钟_alarm-clock.png",  //文字图标的地址
“selectedIconPath": "./icon/闹钟_alarm-clock.png"  //点击之后图标的地址
tabBar 更多的用法样式的设置 在官方文档中可继续参考
```



## 模板语法

### 数据绑定

```html
<text>标签	相当于html中的span标签	行内标签	默认不会换行
<view>标签	相当于html中的div标签	块级标签	默认会换行
```

```html
在pages文件的下级目录中的js文件中 data中编辑数据 在wxml中使用{{}} //类似于Vue的数据绑定
```

![image-20210712132226377](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712132226377.png)

### 运算

```html
运算=》表达式 -- 
1.在花括号中加入表达式 ---”语句“ 
2.表达式 指的是一些简单的	运算	数字运算	字符串	拼接	逻辑运算
2.1数字的加减成熟
2.2字符串的拼接
2.3三元表达式
3语句
3.1复杂的代码片段
```

### 列表渲染

![image-20210712134423550](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712134423550.png)

![image-20210712134933377](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712134933377.png)

```html
//wx:for
//wx:key="唯一的值"  用来提高性能  不重复的
// wx:for-item="item" wx:for-index="index"	没有嵌套循环只有一层的时候可以省略
<view wx:for="{{list}}" wx:for-item="item" wx:for-index="index" wx:key="id">
	{{index}} -- {{item.name}}
</view>
```

```html
block标签相当于占位符
```

### 条件渲染

```html
//wx:if
//{{}}可以定义data动态显示
<view>条件渲染</view>
<view wx:if="{{true}}">显示</view>
<view wx:if="{{false}}">隐藏</view>
```

```html
//hidden
<view hidden>11111</view>
```

![image-20210712140033128](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712140033128.png)

## 事件绑定

### 添加绑定事件

```hmtl
//在定义的btn按钮中添加bindtap事件且定义事件名称，在js文件中，添加事件名称：function（）{}
//在其中写入点击事件的事件即可
```

### 微信小程序的事件

![image-20210712141201604](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712141201604.png)

```
//事件的类别
点击事件 tap
长按事件 longtap
触摸事件 touchstart touchend touchmove touchcancel
其他 submit input .....
```

```
//事件冒泡
点击某一组件或其他时，会让组件的父组件或者上级的组件产生事件
```

```
//事件的绑定
bind绑定
//可以出发冒泡事件
catch绑定
//catch绑定事件则只触发单个绑定事件的组件
```

```
小程序传递参数时  需要注意------不能直接传参 否则会被小程序误认为是一个方法  无法识别   需要进行自定义  data-自定义名称="{{参数}}"
```

## 微信小程序样式

| 设备    | rpx转换px    | px转换rpx   |
| ------- | ------------ | ----------- |
| IPhone5 | 1rpx=0.42px  | 1px=2.34rpx |
| IPhone6 | 1rpx=0.5px   | 1px=2rpx    |
| IPhone7 | 1rpx=0.552px | 1px=1.81rpx |

```
在小程序中是不需要自己引入样式文件的
```

![image-20210712144634590](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712144634590.png)

### 样式导入

```
可以使用@import进行导入 只支持相对路径
```

### 选择器

```
现在的小程序是不支持通配符*
```

### 在小程序中使用less

```js
需要在微信小程序中添加插件 Easy less
在配置中添加：
"less.compile": {
        "outExt":".wxss"
    }
}
```

![image-20210712151114346](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712151114346.png)

## 常见组件

###  view（布局）

```
用来代替之前的div标签
```

### text（文本）

```
1.类似于span
2.只能嵌套text
3.长按文字可以复制（该标签自带功能）
4.可以对空格回车进行编码
```

| 属性名     | 类型    | 默认值 | 说明         |
| ---------- | ------- | ------ | ------------ |
| selectable | Boolean | false  | 文本是否可选 |
| decode     | Boolean | false  | 是否解码     |

### image（图像）

| 属性名    | 类型    | 默认值        | 说明                     |
| --------- | ------- | ------------- | ------------------------ |
| src       | string  |               | 图片资源地址             |
| mode      | string  | ‘scaleToFill‘ | 图片的裁剪、缩放的等模式 |
| lazy-load | Boolean | false         | 图片的懒加载             |

**mode 的合法值**

mode有13种模式	4种缩放	9种裁剪	默认的宽高	w：320px	 h：240px

| 值           | 说明                                                         | 最低版本                                                     |
| :----------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| scaleToFill  | 缩放模式，不保持纵横比缩放图片，使图片的宽高完全拉伸至填满 image 元素 |                                                              |
| aspectFit    | 缩放模式，保持纵横比缩放图片，使图片的长边能完全显示出来。也就是说，可以完整地将图片显示出来。 |                                                              |
| aspectFill   | 缩放模式，保持纵横比缩放图片，只保证图片的短边能完全显示出来。也就是说，图片通常只在水平或垂直方向是完整的，另一个方向将会发生截取。 |                                                              |
| widthFix     | 缩放模式，宽度不变，高度自动变化，保持原图宽高比不变         |                                                              |
| heightFix    | 缩放模式，高度不变，宽度自动变化，保持原图宽高比不变         | [2.10.3](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| top          | 裁剪模式，不缩放图片，只显示图片的顶部区域                   |                                                              |
| bottom       | 裁剪模式，不缩放图片，只显示图片的底部区域                   |                                                              |
| center       | 裁剪模式，不缩放图片，只显示图片的中间区域                   |                                                              |
| left         | 裁剪模式，不缩放图片，只显示图片的左边区域                   |                                                              |
| right        | 裁剪模式，不缩放图片，只显示图片的右边区域                   |                                                              |
| top left     | 裁剪模式，不缩放图片，只显示图片的左上边区域                 |                                                              |
| top right    | 裁剪模式，不缩放图片，只显示图片的右上边区域                 |                                                              |
| bottom left  | 裁剪模式，不缩放图片，只显示图片的左下边区域                 |                                                              |
| bottom right | 裁剪模式，不缩放图片，只显示图片的右下边区域                 |                                                              |

```
lazy-load		当图片出现在视口的上下三屏高度之内开始自动懒加载
```

### swiper（轮播）

```
wsiper存在默认样式	width 100%	height 150px  
images 也是存在默认样式的
swiper	高度	无法实现内容撑开（高度不够）
```

![image-20210712154831638](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712154831638.png)

![image-20210712155421245](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712155421245.png)

### navigator（超链接标签）

页面链接。

| 属性                   | 类型    | 默认值          | 必填 | 说明                                                         | 最低版本                                                     |
| :--------------------- | :------ | :-------------- | :--- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| target                 | string  | self            | 否   | 在哪个目标上发生跳转，默认当前小程序                         | [2.0.7](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| url                    | string  |                 | 否   | 当前小程序内的跳转链接                                       | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| open-type              | string  | navigate        | 否   | 跳转方式                                                     | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| delta                  | number  | 1               | 否   | 当 open-type 为 'navigateBack' 时有效，表示回退的层数        | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| app-id                 | string  |                 | 否   | 当`target="miniProgram"`时有效，要打开的小程序 appId         | [2.0.7](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| path                   | string  |                 | 否   | 当`target="miniProgram"`时有效，打开的页面路径，如果为空则打开首页 | [2.0.7](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| extra-data             | object  |                 | 否   | 当`target="miniProgram"`时有效，需要传递给目标小程序的数据，目标小程序可在 `App.onLaunch()`，`App.onShow()` 中获取到这份数据。[详情](https://developers.weixin.qq.com/miniprogram/dev/framework/app-service/app.html) | [2.0.7](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| version                | string  | release         | 否   | 当`target="miniProgram"`时有效，要打开的小程序版本           | [2.0.7](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| hover-class            | string  | navigator-hover | 否   | 指定点击时的样式类，当`hover-class="none"`时，没有点击态效果 | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| hover-stop-propagation | boolean | false           | 否   | 指定是否阻止本节点的祖先节点出现点击态                       | [1.5.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| hover-start-time       | number  | 50              | 否   | 按住后多久出现点击态，单位毫秒                               | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| hover-stay-time        | number  | 600             | 否   | 手指松开后点击态保留时间，单位毫秒                           | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| bindsuccess            | string  |                 | 否   | 当`target="miniProgram"`时有效，跳转小程序成功               | [2.0.7](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| bindfail               | string  |                 | 否   | 当`target="miniProgram"`时有效，跳转小程序失败               | [2.0.7](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| bindcomplete           | string  |                 | 否   | 当`target="miniProgram"`时有效，跳转小程序完成               | [2.0.7](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |

**target 的合法值**

| 值          | 说明       | 最低版本 |
| :---------- | :--------- | :------- |
| self        | 当前小程序 |          |
| miniProgram | 其它小程序 |          |

**open-type 的合法值**

| 值           | 说明                                                         | 最低版本                                                     |
| :----------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| navigate     | 对应 [wx.navigateTo](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.navigateTo.html) 或 [wx.navigateToMiniProgram](https://developers.weixin.qq.com/miniprogram/dev/api/navigate/wx.navigateToMiniProgram.html) 的功能 |                                                              |
| redirect     | 对应 [wx.redirectTo](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.redirectTo.html) 的功能 |                                                              |
| switchTab    | 对应 [wx.switchTab](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.switchTab.html) 的功能 |                                                              |
| reLaunch     | 对应 [wx.reLaunch](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.reLaunch.html) 的功能 | [1.1.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| navigateBack | 对应 [wx.navigateBack](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.navigateBack.html) 的功能 | [1.1.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| exit         | 退出小程序，`target="miniProgram"`时生效                     | [2.1.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |

**version 的合法值**

| 值      | 说明                                                         | 最低版本 |
| :------ | :----------------------------------------------------------- | :------- |
| develop | 开发版                                                       |          |
| trial   | 体验版                                                       |          |
| release | 正式版，仅在当前小程序为开发版或体验版时此参数有效；如果当前小程序是正式版，则打开的小程序必定是正式版。 |          |

### rich-text（富文本）

```
通过nodes来实现	接受标签字符串	接收对象数组	
```

![image-20210712160950105](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712160950105.png)

富文本。

| 属性  | 类型         | 默认值 | 必填 | 说明                 | 最低版本                                                     |
| :---- | :----------- | :----- | :--- | :------------------- | :----------------------------------------------------------- |
| nodes | array/string | []     | 否   | 节点列表/HTML String | [1.4.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| space | string       |        | 否   | 显示连续空格         | [2.4.1](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |

#### **space 的合法值**

| 值   | 说明                   | 最低版本 |
| :--- | :--------------------- | :------- |
| ensp | 中文字符空格一半大小   |          |
| emsp | 中文字符空格大小       |          |
| nbsp | 根据字体设置的空格大小 |          |

#### nodes

现支持两种节点，通过type来区分，分别是元素节点和文本节点，默认是元素节点，在富文本区域里显示的HTML节点 *元素节点：type = node**

| 属性     | 说明       | 类型   | 必填 | 备注                                     |
| :------- | :--------- | :----- | :--- | :--------------------------------------- |
| name     | 标签名     | string | 是   | 支持部分受信任的 HTML 节点               |
| attrs    | 属性       | object | 否   | 支持部分受信任的属性，遵循 Pascal 命名法 |
| children | 子节点列表 | array  | 否   | 结构和 nodes 一致                        |

*文本节点：type = text**

| 属性 | 说明 | 类型   | 必填 | 备注         |
| :--- | :--- | :----- | :--- | :----------- |
| text | 文本 | string | 是   | 支持entities |

#### 受信任的HTML节点及属性

全局支持class和style属性，**不支持id属性**。

| 节点       | 属性                            |
| :--------- | :------------------------------ |
| a          |                                 |
| abbr       |                                 |
| address    |                                 |
| article    |                                 |
| aside      |                                 |
| b          |                                 |
| bdi        |                                 |
| bdo        | dir                             |
| big        |                                 |
| blockquote |                                 |
| br         |                                 |
| caption    |                                 |
| center     |                                 |
| cite       |                                 |
| code       |                                 |
| col        | span，width                     |
| colgroup   | span，width                     |
| dd         |                                 |
| del        |                                 |
| div        |                                 |
| dl         |                                 |
| dt         |                                 |
| em         |                                 |
| fieldset   |                                 |
| font       |                                 |
| footer     |                                 |
| h1         |                                 |
| h2         |                                 |
| h3         |                                 |
| h4         |                                 |
| h5         |                                 |
| h6         |                                 |
| header     |                                 |
| hr         |                                 |
| i          |                                 |
| img        | alt，src，height，width         |
| ins        |                                 |
| label      |                                 |
| legend     |                                 |
| li         |                                 |
| mark       |                                 |
| nav        |                                 |
| ol         | start，type                     |
| p          |                                 |
| pre        |                                 |
| q          |                                 |
| rt         |                                 |
| ruby       |                                 |
| s          |                                 |
| section    |                                 |
| small      |                                 |
| span       |                                 |
| strong     |                                 |
| sub        |                                 |
| sup        |                                 |
| table      | width                           |
| tbody      |                                 |
| td         | colspan，height，rowspan，width |
| tfoot      |                                 |
| th         | colspan，height，rowspan，width |
| thead      |                                 |
| tr         | colspan，height，rowspan，width |
| tt         |                                 |
| u          |                                 |
| ul         |                                 |

#### Bug & Tip

1. `tip`: nodes 不推荐使用 String 类型，性能会有所下降。
2. `tip`: `rich-text` 组件内屏蔽所有节点的事件。
3. `tip`: attrs 属性不支持 id ，支持 class 。
4. `tip`: name 属性大小写不敏感。
5. `tip`: 如果使用了不受信任的HTML节点，该节点及其所有子节点将会被移除。
6. `tip`: img 标签仅支持网络图片。
7. `tip`: 如果在自定义组件中使用 `rich-text` 组件，那么仅自定义组件的 wxss 样式对 `rich-text` 中的 class 生效。

### Button

按钮。

| 属性                   | 类型        | 默认值       | 必填 | 说明                                                         | 最低版本                                                     |
| :--------------------- | :---------- | :----------- | :--- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| size                   | string      | default      | 否   | 按钮的大小                                                   | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| type                   | string      | default      | 否   | 按钮的样式类型                                               | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| plain                  | boolean     | false        | 否   | 按钮是否镂空，背景色透明                                     | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| disabled               | boolean     | false        | 否   | 是否禁用                                                     | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| loading                | boolean     | false        | 否   | 名称前是否带 loading 图标                                    | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| form-type              | string      |              | 否   | 用于 [form](https://developers.weixin.qq.com/miniprogram/dev/component/form.html) 组件，点击分别会触发 [form](https://developers.weixin.qq.com/miniprogram/dev/component/form.html) 组件的 submit/reset 事件 | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| open-type              | string      |              | 否   | 微信开放能力                                                 | [1.1.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| hover-class            | string      | button-hover | 否   | 指定按钮按下去的样式类。当 `hover-class="none"` 时，没有点击态效果 | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| hover-stop-propagation | boolean     | false        | 否   | 指定是否阻止本节点的祖先节点出现点击态                       | [1.5.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| hover-start-time       | number      | 20           | 否   | 按住后多久出现点击态，单位毫秒                               | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| hover-stay-time        | number      | 70           | 否   | 手指松开后点击态保留时间，单位毫秒                           | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| lang                   | string      | en           | 否   | 指定返回用户信息的语言，zh_CN 简体中文，zh_TW 繁体中文，en 英文。 | [1.3.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| session-from           | string      |              | 否   | 会话来源，open-type="contact"时有效                          | [1.4.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| send-message-title     | string      | 当前标题     | 否   | 会话内消息卡片标题，open-type="contact"时有效                | [1.5.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| send-message-path      | string      | 当前分享路径 | 否   | 会话内消息卡片点击跳转小程序路径，open-type="contact"时有效  | [1.5.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| send-message-img       | string      | 截图         | 否   | 会话内消息卡片图片，open-type="contact"时有效                | [1.5.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| app-parameter          | string      |              | 否   | 打开 APP 时，向 APP 传递的参数，open-type=launchApp时有效    | [1.9.5](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| show-message-card      | boolean     | false        | 否   | 是否显示会话内消息卡片，设置此参数为 true，用户进入客服会话会在右下角显示"可能要发送的小程序"提示，用户点击后可以快速发送小程序消息，open-type="contact"时有效 | [1.5.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| bindgetuserinfo        | eventhandle |              | 否   | 用户点击该按钮时，会返回获取到的用户信息，回调的detail数据与[wx.getUserInfo](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/user-info/wx.getUserInfo.html)返回的一致，open-type="getUserInfo"时有效 | [1.3.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| bindcontact            | eventhandle |              | 否   | 客服消息回调，open-type="contact"时有效                      | [1.5.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| bindgetphonenumber     | eventhandle |              | 否   | 获取用户手机号回调，open-type=getPhoneNumber时有效           | [1.2.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| binderror              | eventhandle |              | 否   | 当使用开放能力时，发生错误的回调，open-type=launchApp时有效  | [1.9.5](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| bindopensetting        | eventhandle |              | 否   | 在打开授权设置页后回调，open-type=openSetting时有效          | [2.0.7](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| bindlaunchapp          | eventhandle |              | 否   | 打开 APP 成功的回调，open-type=launchApp时有效               | [2.4.4](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |

#### **size 的合法值**

| 值      | 说明     | 最低版本 |
| :------ | :------- | :------- |
| default | 默认大小 |          |
| mini    | 小尺寸   |          |

#### **type 的合法值**

| 值      | 说明 | 最低版本 |
| :------ | :--- | :------- |
| primary | 绿色 |          |
| default | 白色 |          |
| warn    | 红色 |          |

#### **form-type 的合法值**

| 值     | 说明     | 最低版本 |
| :----- | :------- | :------- |
| submit | 提交表单 |          |
| reset  | 重置表单 |          |

#### **open-type 的合法值**

| 值             | 说明                                                         | 最低版本                                                     |
| :------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| contact        | 打开客服会话，如果用户在会话中点击消息卡片后返回小程序，可以从 bindcontact 回调中获得具体信息，[具体说明](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/customer-message/customer-message.html) （*小程序插件中不能使用*） | [1.1.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| share          | 触发用户转发，使用前建议先阅读[使用指引](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/share.html#使用指引) | [1.2.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| getPhoneNumber | 获取用户手机号，可以从bindgetphonenumber回调中获取到用户信息，[具体说明](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/getPhoneNumber.html) （*小程序插件中不能使用*） | [1.2.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| getUserInfo    | 获取用户信息，可以从bindgetuserinfo回调中获取到用户信息 （*小程序插件中不能使用*） | [1.3.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| launchApp      | 打开APP，可以通过app-parameter属性设定向APP传的参数[具体说明](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/launchApp.html) | [1.9.5](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| openSetting    | 打开授权设置页                                               | [2.0.7](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| feedback       | 打开“意见反馈”页面，用户可提交反馈内容并上传[日志](https://developers.weixin.qq.com/miniprogram/dev/api/base/debug/wx.getLogManager.html)，开发者可以登录[小程序管理后台](https://mp.weixin.qq.com/)后进入左侧菜单“客服反馈”页面获取到反馈内容 | [2.1.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |

**lang 的合法值**

| 值    | 说明     | 最低版本 |
| :---- | :------- | :------- |
| en    | 英文     |          |
| zh_CN | 简体中文 |          |
| zh_TW | 繁体中文 |          |

#### Bug & Tip

1. `tip`: `button-hover` 默认为`{background-color: rgba(0, 0, 0, 0.1); opacity: 0.7;}`
2. `tip`: `bindgetphonenumber` 从1.2.0 开始支持，但是在1.5.3以下版本中无法使用[wx.canIUse](https://developers.weixin.qq.com/miniprogram/dev/api/base/wx.canIUse.html)进行检测，建议使用基础库版本进行判断。
3. `tip`: 在`bindgetphonenumber` 等返回加密信息的回调中调用 [wx.login](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.login.html) 登录，可能会刷新登录态。此时服务器使用 code 换取的 sessionKey 不是加密时使用的 sessionKey，导致解密失败。建议开发者提前进行 `login`；或者在回调中先使用 `checkSession` 进行登录态检查，避免 `login` 刷新登录态。
4. `tip`: 从 2.1.0 起，button 可作为原生组件的子节点嵌入，以便在原生组件上使用 `open-type` 的能力。
5. `tip`: 目前设置了 `form-type` 的 `button` 只会对当前组件中的 `form` 有效。因而，将 `button` 封装在自定义组件中，而 `form` 在自定义组件外，将会使这个 `button` 的 `form-type` 失效

![image-20210712164238023](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712164238023.png)

### icon

图标。组件属性的长度单位默认为px，[2.4.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)起支持传入单位(rpx/px)。

| 属性  | 类型          | 默认值 | 必填 | 说明                                                         | 最低版本                                                     |
| :---- | :------------ | :----- | :--- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| type  | string        |        | 是   | icon的类型，有效值：success, success_no_circle, info, warn, waiting, cancel, download, search, clear | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| size  | number/string | 23     | 否   | icon的大小                                                   | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| color | string        |        | 否   | icon的颜色，同css的color                                     | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |



### radio

单选项目。

| 属性     | 类型    | 默认值  | 必填 | 说明                                                         | 最低版本                                                     |
| :------- | :------ | :------ | :--- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| value    | string  |         | 否   | [radio](https://developers.weixin.qq.com/miniprogram/dev/component/radio.html) 标识。当该[radio](https://developers.weixin.qq.com/miniprogram/dev/component/radio.html) 选中时，[radio-group](https://developers.weixin.qq.com/miniprogram/dev/component/radio-group.html) 的 change 事件会携带[radio](https://developers.weixin.qq.com/miniprogram/dev/component/radio.html)的value | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| checked  | boolean | false   | 否   | 当前是否选中                                                 | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| disabled | boolean | false   | 否   | 是否禁用                                                     | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| color    | string  | #09BB07 | 否   | radio的颜色，同css的color                                    | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |

#### radio-group

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。

单项选择器，内部由多个 [radio](https://developers.weixin.qq.com/miniprogram/dev/component/radio.html) 组成。

| 属性       | 类型        | 默认值 | 必填 | 说明                                                         | 最低版本                                                     |
| :--------- | :---------- | :----- | :--- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| bindchange | EventHandle |        | 否   | [radio-group](https://developers.weixin.qq.com/miniprogram/dev/component/radio-group.html)中选中项发生改变时触发 change 事件，detail = {value:[选中的radio的value的数组]} | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |

### checkbox

多选项目。

| 属性     | 类型    | 默认值  | 必填 | 说明                                                         | 最低版本                                                     |
| :------- | :------ | :------ | :--- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| value    | string  |         | 否   | [checkbox](https://developers.weixin.qq.com/miniprogram/dev/component/checkbox.html)标识，选中时触发[checkbox-group](https://developers.weixin.qq.com/miniprogram/dev/component/checkbox-group.html)的 change 事件，并携带 [checkbox](https://developers.weixin.qq.com/miniprogram/dev/component/checkbox.html) 的 value | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| disabled | boolean | false   | 否   | 是否禁用                                                     | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| checked  | boolean | false   | 否   | 当前是否选中，可用来设置默认选中                             | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| color    | string  | #09BB07 | 否   | checkbox的颜色，同css的color                                 | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |

#### checkbox-group

> 基础库 1.0.0 开始支持，低版本需做[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。

多项选择器，内部由多个[checkbox](https://developers.weixin.qq.com/miniprogram/dev/component/checkbox.html)组成。

| 属性       | 类型        | 默认值 | 必填 | 说明                                                         | 最低版本                                                     |
| :--------- | :---------- | :----- | :--- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| bindchange | EventHandle |        | 否   | [checkbox-group](https://developers.weixin.qq.com/miniprogram/dev/component/checkbox-group.html)中选中项发生改变时触发 change 事件，detail = {value:[选中的checkbox的value的数组]} | [1.0.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |

## 自定义组件

### 创建自定义组件

```
1.创建新的文件夹 components（由四个文件组成：.json，.wxml，.js，.wxss）
2.新建component文件可以直接创建四个格式后缀的文件
3.在需要引入的组件的文件中的配置文件（.json）中“usingComponents”：{“创建组件定义的名称”：“组件的相对路径”}
4.在（.wxml）页面中写入<定义的组件的名称></定义的组件的名称>即可使用自定的组件
```

  点击跳转

![image-20210712172647314](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712172647314.png)

![image-20210712172842710](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712172842710.png)

![image-20210712173052151](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712173052151.png)

### 子父传数据

```
父----->子		通过标签的属性
<Tabs aaa="123123"></Tabs>
```

![image-20210712173307560](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712173307560.png)

![image-20210712173415328](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712173415328.png)

![](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712173521431.png)

![image-20210712173556404](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210712173556404.png)

## 小程序的生命周期

### 应用生命周期

| 属性           | 类型     | 默认值 | 必填 | 说明                   |
| -------------- | -------- | ------ | ---- | ---------------------- |
| onLaunch       | function |        | 否   | 监听小程序初始化       |
| onShow         | function |        | 否   | 监听小程序启动或且前台 |
| onHide         | function |        | 否   | 监听小程序且后台       |
| onError        | function |        | 否   | 错误监听函数           |
| onPageNotFound | function |        | 否   | 页面不存在监听函数     |



### 页面生命周期

| 属性              | 类型     | 说明                             |
| ----------------- | -------- | -------------------------------- |
| data              | object   | 页面初始数据                     |
| onLoad            | function | 生命周回调---监听页面加载        |
| onShow            | function | 生命周回调--监听页面显示         |
| onReady           | function | 生命周回调--监听页面初次渲染完成 |
| onHide            | function | 生命周回调--监听页面隐藏         |
| onUnload          | function | 生命周回调--监听页面卸载         |
| onPullDownRefresh | function | 监听用户下拉动作                 |
| onReachBottom     | function | 页面上拉触底事件的处理函数       |
| onShareAppMessage | function | 用户点击右上角转发               |
| onPageScroll      | function | 页面滚动出发事件的处理函数       |
| onResize          | function | 页面改变尺寸时触发               |
| onTTabItemTap     | function | 当前是tab时，点击tab触发         |

