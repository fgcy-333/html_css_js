# 一、什么是JavaScript，有什么用？
1、JavaScript是  **运行在浏览器上**   的  `脚本语言`  。简称JS。

2、JavaScript是  **网景公司**（NetScape）的 布兰登艾奇（JavaScript之父）开发的，最初叫做  `LiveScript`。

3、LiveScript的出现让浏览器更加的生动了，不再是单纯的静态页面了。页面更具有交互性。

4、在历史的某个阶段，SUN公司和网景公司他们之间有合作关系，SUN公司把LiveScript的名字修改为JavaScript。

5、JavaScript这个名字中虽然带有“Java”但是和Java没有任何关系，只是  `语法上优点类似 ` 。他们运行的位置不同(Java运行在JVM当中，JavaScript运行在浏览器的内存当中)

6、javascript是一种基于事件驱动型的编程语言,一般都是依靠事件来触发Js代码执行的。



**JavaScript是脚本语言：**

JavaScript程序不需要我们程序员手动编译，编写完源代码之后，浏览器直接打开解释执行。

JavaScript的  `“目标程序”`  以**普通文本形式**保存，这种语言都叫做“脚本语言”。

Java的目标程序以.class形式存在（二进制文件），不能使用文本编辑器打开，不是脚本语言。





**相关历史事件：**

网景公司1998年被美国在线收购。

网景公司最著名的就是领航者浏览器：`Navigator`浏览器。

`LiveScript`的出现，最初的时候是为`Navigator浏览器`量身定制一门语言，不支持其他浏览器。

当Navigator浏览器使用非常广泛的时候，微软害怕了，于是微软在最短的时间内组建了一个团队，
开始研发只支持`  IE浏览器 ` 的`脚本语言`，叫做`JScript`。

JavaScript和JScript并存的年代，程序员是很痛苦的，因为程序员要写两套程序。
在这种情况下，有一个非营利性组织站出来了，叫做  `ECMA组织`（欧洲计算机协会）
ECMA根据JavaScript制定了ECMA-262号标准，叫做`ECMA-Script`。

现代的javascript和jscript都实现了ECMA-Script规范。（javascript和jscript统一了）





**以后大家会学习一个叫做JSP的技术，JSP和JS有啥区别？**

​	JSP : `JavaServer Pages`（隶属于Java语言的，运行在JVM当中，本质上是一个java类servlet，实现了javaee的servlet接口）

​	JS : JavaScript（运行在浏览器上）



# 二、在HTML中怎么嵌入JavaScript代码？
​	三种方式



javascript是一种基于 ` 事件驱动型`  的编程语言,`一般都是依靠事件`来  触发  Js代码执行的。





## 第一种方式（在事件句柄中书写js代码）



1、需求:在页面中有一个按钮,用户点击这个按钮的时候弹出对话框

2、javascript是一种基于事件驱动型的编程语言,一般都是依靠事件来触发Js代码执行的。

​		例如:	

​					鼠标单击事件click。

​					鼠标双击事件:dblclick。

​					获取焦点事件: focus。

​					失去焦点事件: blur



3、在Js当中  **任何一个事件**  都有  对应的  一个  **事件句柄**。所有的事件句柄都是在  事件名称  前面  添加 `on`

例如:

click对应的事件句柄onclick

dbclick对应的事件句柄ondblclick

focus对应的事件句柄是: onfocus

blur对应的事件句柄是:onblur



注意   :   `所有的事件句柄`   都是以  **“标签的属性”**  形式存在。



5、 `onclick后面的js代码`  什么时候执行呢?

`不会在` **页面打开时执行**，只有当有当鼠标单击click事件发生之后才会执行这个JS代码。



例子：

