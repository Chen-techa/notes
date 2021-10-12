### Laravel5.7

#### 一、使用Git Clone将项目复制到新的开发环境中

1.首先在原始文件夹中（假设现在使用的master分支）我们需要推送项目到Git中

```git
//以码云为例 网址：http://gitee.com
git add . //将代码暂存到本地仓库
git commit -m '初始化本地仓库'//提交信息
gti remote add origin https://gitee.com/user/entrepot.git   //entrepot是仓库的意思 //user则为用户在gitee的用户名
git push -u origin master
```

2.从Gitee上复制下来项目

```
git clone https://gitee.com/user/entrepot.git
```

3.接下来我们需要进行composer install来解决dependencies：

```
composer install
```

4.完成后，我们需要建立.env文件，因为.env默认是gitee所忽略的文件：

```
cp .env.example .env
```

5.因为env.example中默认没有app key，所以我们在.env中生成新的app key：

```
php artisan key:generate
```

6.修改.env文件

```
DB_CONNECTION=mysql //链接数据库
DB_HOST=10.10.102.92 //IP地址
DB_PORT=3306 //数据库端口号
DB_DATABASE=webshop //数据库名称
DB_USERNAME=root //数据库用户名
DB_PASSWORD=root //数据库密码
```

7.保存后，运行

```
php artsian migrate
```



#### 二、app==>Http==>

主要为控制器的存放

新建控制器的命令为:

```php
php artisan make:controller PhpController//在控制器的跟目录下新建一个控制器
```



```php
php artsian make:controller filer/PhpController //在指定文件目录下新建一个控制器
```

#### 三、resources==>views(为视图存放目录,界面显示)

新建的视图后缀名需要是 index.blade.php

主页页面结构：

```php
@extends('frame')//frame为继承模板
@section('style')//引入的style的样式
@endsection

@section('content')//界面主要内容
@endsection

@section('script')//js脚本
@endsection
```

#### 四、引入外部js文件的方式

在project==》public ==》 js(文件顺序)

```php
@section('script')//js脚本
	<scritp src="{{URL::asset(js/javascritp.js)}}"></script>//举例
    <scritp src="http://xxx.xxx.xxx"></script>//根据网址引入的js
@endsection
//css的引入方法大致同上
```

#### 五、主界面点击模块跳转到对应的页面

project==>routes==>web.php

```php
Route::prefix('/admin')->group(function(){ //成组
	Route::get('/shoplist',function(){ 
		return view('shoplist');//返回对应的视图
	})->name('shoplist');
})
```

模板frome的跳转方法

```php+HTML
//在模板下写入
<ul>
    <li class="<?php
        if(stripos($_SERVER['REQUSET_URI'],'admin/shoplist') != false) echo 'active'?>">
    	<a href="/admin/shoplist">
   			商品信息
        </a>
    </li>
</ul>
```

#### 六、在phpstudy_pro中搭建网站环境的注意项：

在project==》public==》.htaccess

1.首先复制一份.htaccess文件

2.在phpstudy中搭建网址:

```
www.shoppping.com:80 //默认端口为80端口，若修改在进入浏览器之后则需要在网址后缀中添加所修改的端口号
//搭建网址的目录中不可汉中文
```

3.再次打开.htaccess文件 将复制的.htaccess文件中的内容重新复制到.htaccess文件中