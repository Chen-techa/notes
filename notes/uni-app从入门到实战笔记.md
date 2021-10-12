# uni-app从入门到实战笔记

## uni-app基础部分

### uni-app介绍

`		uni-app`是一个使用`Vue.js`开发的前端应用框架，开发者编写一套代码，可以发布到`ios`,`andorid`,`H5`,以及各种小程序的应用（微信/支付宝/百度/头条/QQ）等。

### globalstyle全局外观设置

|             属性             | 类型     | 默认值   | 描述                                                         | 平台差异说明                                     |
| :--------------------------: | :------- | :------- | :----------------------------------------------------------- | :----------------------------------------------- |
| navigationBarBackgroundColor | HexColor | #F7F7F7  | 导航栏背景颜色（同状态栏背景色）                             | APP与H5为#F7F7F7，小程序平台请参考相应小程序文档 |
|    navigationBarTextStyle    | String   | white    | 导航栏标题颜色及状态栏前景颜色，仅支持 black/white           |                                                  |
|    navigationBarTitleText    | String   |          | 导航栏标题文字内容                                           |                                                  |
|       navigationStyle        | String   | default  | 导航栏样式，仅支持 default/custom。custom即取消默认的原生导航栏，需看[使用注意](https://uniapp.dcloud.io/collocation/pages?id=customnav) | 微信小程序 7.0+、百度小程序、H5、App（2.0.3+）   |
|       backgroundColor        | HexColor | #ffffff  | 下拉显示出来的窗口的背景色                                   | 微信小程序                                       |
|     backgroundTextStyle      | String   | dark     | 下拉 loading 的样式，仅支持 dark / light                     | 微信小程序                                       |
|    enablePullDownRefresh     | Boolean  | false    | 是否开启下拉刷新，详见[页面生命周期](https://uniapp.dcloud.io/collocation/frame/lifecycle?id=页面生命周期)。 |                                                  |
|    onReachBottomDistance     | Number   | 50       | 页面上拉触底事件触发时距页面底部距离，单位只支持px，详见[页面生命周期](https://uniapp.dcloud.io/collocation/frame/lifecycle?id=页面生命周期) |                                                  |
|      backgroundColorTop      | HexColor | #ffffff  | 顶部窗口的背景色（bounce回弹区域）                           | 仅 iOS 平台                                      |
|    backgroundColorBottom     | HexColor | #ffffff  | 底部窗口的背景色（bounce回弹区域）                           | 仅 iOS 平台                                      |
|          titleImage          | String   |          | 导航栏图片地址（替换当前文字标题），支付宝小程序内必须使用https的图片链接地址 | 支付宝小程序、H5、APP                            |
|       transparentTitle       | String   | none     | 导航栏整体（前景、背景）透明设置。支持 always 一直透明 / auto 滑动自适应 / none 不透明 | 支付宝小程序、H5、APP                            |
|        titlePenetrate        | String   | NO       | 导航栏点击穿透                                               | 支付宝小程序、H5                                 |
|       pageOrientation        | String   | portrait | 横屏配置，屏幕旋转设置，仅支持 auto / portrait / landscape 详见 [响应显示区域变化](https://developers.weixin.qq.com/miniprogram/dev/framework/view/resizable.html) | App 2.4.7+、微信小程序                           |
|        animationType         | String   | pop-in   | 窗口显示的动画效果，详见：[窗口动画](https://uniapp.dcloud.io/api/router?id=animation) | App                                              |
|      animationDuration       | Number   | 300      | 窗口显示动画的持续时间，单位为 ms                            | App                                              |
|           app-plus           | Object   |          | 设置编译到 App 平台的特定样式，配置项参考下方 [app-plus](https://uniapp.dcloud.io/collocation/pages?id=app-plus) | App                                              |
|              h5              | Object   |          | 设置编译到 H5 平台的特定样式，配置项参考下方 [H5](https://uniapp.dcloud.io/collocation/pages?id=h5) | H5                                               |
|          mp-alipay           | Object   |          | 设置编译到 mp-alipay 平台的特定样式，配置项参考下方 [MP-ALIPAY](https://uniapp.dcloud.io/collocation/pages?id=mp-alipay) | 支付宝小程序                                     |
|          mp-weixin           | Object   |          | 设置编译到 mp-weixin 平台的特定样式                          | 微信小程序                                       |
|           mp-baidu           | Object   |          | 设置编译到 mp-baidu 平台的特定样式                           | 百度小程序                                       |
|          mp-toutiao          | Object   |          | 设置编译到 mp-toutiao 平台的特定样式                         | 字节跳动小程序                                   |
|            mp-qq             | Object   |          | 设置编译到 mp-qq 平台的特定样式                              | QQ小程序                                         |
|         mp-kuaishou          | Object   |          | 设置编译到 mp-kuaishou 平台的特定样式                        | 快手小程序                                       |
|       usingComponents        | Object   |          | 引用小程序组件，参考 [小程序组件](https://uniapp.dcloud.io/frame?id=小程序组件支持) |                                                  |
|        renderingMode         | String   |          | 同层渲染，webrtc(实时音视频) 无法正常时尝试配置 seperated 强制关掉同层 | 微信小程序                                       |
|          leftWindow          | Boolean  | true     | 当存在 leftWindow 时，默认是否显示 leftWindow                | H5                                               |
|          topWindow           | Boolean  | true     | 当存在 topWindow 时，默认是否显示 topWindow                  | H5                                               |
|         rightWindow          | Boolean  | true     | 当存在 rightWindow 时，默认是否显示 rightWindow              | H5                                               |
|    rpxCalcMaxDeviceWidth     | Number   | 960      | rpx 计算所支持的最大设备宽度，单位 px                        | App、H5（2.8.12+）                               |
|    rpxCalcBaseDeviceWidth    | Number   | 375      | rpx 计算使用的基准设备宽度，设备实际宽度超出 rpx 计算所支持的最大设备宽度时将按基准宽度计算，单位 px | App、H5（2.8.12+）                               |
|     rpxCalcIncludeWidth      | Number   | 750      | rpx 计算特殊处理的值，始终按实际的设备宽度计算，单位 rpx     | App、H5（2.8.12+）                               |
|           maxWidth           | Number   |          | 单位px，当浏览器可见区域宽度大于maxWidth时，两侧留白，当小于等于maxWidth时，页面铺满；不同页面支持配置不同的maxWidth；maxWidth = leftWindow(可选)+page(页面主体)+rightWindow(可选) | H5（2.9.9+）                                     |

### 创建新的页面和页面配置

​		在pages文件当中新建文件`message(以message为例)`，在`message`文件夹当中新建`.vue`文件，在pages.json文件中，添加页面路径（第一位）即可显示新建的页面文件。 

### 项目目录介绍

`pages`用来存放uni-app页面

`static`存放静态资源`图片`,`视频`,`字体图标`

`unpackage`用来存放最终的打包输出文件

`App.vue`项目的更跟组件，是页面的入口文件，可以调用生命周期函数

`main.js`项目的入口文件，主要作用是初始化`vue`实例并使用所需要的插件

`manifest.json`文件是，配置文件，用于指定的名称、图标、权限

`pages.json`文件用来对uni-app进行全局配置，决定页面文件的路径、窗口样式、原生的导航栏、底部原生tabbar等。

`uni.scss`文件的用途是为了方便整体控制应用的风格。比如：按钮颜色、边框风格。`uni-app`文件预置了一批scss变量预置

`components`组件存放目录

### 开发规范

`开发规范`:页面文件遵循Vue当文件组件、组件标签靠近小程序规范、接口能力靠近小程序规范、数据绑定事件处理靠近Vue、为兼容多端运行，使用flex布局进行开发

### tabbar

如果应用是一个多tab应用，可以通过tabbar来配置对应的tab页

**Tips**

- 当设置position为top时，将不会显示icon（设置top时，只能在微信小程序显示）
- tabbar中list是一个数组，只能配置最少两个，最多五个tab，tab按数组的顺序排队

### condititon启动模式配置

启动模式配置，仅在开发模式直达页面场景，如：小程序转发后，用户点开指定的页面。

#### 属性说明

| 属性    | 类型   | 是否必填 | 描述                             |
| ------- | ------ | -------- | -------------------------------- |
| current | Number | true     | 当前激活的模式，list节点的索引值 |
| list    | Array  | true     | 启动模式列表                     |

#### list说明

| 属性  | 类型   | 是否必填 | 描述                                   |
| ----- | ------ | -------- | -------------------------------------- |
| name  | String | ture     | 启动模式名称                           |
| path  | String | true     | 启动页面路径                           |
| query | String | false    | 启动参数，可在也买你的onLoad函数中获得 |

###  组件的基本使用

#### text组件的基本使用

| 属性       | 类型    | 默认值 | 必填  | 描述                                         |
| ---------- | ------- | ------ | ----- | -------------------------------------------- |
| selectable | boolean | false  | false | 文本是否可选                                 |
| space      | string  |        | false | 显示连线空格，可选参数：`ensp`,`emsp`,`nbsp` |
| decode     | boolean | false  | false | 是否解码                                     |

- `text`组件相当于行内标签，在同一行显示
- 除文本节点以外的其他节点都无法长安选中

#### view组件的基本使用

| 属性                   | 类型    | 默认值 | 必填  | 说明                                                       |
| ---------------------- | ------- | ------ | ----- | ---------------------------------------------------------- |
| hover-class            | string  | none   | false | 指定按下去的样式类，当`hover-class=”none“时`，没有点击效果 |
| hover-stop-propagation | boolean | false  | false | 指定是否阻止本节点出现点击态                               |
| hover-start-tiem       | number  | 50     | false | 按住多久会出现点击态，单位毫秒                             |
| hover-stay-time        | number  | 400    | false | 手指松开点击态保留时间，单位毫秒                           |

- 块级组件，相当于html中的div标签

#### button组件的基本使用

| 属性     | 类型    | 默认值  | 说明                     |
| -------- | ------- | ------- | ------------------------ |
| size     | String  | default | 按钮大小                 |
| type     | String  | default | 按钮的样式类型           |
| plain    | Boolean | false   | 按钮是否镂空，背景色透明 |
| disabled | Boolean | false   | 是否按钮                 |
| loading  | Boolean | false   | 名称是否带Loading图标    |

- `button`组件默认独占一行，设置`size`为`mini`时可以在一行显示多个

#### image组件的基本使用

| 属性名                 | 类型        | 默认值        | 说明                                                         | 平台差异说明                           |
| :--------------------- | :---------- | :------------ | :----------------------------------------------------------- | :------------------------------------- |
| src                    | String      |               | 图片资源地址                                                 |                                        |
| mode                   | String      | 'scaleToFill' | 图片裁剪、缩放的模式                                         |                                        |
| lazy-load              | Boolean     | false         | 图片懒加载。只针对page与scroll-view下的image有效             | 微信小程序、百度小程序、字节跳动小程序 |
| fade-show              | Boolean     | true          | 图片显示动画效果                                             | 仅App-nvue 2.3.4+ Android有效          |
| webp                   | boolean     | false         | 默认不解析 webP 格式，只支持网络资源                         | 微信小程序2.9.0                        |
| show-menu-by-longpress | boolean     | false         | 开启长按图片显示识别小程序码菜单                             | 微信小程序2.7.0                        |
| draggable              | boolean     | true          | 鼠标长按是否能拖动图片                                       | 仅 H5 平台 3.1.1+ 有效                 |
| @error                 | HandleEvent |               | 当错误发生时，发布到 AppService 的事件名，事件对象event.detail = {errMsg: 'something wrong'} |                                        |
| @load                  | HandleEvent |               | 当图片载入完毕时，发布到 AppService 的事件名，事件对象event.detail = {height:'图片高度px', width:'图片宽度px'} |                                        |

**Tips**

- `<image>` 组件默认宽度 300px、高度 225px；`app-nvue平台，暂时默认为屏幕宽度`
- `src` 仅支持相对路径、绝对路径，支持 base64 码；
- 页面结构复杂，css样式太多的情况，使用 image 可能导致样式生效较慢，出现 “闪一下” 的情况，此时设置 `image{will-change: transform}` ,可优化此问题。
- 自定义组件里面使用 `<image>`时，若 `src` 使用相对路径可能出现路径查找失败的情况，故建议使用绝对路径。
- webp格式的图片在Android上是内置支持的。iOS上不同平台不一样，具体如下：app-vue下，iOS不支持；app-nvue下，iOS支持；微信小程序2.9.0起，iOS支持。
- svg 格式的图片在不同的平台支持情况不同。具体为：app-nvue 不支持 svg 格式的图片，小程序上只支持网络地址。

### uni-app中使用scss和字体图标



### 数据的基本绑定



### v-bind和v-for



### 注册事件和传递参数以及获取到的事件队象



### 生命周期



### 下拉刷新和上拉加载



### 发送get请求



### 数据缓存



### 图片的上传和预览



### 条件编译跨端兼容



### 两种方式导航跳转和传参



### 组件的创建使用和组件的生命周期



### 组件之间的通讯方式



### 组件库的基本使用和介绍





## uni-app项目部分