~~~html
<!doctype html>
<html>
	<head>
		<title>HTML中嵌入JS代码的第一种方式</title>
	</head>
	<body>
		
		<!--
			1、要实现的功能：
				用户点击以下按钮，弹出消息框。

			2、JS是一门事件驱动型的编程语言，依靠事件去驱动，然后执行对应的程序。
			在JS中有很多事件，其中有一个事件叫做：鼠标单击，单词：click。并且任何
			事件都会对应一个事件句柄叫做：onclick。【注意：事件和事件句柄的区别是：
			事件句柄是在事件单词前添加一个on。】，而事件句柄是以HTML标签的属性存在
			的。

			3、onclick="js代码"，执行原理是什么？
				页面打开的时候，js代码并不会执行，只是把这段JS代码注册到按钮的click事件上了。
				等这个按钮发生click事件之后，注册在onclick后面的js代码会被浏览器自动调用。
			
			4、怎么使用JS代码弹出消息框？
				在JS中有一个内置的对象叫做window，全部小写，可以直接拿来使用，window代表的是浏览器对象。
				window对象有一个函数叫做:alert，用法是：window.alert("消息");这样就可以弹窗了。
			
			5、JS中的字符串可以使用双引号，也可以使用单引号。

			6、JS中的一条语句结束之后可以使用分号“;”，也可以不用。
		-->
		<input type="button" value="hello" onclick="window.alert('hello js')"/>

		<input type="button" value="hello" onclick='window.alert("hello jscode")'/>

		<input type="button" value="hello" onclick="window.alert('hello zhangsan')
													window.alert('hello lis')
													window.alert('hello wangwu')"/>
		
		<!-- window. 可以省略。-->
		<input type="button" value="hello" onclick="alert('hello zhangsan')
													alert('hello lis')
													alert('hello wangwu')"/>
		
		<input type="button" value="hello" onclick="alert('hello zhangsan');
													alert('hello lis');
													alert('hello wangwu');"/>

	</body>
</html>
~~~





## 第二种方式（在Script块中书写js代码）

~~~html

<!--
	javascript的脚本块在一个页面当中可以出现多次。没有要求。
	javascript的脚本块出现位置也没有要求，随意。
-->
<script type="text/javascript">
// alert有阻塞当前页面加载的作用。（阻挡，直到用户点击确定按钮。）
window.alert("first.......");
</script>

<!doctype html>
<html>
	<head>
		<title>HTML中嵌入JS代码的第二种方式</title>

		<!--样式块-->
		<style type="text/css">
			/*
				css代码
			*/
		</style>

		<script type="text/javascript">
			window.alert("head............");
		</script>

	</head>
	<body>

		<input type="button" value="我是一个按钮对象1" />
		
		<!--第二种方式：脚本块的方式-->
		<script type="text/javascript">

			/*
				暴露在脚本块当中的程序，在页面打开的时候执行，
				并且遵守自上而下（包括html）的顺序依次逐行执行。（这个代
				码的执行不需要事件）
			*/
			window.alert("Hello World!"); // alert函数会阻塞整个HTML页面的加载。
			
			// JS代码的注释，这是单行注释。
			/*
				JS代码的多行注释。和java一样。
			*/
			window.alert("Hello JavaScript!");

		</script>

		<input type="button" value="我是一个按钮对象" />

	</body>
</html>

<script type="text/javascript">
window.alert("last.......");
</script>

<!--
/**
*
* javadoc注释，这里的注释信息会被javadoc.exe工具解析提取生成帮助文档。
*/
-->
~~~





## 第三种方式（连接外部js文件）

~~~html
<!doctype html>
<html>
	<head>
		<title>HTML中嵌入JS代码的第三种方式：引入外部独立的js文件。</title>
	</head>
	<body>
		
		<!--在需要的位置引入js脚本文件-->
		<!--引入外部独立的js文件的时候，js文件中的代码会遵循自上而下的顺序依次逐行执行。-->
        <!--<script type="text/javascript" src="js/1.js"></script>-->

        
        
		<!--同一个js文件可以被引入多次。但实际开发中这种需求很少。-->
		<!--<script type="text/javascript" src="js/1.js"></script>-->

		<!--这种方式不行，结束的script标签必须有。-->
		<!--<script type="text/javascript" src="js/1.js" />-->
		<!--<script type="text/javascript" src="js/1.js"></script>-->

        
        
		<script type="text/javascript" src="js/1.js">
			// 这里写的代码不会执行。
			// window.alert("Test");
		</script>

    </body>
    	<!--这里的代码可以执行-->
		<script type="text/javascript">
			alert("hello jack!");
		</script>


	</body>
