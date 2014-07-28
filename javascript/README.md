javascript
==========

## JavaScript 简介
略


## JavaScript 简单实例
略


## JavaScript 基本语法

JavaScript 语言是区分大小写的，不管是命名变量还是使用关键字的时候。

大多数情况下，JavaScript 忽略空白或者 JavaScript 语句之间的空格（也包括 Tab 键产生的空白缩进）。

js变量的声明:  
>  var 变量名;

js中可以同时赋值多个变量:

```javascript
    var a=2 , b =12;
    alert(a);
```



## JavaScript 数据类型
JavaScript 主要有如下 6 种数据类型：

1. 字符串（String）类型: 字符串类型使用双引号 " 或单引号 ' 括起来
2. 数值（Number）类型: 数值（Number）类型包括整数和浮点数（包含小数点的数或科学记数法的数）
3. 布尔（Boolean）类型
4. 空值（Null）: 空值类型表示该变量或内容无任何值
5. 未定义（Undefined）类型: 变量被创建后，未给该变量赋值，该变量即为未定义类型
6. 对象（Object）类型

> JavaScript 是一门松散的语言，甚至可以说是混合语言，因此导致其数据类型以及类型之间的关系比较复杂。另外也有一些人把 function（函数） 列为数据类型之一，对于这些有一定争议的说法



## JavaScript 运算符
JavaScript 运算符主要包括：

1. 算术运算符 : + - * / % ++ --
2. 赋值运算符
3. 比较运算符
4. 三元运算符

```javascript
    x = 2;
    y = (x == 2) ? x : 1;
    alert(y);   //输出：2
```

5. 逻辑运算符: && || !
6. 字符串连接运算符: 连接运算符 + 主要用于连接两个字符串或字符串变量。因此，在对字符串或字符串变量使用该运算符时，并不是对它们做加法计算。

## JavaScript 循环控制

```javascript
var i=1
for (i = 1; i <= 10; i++) {
    document.write(i + "<br />")
}
```



## JavaScript 流程控制
JavaScript for 循环用于反复执行一段代码，其语法如下：

    for (expr1; expr2; expr3){
        statement
    }

for 循环语法解读
. expr1 在循环开始前无条件求值一次
. expr2 在每次循环开始前求值，如果值为 TRUE，则继续循环，执行嵌套的循环语句；如果值为 FALSE，则终止循环。
. expr3 在每次循环之后被求值（执行）
. 每个表达式都可以为空。如果expr2 为空意则将无限循环下去，

```javascript
var i=1
for (i = 1; i <= 10; i++) {
    document.write(i + "<br />")
}
```



## JavaScript 消息提示框

alert(): 

confirm(): 创建一个消息确认框

prompt(): 创建一个消息提示框




## JavaScript 函数
函数是 JavaScript 语言的核心之一，其基本语法如下：

    function functionName(arg0, arg1, ...) {
        statements
    }


__JavaScript 函数参数错误__

JavaScript 函数参数并没有严格要求哪些参数是必选参数，哪些参数是可选参数，因此传入的参数个数是允许不等于定义函数时参数的个数的。
如果在函数中使用了未定义的参数，则会提示语法错误（参数未定义），JavaScript 代码不会正常运行。
如果参数已经定义，但未正确的传入参数时，相关参数值会以 undefined 替换，JavaScript 代码仍正常运行，如下例所示：

```html
<script type="text/javascript">
function hello(name,age){
    document.write("我叫" + name + "，今年" + age + "岁！");
}
</script>
<input type="button" onclick="hello('小明')" value="确定" />
```

> 输出：我叫小明，今年undefined岁！


__JavaScript arguments 对象__

在 JavaScript 函数中，有个特殊的 arguments 对象，它以类似数组的形式保存了当前函数调用的参数。因此，开发者无需定义具体的参数名，就可以方便的访问函数参数：

```html
<script type="text/javascript">
function hello(){
    document.write("我叫" + arguments[0] + "，今年" + arguments[1] + "岁！");
}
</script>
<input type="button" onclick="hello('小明',18)" value="确定" />
```

> 输出：我叫小明，今年18岁！
 
通常在函数定义中，为便于代码的可读性，一般不会使用 arguments 对象。在处理不定数目的参数，或者模拟函数重载时，可方便的使用 arguments 对象来处理。

arguments.length 可以很方便的检测函数的参数个数。  
> document.write(arguments.length);


## JavaScript 事件
## JavaScript 面向对象
## JavaScript 字符串处理(String对象)
## JavaScript 数组
## JavaScript 时间日期(Date 对象)
## JavaScript 数学计算(Math对象)
## JavaScript Boolean 对象
## JavaScript History 对象
## JavaScript Location 对象
## JavaScript Navigator 对象
## JavaScript Screen 对象
## JavaScript Document 对象
## JavaScript Window 对象

