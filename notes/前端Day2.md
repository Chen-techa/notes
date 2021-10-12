## 前端Day2(SASS)

### 概念：

   1.css的扩展语言，本质上是脚本编程语言，通过sass所有的特点提高编写css代码的效率。即，用部分的sass代码替代之前繁琐的css代码

   2.  sass底层是由面向对象的语言ruby来编写的（了解）

### 安装：

	1. 先安装ruby再通过npm安装sass
	2. 使用vscode提供的插件 essay sass 快速的入手sass

## 基础语法

### 使用：

1. sass需要放在以.sass .scss为后缀的文件之中

2. 在vscode中setting中设置sass文件转为css文件相关的配置信息

3. ```
   {
   	//保存scss代码后转为css
   	"easysass.compileAfterSave": true
   	//指定什么格式转为css代码
   	"easysass.formats":[
   		{
   			"format":"expanded",
   			"extension": "css"
   		},
   		{
   			"format":"compressed",
   			"extension": ".min.css"
   		}
   	],
   	"easysass.targetDir": "css/"
   }
   ```

   

### 嵌套：

1. 概念：可以标签样式代码里继续对其子标签设置样式

2. 作用：让css代码中标签的层次更加清晰明了。解决了可能权重的问题。

3. ```scss
   #box{
   	color：yellow；
   	p{
   		color：blue；
   		span{
   			color：red；
   		}
   	}
   }
   //转为css后
   #box{
   	color：yellow；
   }
   #box p{
   	color：blue；
   }
   #box p span {
   	color：red；
   }
   ```

   ### 变量：

   1. 概念：变量是一种存放css属性值的容器，一个变量可以保存一个样式属性值，定义的变量可以重复使用。类似于姓名。

   2. 作用：解决重复样式的繁琐修改问题

   3. 使用

      定义一个变量（只需要定义一次，可以多次使用）

      ```
      $变量名：css属性值；
      ```

      运用变量：

      ```sc
      css属性名：$变量名；
      ```

      例子：

      ```scss
      //定义变量BColor=red，用于header，main，footer三个标签
      $BColor：red；
      header{
      	background-color：$BColor；
      }
      main:{
      	background-color：$BColor；
      }
      footer:{
      	background-color：$BColor；
      }
      
      
      //转css之后
      header{
      	background-color：red;
      }
      footer{
      	background-color：red;
      }
      main{
      	background-color：red;
      }
      ```

   4. 定义变量的位置

         如果需要变量整个scss文件都可以使用，就在页面的开头定义变量。

         如果需要使用局部的变量，就在使用范围内定义变量。

         ```scss
         //scss文件开头：
         $BColor:red;//该变量整个文件都可已使用
         
         header{
             $textColor:red;//该变量职能制header中使用
         } 
         ```

   5. 变量的命名规范：

            变量可以包含数字，字母，
            
            尽量不要使用数字开头
            
            多个单词尽量以-间隔