</html>
~~~



# 三、JS中的变量

## 回顾java中的变量：



1、java中怎么  **定义** 声明变量？
			`	数据类型 变量名;`
例如：

		int i;
		double d;
		boolean flag;	







2、java中的变量怎么赋值？
					使用“=”运算符进行赋值运算。（"="运算符右边先执行，将右边执行的结果赋值给左边的变量）
例如：

~~~
			i = 10;
			d = 3.14;
			flag = false;
~~~



3、java语言是一种`强类型语言`，强类型怎么理解？
					java语言存在编译阶段，假设有代码：int i;
					那么在Java中有一个特点是：java程序编译阶段就已经确定了i变量的数据类型，该i变量的数据类型在编译阶段是int类型，
					那么  **这个变量**  到`  最终内存释放`，一直都是int类型，不可能变成其他类型。

例如：

~~~
		int i = 10;
		double d = i; 
		这行代码是说声明一个新的变量d，double类型，把i变量中保存的值传给d。
		i还是int类型。
~~~



`		i = "abc";  `  这行代码编译的时候会报错，因为i变量的数据类型是int类型，不能将字符串赋给i。

java中要求变量声明的时候是什么类型，以后永远都是这种类型，不可变。`编译期`  ` 强行固定变量`的  **数据类型**。称为**强类型语言**。



## JS中的变量

javascript当中的变量？怎么声明变量？

`	var 变量名;`

怎么给变量赋值？
`变量名 = 值;`

javascript是一种 ` 弱类型语言`，**没有编译阶段**，一个变量可以随意赋值，赋什么类型的值都行。

		var i = 100;
		i = false;
		i = "abc";
		i = new Object();
		i = 3.14;		

重点：

javascript是一种   **弱类型**  编程语言。





例子：

~~~html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>关于JS中的变量</title>
	</head>
	<body>
        <!--在js代码块中的代码，在页面打开时自上而下地执行-->
		<script type="text/javascript">

		   // 在JS当中,当一个变量没有手动赋值的时候,系统默认赋值undefined
		   var i;
		   // undefined 在JS中是一个   具体  存在值.
		   alert("i = " + i); // i = undefined
		   
		   alert(undefined);
		   var k = undefined;
		   alert("k = " + k);
		   
            
            
            
		   // 一个变量没有声明/定义,直接访问?
		   // alert(age); //语法错误：age is not defined (变量age不存在。不能这样写)
		   
		   var a, b, c = 200;
		   alert("a = " + a);//undefine
		   alert("b = " + b);//undefine
		   alert("c = " + c);//200
		   
		   a = false;
		   alert(a);//false
		   
		   a = "abc";
		   alert(a);//abc
		   
		   a = 1.2;
		   alert(a);//1.2
		   
		</script>
	</body>
</html>

~~~



## 全局变量与局部变量

全局变量：
在  `函数体之外`  声明的变量 ` 属于全局变量`(只要不带 类型 如：var let  ，无论在哪里声明，都是全局变量)

全局变量的生命周期是：
		浏览器打开时声明，**浏览器关闭时销毁**，尽量少用。因为全局变量会一直在浏览器的内存当中，耗费内存空间。
		能使用局部变量尽量使用局部变量。

局部变量：
		在函数体当中声明的变量，包括一个函数的形参都属于局部变量，
		局部变量的生命周期是：函数开始执行时局部变量的内存空间开辟，`函数执行结束 `之后，`局部变量的内存空间释放`。
		局部变量生命周期较短。

