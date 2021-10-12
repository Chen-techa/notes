将本地文件提交到gitee

```
mkdir web_shop //创建项目文件
cd web_shop //切换到项目
git init  //创建本地仓库
touch README.md  //创建README文件
git add .//将文件暂存到本地仓库
git add README.md  //将README文件添加到git仓库中
git commit -m "first commit"   //初始化仓库信息
git remote add origin https://gitee.com/a17502248584/web_shop.git    //提交仓库
git push -u origin master  //提交分支
```

后续推送续写的代码

```
git add .  //将自己重新编辑的代码先提交到本地仓库
git commit -m '（写入自己代码进行到什么程度 ，可以用中文）'
git push -u origin 分支名（分支名可以自己创建） //提交到分支
```

将GitHub或者gitee的代码复制到本地

```
git clone 复制的地址 //复制完成后，安装代码运行的依赖包的命令 例如vue项目可以使用npm i
```

