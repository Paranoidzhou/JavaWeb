## JavaScript

### 网页所有的交互都要使用JavaScript--->JQuery(网景开发) JScript(微软开发)

- JavaScript的发展：网景找到ECMA(欧洲计算机联盟协会)统一了JavaScript标准。
- 我们需要学习的就是这一套统一标准。
- JavaScript与Java没有任何关系。

### JavaScript的特点：
- 1.可以使用任何文本编译工具编写。
- 2.由浏览器内置的JavaScropt引擎执行代码。
- 3.解释执行：事先不编译、逐行执行。
- 4.基于对象：内置了大量写好的对象。

### 学习JavaScript：
- 1.学习如何找到标签对象。
- 2.学习对标签对象的属性内容，进行增删改查。       

## JavaScript的使用：

### 事件定义式、在事件定义时直接写js代码。
- 什么是事件？：用户在做出某种操作时，会调用js代码.事件就是Js调用时机、例如单击按钮（鼠标的点击，F5刷新，滚轮等等都是事件） 

- 事件定义式 ：在定义事件时、直接写js代码。
实例代码： 
			 <input type="button" value="时间定义式" onclick="alert('我被猪点了');"> 

- js代码的嵌入式：在< script >标签内，写js代码。script标签可以放到html的任何位置，但是通常放到head标签中。
实例代码：  	
			<!-- function是关键字，用来声明函数。fn1是函数名，小括号内可以声明参数 -->
			<!-- js中函数都是共有的，不需要修饰符。函数不需要声明返回值类型 -->
			<!-- 函数体中没写return,函数调用时默认返回值为undefined(未定义) -->

			<script type="text/javascript">
				function fn1(){
				alert("我是嵌入式js的使用!");
			}
			</script>
			<input type="button" value="嵌入式" onclick="fn1('');"> 
	
- 文件调用式：在外部新建一个 xx.js文件，然后< script >标签内添加(src)调用.
实例代码：
			<script type="text/javascript" src="my.js"></script>	
			<input type="button" value="文件调用式" onclick="fn3();">
	
			【外部js代码：】
			function fn3(){
			console.log("我是文件样式");
			}

> 总结：文件调用式、在单独的.js文件写js代码，需要引用到网页才能使用.引用时script标签必须成对出现，哪怕没有内容。此script作用就是导入外部的js文件，不允许同时引用文件，又写js代码。

- js注释：< script >标签中，时js的地盘，要使用Js的注释。
-  `//`                       ： 单行注释
- `/* js代码区分单双引号 */ `	  ： 多行注释

## Js数据类型
- 变量的声明和定义
		<script type="text/javascript">
 		  // 声明变量。
 		  var x ;
  		 // 给变量赋值。
  		 x = 9;
  		 x = "abc";
  		 console.log(x);
	    </script>
> 总结：在< script > 标签中写js代码一般有两种形式：
> 1.封装成函数、该函数在页面加载完成之后，用户激活事件时被调用。
> 2.直接在标签中写js代码、这段Js代码是在页面加载过程中被直接调用，其调用时机甚至比body渲染还早。

#### number(数值类型)：
- 不区分整型、浮点型；js数据类型中没有double型。
- 所有的数字都采用64位浮点格式存储。

#### String(字符串类型)：
- 由Unicode字符、数字、符号、组成的字符序列。
- 由首尾一对单引号/双引号括起。例如: "abc" 和'abc'效果是一样的。
- 单引号和双引号嵌套的时候，无需转义.其他特殊字符需要转义;例如\n
- js中没有char的概念，字符就是一个长度的String

#### boolean(布尔类型)：
- true和false.
- 在做数学运算的时候，自动转型为数值参与计算。
			var s="hello";
			var n=9;
			var b=true;

			console.log(s+n);
			console.log(s+b);
			console.log(n+b);
			console.log(b+b);
>总结：在参与纯数学运算时，true---1、false---0.

- js引擎对boolean类型的解释规则：
1.非空字符串解释为true,""字符串解释为false.
		if("a"){console.log(true)}else{console.log("false")}    //true
		if(""){console.log(true)}else{console.log("false")}    //false

2.非0数字，解释为true、0为false.
		if(0){console.log("true")}else{console.log("false")}   //false
		if(1){console.log("true")}else{console.log("false")}   //true

3.null undefined都为false.
		if(unde){console.log("true")}else{console.log("false")}		  //false
		if(undefined){console.log("true")}else{console.log("false")}  //false

#### 强制类型转换：
		<title>JS中的强制类型转换</title>
		<script type="text/javascript">
			var n = 3.14;
			var s = "3.14";
			console.log(n.toString()+1);	//3.141
			console.log(parseInt(s)+1);		//4
			console.log(parseFloat(s)+1);	//4.14000000000001 
			console.log(parseInt(""));      //NaN (not a number)不是一个数
			function fn1(){
				var num=100;
				console.log(typeof(num)=="number");	 //判断数据类型
				var str="abc";
				console.log(typeof(str)=="string");  //严格区分大小写
				console.log(typeof(null));
				console.log(typeof(undefined));
			}
			function fn2(){	
				// is 是什么/是不是
				// NaN 不是一个数
				// is NaN 是不是 不是一个数。
				console.log(isNaN(56));	 //f   不是NaN
				console.log(isNaN("32"));   //f
				console.log(isNaN("abc"));  //t   是NaN
				console.log(isNaN(""));	 //f
				console.log(parseInt(""));  //此处是个BUG
			}
	
		</script>
		</head>
		<body>
			<input type="button" value="检测typeof" onclick="fn1();">
			<input type="button" value="检测isNaN" onclick="fn2();">
		</body>

#### 数学运算符：+ - * / % ++ 
- 1.纯数字的字符串，除了+会变成字符串拼接，其他的运算都会自动转换成数字运算。
- 2.js中的除法如果除不尽会得到浮点数。 例如：100/3=33.3333333336.

#### 关系运算符：> < >= <= != ==  ===
		var s1 = "123";
		var s2 = 123 ;
		var s3 = 123 ;
		
		console.log(s1==s2);    //true
		console.log(s1==s3);	//true
		console.log(s1===s2);	//false
		console.log(s1===s2);	//false
		// === 全等：类型相同、数据值相同。

#### 逻辑运算符：! && ||
* 注意短路问题。

#### 条件表达式：
- js可以使用任何数据做条件。 

>回顾总结：当使用非boolean值做条件时，非空字符串、非0数字都为true ; null、undefined "" 0 NaN都为false.