~~~html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>JS的局部变量和全局变量</title>
	</head>
	<body>
		<script type="text/javascript">
		   
		   // 全局变量
		   var i = 100;
		   
		   function accessI(){
			   // 访问的是全局变量
			   alert("i = " + i);
		   }
		   
		   accessI();
		   
		   // 全局变量
		   var username = "jack";
		   function accessUsername(){
			   // 局部变量
			   var username = "lisi";
			   // 就近原则:访问局部变量
			   alert("username = " + username);
		   }
		   // 调用函数
		   accessUsername();
		   // 访问全局变量
		   alert("username = " + username);
		   
		   function accessAge(){
			   var age = 20;
			   alert("年龄 = " + age);
		   }
		   
		   accessAge();
		   
		   // 报错(语法不对)
		   // alert("age = " + age);
		   
		   // 以下语法是很奇怪的.
		   function myfun(){
			   // 当一个变量声明的时候没有使用var关键字,那么不管这个变量是在哪里声明的,都是全局变量.
			   myname = "dujubin";
		   }
		   
		   // 访问函数
		   myfun();
		   
		   alert("myname = " + myname); // myname = dujubin
		   
		</script>
	</body>
</html>

~~~







# 四、JS中的数据类型

## 4.1 总体概述

1、虽然JS中的变量在声明的时候不需要指定数据类型，但是在赋值，每一个数据还是有类型的，所以

这里也需要学习一下JS包括哪些数据类型

JS中数据类型有：`原始类型、引用类型` **ES6之前一共六种**

​         原始类型：`Undefined、Number、String、Boolean、Null`
​         引用类型：`Object以及Object的子类`



2、ES规范(ECMAScript规范)，在ES6之后，又基于以上的6种类型之外添加了一种新的类型：

​	`	Symbol`





3、JS中有一个运算符叫做`typeof`，这个运算符可以在 ` 程序的运行阶段`  **动态的获取 **  `变量的数据类型`。

​      typeof运算符的语法格式：
​          `typeof 变量名`



typeof运算符的运算结果是以下 ` 6个字符串之一`：注意 ` 字符串`  都是**全部小写**。

```
   "undefined"
   "number"
   "string"
   "boolean"
   "object"
   "function"
```



4、在JS当中  `比较字符串`  是否相等   **使用“==”完成**。**没有equals**。



```html
<!DOCTYPE html>
<html>
   <head>
      <meta charset="utf-8">
      <title>JS中的数据类型</title>
   </head>
   <body>
      <script type="text/javascript">
         
         /*
         // 求和,要求a变量和b变量将来的数据类型必须是数字,不能是其他类型
         // 因为以下定义的这个sum函数是为了完成两个数字的求和.
         function sum(a, b){
            if(typeof a == "number" && typeof b == "number"){
               return a + b;
            }
            alert(a + "," + b + "必须都为数字！");
         }
         
         // 别人去调用以上你写的sum函数.
         var retValue = sum(false, "abc");
         alert(retValue); // undefined  因为函数是弹出窗口，而没有返回值，所以是undefine
         
         var retValue2 = sum(1, 2);
         alert(retValue2); // 3
         */
        
          
          
          
          
          
        //js typeof运算符的六种值
        var i;
        alert(typeof i); // "undefined"
        
        var k = 10;
        alert(typeof k); // "number"
        
        var f = "abc";
        alert(typeof f); // "string"
        
        var d = null;
        alert(typeof d); // "object"  【null属于Null类型,但是typeof运算符的结果是"object"】
        
        var flag = false;
        alert(typeof flag); // "boolean"
        
        var obj = new Object();
        alert(typeof obj); // "object"
        
        // sayHello是一个函数.
        function sayHello(){
           
        }
        alert(typeof sayHello); // "function"
        
         
      </script>
   </body>
</html>
```



## 4.2 Undefine

Undefined是一种类型，该类型只有只有一个值，这个值就是 undefined；不要用单引号或者是双引号括着，不然类型就变成字符串了；

