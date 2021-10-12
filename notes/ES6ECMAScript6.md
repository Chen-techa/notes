### ES6ECMAScript6(Day1)

#### const关键字

const关键字用于定义常量（一旦定义无法改变的变量，通常是表示一些固定不变的数据）

使用const 的特点

1. 无法修改

2.  支持块作用域

3.  无法重复定义

4.  无法声明前置

5.  不能被windows挂载

6. 不能作为for循环体中的变量使用

7. 值只能是值类型，如果是引用类型则可以被修改

8. 示例：

   ```js
   const number = 42;
   
   try {
     number = 99;
   } catch (err) {
     console.log(err);
     // expected output: TypeError: invalid assignment to const `number'
     // Note - error messages will vary depending on browser
   }
   
   console.log(number);
   // expected output: 42
   ```

   

#### 语法：

```js
const name1 = value1 [, name2 = value2 [, ... [, nameN = valueN]]];
//nameN
//常量名称，可以是任意合法的标识符。
//valueN
//常量值，可以是任意合法的表达式。
```

#### 描述

此声明创建一个常量，其作用域可以是全局或本地声明的块。 与`var`变量不同，全局常量不会变为 window 对象的属性。需要一个常数的初始化器；也就是说，您必须在声明的同一语句中指定它的值（这是有道理的，因为以后不能更改）。

**`const`****声明**创建一个值的只读引用。但这并不意味着它所持有的值是不可变的，只是变量标识符不能重新分配。例如，在引用内容是对象的情况下，这意味着可以改变对象的内容（例如，其参数）。

关于“[暂存死区](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/let#temporal_dead_zone_and_errors_with_let)”的所有讨论都适用于`let`和`const`。

一个常量不能和它所在作用域内的其他变量或函数拥有相同的名称。

#### 示例：

#### 基本用法：

```js
// 定义常量MY_FAV并赋值7
const MY_FAV = 7;

// 报错 - Uncaught TypeError: Assignment to constant variable.
MY_FAV = 20;

// MY_FAV is 7
console.log('my favorite number is: ' + MY_FAV);

// 尝试重新声明会报错
// Uncaught SyntaxError: Identifier 'MY_FAV' has already been declared
const MY_FAV = 20;

// MY_FAV 保留给上面的常量，这个操作会失败
var MY_FAV = 20;

// 也会报错
let MY_FAV = 20;


```

#### 块作用域：

注意块作用域的性质很重要

```js
if (MY_FAV === 7) {
  // 没问题，并且创建了一个块作用域变量 MY_FAV
  // (works equally well with let to declare a block scoped non const variable)
  let MY_FAV = 20

  // MY_FAV 现在为 20
  console.log('my favorite number is ' + MY_FAV);

  // 这被提升到全局上下文并引发错误
  var MY_FAV = 20;
}

// MY_FAV 依旧为7
console.log('my favorite number is ' + MY_FAV);

```

#### 常量需要一个初始值

```js
// 报错
// Uncaught SyntaxError: Missing initializer in const declaration

const FOO;

```

#### 常量可以定义为对象或者数组：

```js
const MY_OBJECT = {'key': 'value'};

// 重写对象和上面一样会失败
// Uncaught TypeError: Assignment to constant variable.
MY_OBJECT = {'OTHER_KEY': 'value'};

// 对象属性并不在保护的范围内
// 下面这个声明会成功执行
MY_OBJECT.key = 'otherValue'; // Use Object.freeze() to make object immutable

// 也可以用来定义数组
const MY_ARRAY = [];
// 可以向数组填充数据
MY_ARRAY.push('A'); // ["A"]
// 但是，将一个新数组赋给变量会引发错误
// Uncaught TypeError: Assignment to constant variable.
MY_ARRAY = ['B'];
```

