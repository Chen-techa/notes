### Let Const Var的区别

### var

1. var只有函数作用域，没有块作用域，可以声明全局/局部变量（在一共函数内声明的变量，只在该函数有效）
2. var定义的变量不能跨函数访问，但是可以跨块访问！
3. var 定义的变量如果不初始化会输出undefined，但不会报错
4. 可以重复定义，后定义的会覆盖先定义的。

```js
var a;
console.log(a);   //undefined,定义没赋值
//-----------------------------------------
var a = 1;   //全局变量 第一次定义
console.log(a);    // a：1
function A(){
    a=2;
    console.log(a);  //此时之前var a=1的值已经被改变
    
}
A(); //调用A方法
console.log(a);   //调用A函数，a变为函数A内部修改的值：2
//---------------------------------------------
var b=1;
var b=2;
console.log(b);  //2,后面的声明覆盖了前面的声明

```

### const

1. 块级作用域内有效；
2. `const`声明的变量不得改变值，这意味着，const一旦声明变量，就必须立即初始化，不能留到以后赋值。
3. 对于复合类型的变量，如数组和对象，变量名不指向数据，而是指向数据所在的地址。`const`命令只是保证变量名指向的地址不变，并不保证该地址的数据不变，所以将一个对象声明为常量必须非常小心。

```js
const a ;//报错 定义const 之后应该立即赋值
const b = 2;
b = 3//const赋的值不能直接 =
const names = [];
names = [1,2,3] //报错，const赋的值不能直接 = 
```

### let

1. let是块级作用域，函数内部使用let定义后，对函数外部无影响
2. let定义的变量只能在块作用域中访问，不能跨块访问，更不能跨函数访问
3. 不能变量声明提前，否则会报错
4. 不能重复定义，否则会报错

```js
let a =1;
console.log(a); // 全局变量1
function A(){
    let a = 2;
    console.log(a);  //局部变量：2
}
A();
console.log("A()函数调用后，a++");  
//2
var b=1;
{
    let b=2;
    console.log(b);  //  2
}
console.log(b);   //1
 console.log(aaa);
 let aaa=1;   //会进行报错，不能变量声明提前
 let p = 1;
 let p = 2;
 console.log(p);  //重复定义，会报错

```