当一个变量没有手动赋值，系统默认赋值undefined或者也可以给一个变量手动赋值undefined。

​	

例子：

~~~html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>Undefined类型</title>
	</head>
	<body>
		
		<script type="text/javascript">
		   var i; // undefined
		   var k = undefined; // undefined
		   
		   alert(i == k); // true
		   
		   var y = "undefined"; // "undefined"
		   alert(y == k); // false
		   
		</script>
		
	</body>
</html>

~~~



## 4.3 Menber

1、Number类型包括哪些值？

~~~
 -1 0 1 2 2.3 3.14 100 .... NaN Infinity
~~~



整数、小数、正数、负数、不是数字、无穷大都属于Number类型。



2、isNaN() : 

​	结果是true表示不是一个数字，结果是false表示是一个数字。

3、parseInt()函数

4、parseFloat()函数

5、Math.ceil() 函数（Math是数学类，数学类当中有一个函数叫做ceil()，作用是向上取整）





例子：

```html
<!DOCTYPE html>
<html>
   <head>
      <meta charset="utf-8">
      <title>Number类型</title>
   </head>
   <body>
      <script type="text/javascript">

         var v1 = 1;
         var v2 = 3.14;
         var v3 = -100;
         var v4 = NaN;
         var v5 = Infinity;
         
         // "number"
         alert(typeof v1);
         alert(typeof v2);
         alert(typeof v3);
         alert(typeof v4);
         alert(typeof v5);
         
          
          
         // 关于NaN (表示Not a Number，不是一个数字，但属于Number类型)
         // 什么情况下结果是一个NaN呢？
         // 运算结果本来应该是一个数字,最后算完不是一个数字的时候,结果是NaN.
         var a = 100;
         var b = "中国人";
         alert(a / b); // 除号显然最后结果应该是一个数字,但是运算的过程中导致最后不是一个数字,那么最后的结果是NaN
         
         var e = "abc";
         var f = 10;
         alert(e + f); // "abc10"
         
          
          
          
         // Infinity (当除数为0的时候，结果为无穷大)
         alert(10 / 0);
         
          
          
         // 思考:在JS中10 / 3 = ?
         alert(10 / 3); // 3.3333333333333335
         
          
          
          
         // 关于isNaN函数？
         // 用法：isNaN(数据) ,结果是true表示不是一个数字, 结果是false表示是一个数字.
         // isNaN : is Not a Number 
         function sum(a, b){
            if(isNaN(a) || isNaN(b)){
               alert("参与运算的必须是数字！");
               return;
            }
            return a + b;
         }
         sum(100, "abc");
         alert(sum(100, 200));
         
          
          
          
         // parseInt():可以将字符串自动转换成数字,并且取整数位.
         alert(parseInt("3.9999")); // 3
         alert(parseInt(3.9999)); // 3
         
          
          
          
         // parseFloat():可以将字符串自动转换成数字.
         alert(parseFloat("3.14") + 1); // 4.14
         alert(parseFloat("3.2") + 1); // 4.2
         
          
          
          
         // Math.ceil()
         alert(Math.ceil("2.1")); // 3
         
      </script>
   </body>
</html>
```



## 4.4 Boolean

 1、 JS中的布尔类型永远都只有两个值：true和false （这一点和java相同）

2、在Boolean类型中有一个函数叫做：Boolean()。

 语法格式：  `  Boolean(数据) `

 Boolean()函数  的  **作 用是 ** 将`非布尔类型   转换   成布尔类型`。



规律:“有"就转换成true,"没有"就转换成false.

```js
	alert(Boolean(1)); // true
    alert(Boolean(0)); // false
    alert(Boolean("")); // false
    alert(Boolean("abc")); // true
    alert(Boolean(null)); // false
    alert(Boolean(NaN)); // false
    alert(Boolean(undefined)); // false
    alert(Boolean(Infinity)); // true
```

注意了：if括号中的类型必须是Boolean类型；所以当里面的类型不是Boolean类型时，会自动调用Boolean方法，转化为Boolean类型的值



