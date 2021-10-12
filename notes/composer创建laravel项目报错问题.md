composer创建laravel项目报错问题

![composer报错信息](C:\Users\91790\Desktop\composer报错信息.png)

若显示如图的报错信息，则需要更换composer镜像源

之前用的是composer中国镜像，地址：

```
https://pkg.phpcomposer.com/#how-to-install-composer
```

换成阿里镜像后成功创建laravel项目

![image-20210708151656481](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210708151656481.png)

阿里镜像地址：

```
https://developer.aliyun.com/article/726948spm=a2c6h.14164896.0.0.6f8a791fPW7fDO
```

阿里镜像（切换）

```
composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/
```

切换之后可以使用

```
composer config -gl
```

来查看镜像地址

![image-20210708152013277](C:\Users\91790\AppData\Roaming\Typora\typora-user-images\image-20210708152013277.png)

注：切换镜像需要安装composer

