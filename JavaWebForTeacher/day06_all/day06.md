# day06

## JavaScript

### 网页所有的交互都要使用JavaScript

## Javascript的发展

### 网景找到ECMA(欧洲计算机联盟协会)统一了Javascript标准
### 我们要学习的就是这一套统一的标准

### JavaScript的特点

1. 可以使用任何文本编译工具编写
2. 由浏览器内置的JavaScript引擎执行代码
3. 解释执行:事先不编译,逐行执行
4. 基于对象:内置了大量写好的对象


### 学习javascript
### 1. 学习如何找到标签对象
### 2. 学习对标签对象的属性内容,进行增删改查.

## JavaScript的使用

1. 事件定义式,在事件定义时直接写js代码


	<!-- 事件:用户在做出某种操作时,会调用js代码  -->
	<!-- 事件就是js调用时机,比如单击按钮等 -->
	<!-- 1.事件定义式,在定义事件时,直接写js代码 -->
	<input type="button" value="事件定义式"
	onclick="alert('我被单击了');">

2. 嵌入式,在`<script>`标签内,写js代码

	/* 把js代码写到script标签内部 */
	/* script标签可以放到html的任何位置 */
	/*但通常放到head标签中 */
	
	/* function是关键字,用来声明函数 */
	/* fn1是函数名,小括号内可以声明参数 */
	/* js中函数都是公有的,不需要修饰符 */
	/* 函数不需要声明返回值类型 */
	/* 函数体中没写retrun,函数调用时默认返回值为undefined */
	function fn1(){
		alert("我是嵌入式js的使用");
	}
	function fn2(){
		alert("我是验证返回值");
		return 123;
	}

3. 文件调用式

	<input type="button" value="文件调用式"
	onclick="fn3();">

	my.js文件中

	function fn3(){
		console.log("我是文件调用式");
	}
	
	在<head>标签内部写

	<script type="text/javascript" src="my.js"></script>

### 总结:
### 文件调用式,在单独的.js文件写js代码
### 需要引用到网页才能使用
### 引用时:script标签必须是双标签,哪怕没有内容
### 这个script作用就是导入外部的js文件,
### 不允许同时引用文件,又写js代码

4. js注释:`<script>`标签中,是js地盘,要使用js的注释.

	  //      /* js不区分单引号和双引号 */


### 课堂练习

1. 事件定义式
2. 嵌入式
3. 文件调用式
4. 注释

## js数据类型

### 1.变量的声明和定义

	<script type="text/javascript">
	  //声明变量
	  var x;
	  //给变量赋值
	  //x=9;
	  //x="abc";
	  console.log(x);
	  var y=123;
	</script>

### 总结:在`<script>`标签中写js代码一般有两种形式
### 1. 封装成函数,该函数在页面加载完成之后,用户激活事件时,被调用.
### 2. 直接在标签中写js代码,这段js代码是在页面加载过程中被直接调用,其调用时机甚至比body渲染还早.

## number 类型

### 不区分整型和浮点型
### 所有的数字,都采用64位浮点格式存储
### js中没有double的概念

## String类型

### 由Unicode字符.数字.符号组成字符序列
### 由首尾一对单引号或者一对双引号括起.
### 单引号和双引号,嵌套的时候,无需转义
### 其他特殊字符需要转义,\n
### js中没有char的概念,字符就是一个长度的string

## boolean
### true和false
### 做数学运算的时候,自动转型为数值参与计算

	  var s="hello";
	  var n=9;
	  var b=true;
	  
	  console.log(s+n);//hello9
	  console.log(s+b);//hellotrue
	  console.log(n+b);//true--1  false--0
	  console.log(b+b);//

### 在参与纯数学运算时,true---1 false---0

### js引擎对boolean类型的解释规则

1. 非空字符串解释为true,""字符串解释为false
2. 非0数字,解释为true.0为false
3. null undefined都为false

### 强制类型转换

	//var n=3.14;
	//var s="3.14";
	//console.log(n.toString()+1);
	//console.log(parseInt(s)+1);
	//console.log(parseFloat(s)+1);
	//console.log(parseFloat("abc")+1);//not a number
	//console.log(parseInt(""));//NaN

### typeof

	function fn1(){
		var num=100;
		console.log(typeof(num)=="number");
		var str="abc";
		console.log(typeof(str)=="string");
		console.log(typeof(null));
		console.log(typeof(undefined));
	}

### isNaN

	function fn2(){
		//is 是什么
		//NaN not a number  不是一个数
		//isNaN 是不是 不是一个数
		console.log(isNaN(56));//f  不是 NaN
		console.log(isNaN("32"));//f
		console.log(isNaN("abc"));//t 是 NaN
		console.log(isNaN(""));//f
		console.log(parseInt(""));//此处是个bug
	}

### 课堂练习

![](1.png)

		<body>
			<input type="text" id="num">
			<input type="button" value="平方" onclick="cal();">
			= <span id="result">计算的结果</span>
		</body>

		<script type="text/javascript">
		function cal(){
			//1.获取文本框内的数 value
			var input=document.getElementById("num");
			var num=input.value;
			var span=document.getElementById("result");
			console.log(span);
			//2.判断这个数是不是数字
			if(num!=""){
				if(isNaN(num)){
					//4.不是数字,span中提示用户输入错误
					span.innerHTML="输入错误";
				}else{
					//3.是数字,计算,并把结果放入span显示
					span.innerHTML=num*num;
				}
			}else{
				span.innerHTML="请输入数字";
			}
		}
		</script>

### 数学运算符 + - * / %  ++
### 总结:
### 1.纯数字的字符串,除了+会变成字符串连接,其他的运算都会自动转成数字
### 2.js中的除法,如果除不尽会得到浮点数100/3

### 关系运算符 > < >= <= != ==


	<script type="text/javascript">
		function doClick(){
			var s1="123";
			var s2=123;
			var s3=123;
			
			console.log(s1==s2);//t
			console.log(s1==s3);//t
			//全等:
			//类型相同
			//数据值相同
			console.log(s1===s2);
			console.log(s2===s3);
		}
		doClick();
	</script>

### 课堂练习:网页版猜数字

![](2.png)

### 逻辑运算符  ! && ||  
### 要注意短路问题

### 条件表达式
### js可以使用任何数据做条件

		if("afsda"){
			console.log(1111);
		}

### 当使用非boolean值做条件时
### true  非空字符串 非0数字
### false null undefined "" 0 NaN

	if(NaN){

	}else{
		console.log(11111);
	}


## 作业:
### 今天所有的理论和demo重新过一遍
### 1.猜数字和平方
### 2.提高题:选作

426029026218 2
求出前12位奇数位数字之和.462061=19
求出前12位偶数位数字之和.209228=23
把 前12位奇数位数字之和 与 偶数位数字之和的3倍相加.19+69=88
取结果的个位数.	8
用10减去这个个位数.	2
再取结果的个位数.	2

for(var i=0;i<12;i++){
console.log(i);
}




































