```html
<!DOCTYPE html>
<html>
   <head>
      <meta charset="utf-8">
      <title>Boolean类型</title>
   </head>
   <body>
      <script type="text/javascript">

         // var username = "lucy";
         var username = "";
         
         /*
         if(Boolean(username)){//false
            alert("欢迎你" + username);
         }else{
            alert("用户名不能为空！");
         }
         */
        
        /*
         if(username){
            alert("欢迎你" + username);
         }else{
            alert("用户名不能为空！");
         }
         */
        

         
         /*
         while(10 / 3){//true
            alert("hehe");
         }
         */
         
         for(var i = 0; i < 10; i++){
            alert("i = " + i);
         }
         
          
          
          
          
         // Null类型只有一个值,null
         alert(typeof null); // "object"
         
      </script>
   </body>
</html>
```



# 、JS中的函数

  1、JS中的函数：
               等同于java语言中的方法，函数也是一段可以被重复利用的代码片段。
               函数一般都是可以完成某个特定功能的。
               





2、回顾java中的方法？


```
       [修饰符列表] 返回值类型 方法名(形式参数列表){
          方法体;
       }
```

 例如：

~~~java
       public static boolean login(String username,String password){
          ...
          return true;
       }

        public static void main(String[] args){
              boolean loginSuccess = login("admin","123"); 
        }

~~~







 3、JS中的  **变量**  是一种  **弱类型**的，那么函数应该怎么定义呢？
           语法格式：

~~~
              第一种方式：
                 function 函数名(形式参数列表){
                    函数体;
                 }
              第二种方式：
                 函数名 = function(形式参数列表){
                    函数体;
                 }
~~~

 JS中的函数  **不需要  指定**返回值类型，因为  **返回什么类型都行**。

​             

注意：

1、形参不用指定类型；

2、函数必须调用，不然不会执行；

3、在script块中，函数定义的优先级较高（即使函数调用在上，函数定义在下，函数依旧可以执行）

```html
<!DOCTYPE html>
<html>
   <head>
      <meta charset="utf-8">
      <title>JS函数初步</title>
   </head>
   <body>
      <script type="text/javascript">

         function sum(a, b){
            // a和b都是局部变量,他们都是形参(a和b都是变量名，变量名随意。)
            //alert(a + b);
             console.log(a+':'+b);
         }
         
         // 函数必须调用才能执行的.
          sum();//undefine:undefine
          sum(1)//undefine:undefine
          sum(10, 20);//10:20
          sum(1,2,3,4)//1:2
         
         // 定义函数sayHello
         sayHello = function(username){
            alert("hello " + username);
         }
         
         // 调用函数
         sayHello("zhangsan");//hellozhangsan
         sayHello();//helloundefine
      </script>
      <!--事件句柄中写js代码-->
      <input type="button" value="hello" onclick="sayHello('jack');" /> 
      <input type="button" value="计算10和20的求和" onclick="sum(10, 20);" />
      
   </body>
</html>
```





~~~html
<!DOCTYPE html>
<html>
   <head>
      <meta charset="utf-8">
      <title>JS函数初步</title>
   </head>
   <body>
      <script type="text/javascript">
         /*
            java中的方法有重载机制，JS中的函数能重载吗？
               JS当中的函数在调用的时候，参数的类型没有限制，并且参数的个数也没有限制，JS就是这么随意。（弱类型）
            
            重载的含义：
               方法名或者函数名一样，形参不同（个数、类型、顺序）
         */
         function sum(a, b){
            return a + b;
         }
         
         // 调用函数sum
         var retValue = sum(1, 2);
         alert(retValue);
         
         var retValue2 = sum("jack"); // jack赋值给a变量,b变量没有赋值系统默认赋值undefined
         alert(retValue2); // jackundefined
         
         var retValue3 = sum();
         alert(retValue3); // NaN (NaN是一个具体存在的值，该值表示不是数字。Not a Number)
         
         var retValue4 = sum(1, 2, 3);
         alert("结果=" + retValue4); // 结果=3
         
         function test1(username){
            alert("test1");
         }
         
         /*
         在JS当中，函数的名字 不能重名 ，当函数重名的时候，后声明的函数会将之前声明的同名函数覆盖。
         */
         function test1(){
            alert("test1 test1");
         }
         
         test1("lisi"); // 这个调用的是第二个test1()函数.
         
      </script>
   </body>
</html>
~~~



# 、JS中的事件

 JS中的事件：
           blur失去焦点   
           focus获得焦点
  		 click鼠标单击
           dblclick鼠标双击
           keydown键盘按下

​		   keyup键盘弹起

​		   mousedown鼠标按下
​           mouseover鼠标经过
​           mousemove鼠标移动
​           mouseout鼠标离开
​           mouseup鼠标弹起

​		   reset表单重置
​           submit表单提交
​           change下拉列表选中项改变，或文本框内容改变

​			select文本被选定
​       	load页面加载完毕（ ` 整个HTML页面中`  **所有的元素**  `全部加载完毕之`后  发生）



   任何一个事件都会对应一个事件句柄，事件句柄是在事件前添加on。

  onXXX这个事件句柄出现在一个标签的属性位置上。（  `事件句柄  ` 在标签中  `以属性的形式存在`）









**blur事件：**

~~~html
blur事件: <input type="text" onblur="console.log('失点了!')"/>
~~~

---

[![vZXs9e.png](https://s1.ax1x.com/2022/08/03/vZXs9e.png)](https://imgtu.com/i/vZXs9e)

---





**change事件：**

****

~~~html
<!-- change事件:下拉列表项被改变的时候发生-->
change事件:
<select name="grade" onchange="console.log('下拉列表项发生改变了.')">
    <option value ="gz">高中</option>
    <option value ="zk">专科</option>
    <option value ="bk">本科/option> 
</select>
~~~

---

[![vZXWHP.png](https://s1.ax1x.com/2022/08/03/vZXWHP.png)](https://imgtu.com/i/vZXWHP)



----

[![vZXo9g.png](https://s1.ax1x.com/2022/08/03/vZXo9g.png)](https://imgtu.com/i/vZXo9g)

---







**load事件：**

~~~html
<!DOCTYPE html>
<html>
    <head>
        <meta charset= "utf-8">
        <title>Js的事件</title>
        <script type="text/javascript">
            alert(111)
        </script>
    </head>
    <!-- load事件在什么时候发生?在页面元素全部加载完毕之后才会发生-->
    <!--alert()函数有阻塞功能，必须用户点确认才可以继续往下-->
    <body onload="console.log('页面加载完毕了,load事件发生了.')">
        
    </body>
</html>
~~~







根据标签中的id获取，某个节点

~~~html
<!DOCTYPE html> 
<html>
    <head>
        <meta charset= "utf-8">
        <title>根据id获取页面中的某个节点</title>
    </head>
    
    <body>
        <!--脚本块-->
        <script type="text/javascript">
            //获取div节点对象1document对象是Js内置的对象,全部小写,可以直接拿来使用.window对象是Js内置的对象,全部小写,可以直接拿来使用。window
            function getDivElt(){
               var mydivElt document.getElementById('mydiv');
                console.log(mydivElt);
            }
        
        </script><!-- div节点对象-->
        
        <!-- div节点对象-->
        <div id="mydiv"></div>
        <input type="button" value="获取div节点元素" onclick="getDivElt()"/>
        
    </body>
</html>
~~~

~~~
<div id="mydiv"></div>
~~~



document对象代表的是浏览器窗口中的网页(文档)

window代表当前浏览器窗口



---

[![vZj0rn.png](https://s1.ax1x.com/2022/08/03/vZj0rn.png)](https://imgtu.com/i/vZj0rn)

---

我们把这个文档称为DOM树。

DOM树上有很多节点,每一个节点都有ID属性。获取DOM树上的一个节点,可以根据id来获取。document对象代表的是浏览器窗口中的网页(文档)





innerHtml()方法的使用

~~~html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<script type="text/javascript">
    function getContent() {
        var h1Elt = document.getElementById('myh1');
        //获取div中的内容
        // innerHTML是一个非常重要的属性,它可以获取也可以设置元素内部的内容.
        console.log(h1Elt.innerHTML);
    }
</script>
<body>
<h1 id="myh1">
    this is the content of h1
</h1>

<div id="div1" style="background-color: aquamarine">

</div>
<input type="button" value="button" onclick="getContent()">
</body>
</html>
~~~

---

[![vZvBSe.png](https://s1.ax1x.com/2022/08/03/vZvBSe.png)](https://imgtu.com/i/vZvBSe)

---







~~~html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<script type="text/javascript">
    function getContent() {
        var h1Elt = document.getElementById('myh1');
        //获取div中的内容
        // innerHTML是一个非常重要的属性,它可以获取也可以设置元素内部的内容.
        console.log(h1Elt.innerHTML);
        let divElt = document.getElementById('div1');
        divElt.innerHTML = h1Elt.innerHTML;
    }
</script>
<body>
<h1 id="myh1">
    this is the content of h1
</h1>

<div id="div1" style="background-color: aquamarine">

</div>
<input type="button" value="button" onclick="getContent()">
</body>
</html>
~~~



---

[![vZvOYT.png](https://s1.ax1x.com/2022/08/03/vZvOYT.png)](https://imgtu.com/i/vZvOYT)

---





```html
<!DOCTYPE html>
<html>
   <head>
      <meta charset="utf-8">
      <title>JS的常用事件</title>
   </head>
   <body>
      <script type="text/javascript">
         /*
           
         */
         // 对于当前程序来说,sayHello函数被称为回调函数(callback函数)
         // 回调函数的特点:自己把这个函数代码写出来了,但是这个函数不是自己负责调用,由其他程序负责调用该函数.
         function sayHello(){
            alert("hello js!");
         }
      </script>
      
      <!--注册事件的第一种方式，直接在标签中使用事件句柄-->
      <!--以下代码的含义是：将sayHello函数注册到按钮上，等待click事件发生之后，该函数被浏览器调用。我们称这个函数为回调函数。-->
      <input type="button" value="hello" onclick="sayHello()"/>
      
      
      <input type="button" value="hello2" id="mybtn" />
      <input type="button" value="hello3" id="mybtn1" />
      <input type="button" value="hello4" id="mybtn2" />
      <script type="text/javascript">
         function doSome(){
            alert("do some!");
         }
         /*
            第二种注册事件的方式，是使用纯JS代码完成事件的注册。
         */
         // 第一步:先获取这个按钮对象(document是全部小写，内置对象，可以直接用，document就代表整个HTML页面)
         var btnObj = document.getElementById("mybtn");
         // 第二步:给按钮对象的onclick属性赋值
         btnObj.onclick = doSome; // 注意:千万别加小括号. btnObj.onclick = doSome();这是错误的写法.
                           // 这行代码的含义是,将回调函数doSome注册到click事件上.
         
         var mybtn1 = document.getElementById("mybtn1");
         mybtn1.onclick = function(){ // 这个函数没有名字,叫做匿名函数,这个匿名函数也是一个回调函数.
            alert("test.........."); // 这个函数在页面打开的时候只是注册上,不会被调用,在click事件发生之后才会调用.
         }
         
         document.getElementById("mybtn2").onclick = function(){
            alert("test22222222.........");
         }
      </script>
      
   </body>
</html>

<!--
   java中也有回调函数机制：
      public class MyClass{
         
         public static void main(String[] args){
            // 主动调用run()方法，站在这个角度看run()方法叫做正向调用。
            run();
         }
         
         // 站在run方法的编写者角度来看这个方法，把run方法叫做回调函数。
         public static void run(){
            System.out.println("run...");
         }
      }
-->
```

















































