# day08
## js中的常用API

## 完善form表单的验证

![](1.png)

		<body>
			<form action="http://www.tmooc.cn"   
			onsubmit="return checkUser()*checkPwd()==1;">
				<div>
					账号:<input type="text" id="username" 
					onblur="checkUser();">
					<span id="msg_user">5-10位数字,字母,下划线</span>
				</div>
				<div>
					密码:<input type="password" id="pwd" 
					onblur="checkPwd();">
					<span id="msg_pwd">5-10位数字,字母,下划线</span>
				</div>
				<div>
					<input type="submit" value="登录">
				</div>
			</form>
		</body>

		<style type="text/css">
		.ok{
			color: #0f0;
		}
		.error{
			color: #f00;
		}
		</style>

		<script type="text/javascript">
			function checkUser(){
				//获取有户名的字符串
				var code=document
				.getElementById("username").value;
				//获得span对象
				var span=document.getElementById("msg_user");
				//获得正则对象
				//5-10位数字,字母,下划线
				var reg=/^\w{5,10}$/;
				//开始验证
				if(reg.test(code)){
					//格式正确,span字体变绿
					span.className="ok";
					return true;
				}else{
					span.className="error";
					return false;
				}
			}
			function checkPwd(){
				var code=document
				.getElementById("pwd").value;
				var span=document.getElementById("msg_pwd");
				var reg=/^\w{5,10}$/;
				if(reg.test(code)){
					span.className="ok";
					return true;
				}else{
					span.className="error";
					return false;
				}
			}
		</script>

## 学子商城登陆页表单验证

![](2.png)

## function对象
### 1.js中函数就是function对象
### 2.函数名就是指向function对象的引用

    var fn1=function(){alert(1111);}
	function fn2(){
		alert(1111);
	}

### 3.使用函数名可以访问函数对象
### 4.函数名后面跟上(),是调用函数
### 5.函数的返回值

	- 不定义返回值的类型
	- 默认返回值是undefined
	- 可以使用return返回具体的值

### 6.函数的参数 var 

		function x(){
			alert(arguments[0]);
		}

		x();

		x(1,2);//不报错,问题是1和2究竟哪去了

![](3.png)

### JS的函数没有重载
### 函数被调用时,只要函数名一样,无论传入多少个参数,调用的都是同一个函数对象,所以js没重载
### 但是可以实现和重载一样的调用方式,使用arguments

### 代码演示 

### 定义一个函数,参数连续相加,返回累加和
		
		function add(){
		  var sum=0;
		  for(var i=0;i<arguments.length;i++){
		     sum+=arguments[i];
		  }
		  return sum;
		}

### js在调用函数的过程中,只检测函数名,不检测参数列表
### 如果参数名称匹配,则直接调用
### 可以使用arguments访问传递过来的参数列表
### js中没有重载,如果出现相同函数名的两个函数,后一个有效


### 匿名函数
### 就是不给函数起名字
### 如果一个函数在别的地方不再被调用了,就可以使用匿名函数


### 全局函数
### 全局函数可用于所有的javaScript对象
### 不需要对象调用
### 常用全局函数

		typeof()
		isNaN();
		parseInt();
		parseFloat();

### eval()
### eval函数用于 计算 表达式 字符串

		var str="2+3"; 	
		eval(str);

### eval函数用于 执行 字符串中的js代码

		var str="function aa(){alert(1111);}aa();";
		eval(str);

### eval最重要的作用,是动态执行服务器传过来的javascript代码

		<body>
			<input type="text" id="num">
			<input type="button" value="计算" 
			onclick="cal();">
		</body>

		<script type="text/javascript">
		function cal(){
			var input=document.getElementById("num");
			var num=input.value;
			//开始计算
			try{
				input.value=eval("("+num+")");
			}catch(e){
				input.value="Error";
			}
		}
		</script>
		
## 外部对象概述
### BOM与DOM

![](4.png)

### BOM Browser Object Model 浏览器对象模型
### DOM Document Object Model 文档对象模型

### 总结:通过BOM,可以移动窗口,更改状态栏文本
### 执行其他不与页面内容发生直接联系的操作(不操作标签)
### BOM是没有标准,却被浏览器厂商广泛支持

### 总结:DOM定义了访问和操作HTML的标准方法
### 通过对DOM树的操作,来实现对html文档数据的操作

## JS相关BOM操作
### window 表示整个浏览器窗口
### 所有js的全局对象,全局函数以及全局变量,都自动成为window对象的成员(window可以点出来)

### window的常用属性

		document  窗口中显示的HTML文档对象
		history   浏览过的历史记录对象
		location  窗口文件地址对象
		screen    屏幕对象
		navigator 浏览器相关信息对象

## window对象常用的函数

1. 弹出框


		<body>
			<input type="button" value="按钮1"  
			onclick="fn1();">
			<input type="button" value="按钮2"  
			onclick="fn2();">
			<input type="button" value="按钮3"  
			onclick="fn3();">
		</body>

		<script type="text/javascript">
			//1.弹出框
			function fn1(){
				window.alert("你好");
			}
			//2.确认框
			function fn2(){
				var flag=window.confirm("how are you!!");
				console.log(flag);
			}
			//3.输入框
			function fn3(){
				var str=window.prompt("中午吃的什么?");
				console.log(str);
			}
		</script>


## 定时器
### 主要用于网页动态时钟,倒计时,轮播图,无缝滚动,跑马灯效果

### 1.周期性定时器
### 以一定的时间间隔执行代码,循环往复
	
	setInterval(exp,time);
	exp:要执行的js语句,一般为匿名函数
	time:时间周期,毫秒 
	返回值:返回已经启动的定时器ID
	clearInterval(ID);停止定时器

	//周期性定时器
	function fn4(){//每一秒打印一个数 5,4,3,2,1
		var num=5;
		var id=setInterval(function(){
			console.log(num--);
			if(!num){// num==0
				clearInterval(id);
			}
		},1000);
		console.log("蹦蹦");
	}

### 总结:启动定时器就相当于启动了一个子线程
### 当前方法fn4相当于主线程
### 2个线程之间并发执行,相互不等待

### 课堂练习,电子时钟

![](5.png)

	<div>
		<input type="button" value="开始" onclick="start();">
		<input type="button" value="停止" onclick="stop();">
		<p id="clock"></p>
	</div>

		<style type="text/css">
			#clock{
				width: 200px;
				height: 30px;
				border: 2px solid #f00;
				text-align: center;
				line-height: 30px;
				font-size: 20px;
			}
		</style>

![](6.png)

		<script type="text/javascript">
		var id;
		function start(){
			if(id){//id在undefined和null的情况才会启动定时器
				return;
			}
			var oP=document.getElementById("clock");
			id=setInterval(function(){
				var d=new Date();
				var now=d.toLocaleTimeString();
				oP.innerHTML=now;
			},1000);
		}
		function stop(){
			//id非空时,定时器处于启动状态,这样可以停止
			if(id){
				clearInterval(id);
				//如果此时不给ID赋值null
				//下次点击启动时,会进入if块直接返回.
				id=null;
			}
		}
		</script>





### 2.一次性定时器(延迟执行)
### 在一个设定好的时间 间隔之后来执行代码

		setTimeout(exp,time);
		exp:执行的代码
		time:延迟时间
		返回值为id
		clearTimeout(id);

### 发送撤销的案例

![](7.png)

		<script type="text/javascript">
		   var id;
			function send(){
				var oP=document.getElementById("msg");
				oP.innerHTML="发送中...";
				//推迟三秒发送
				id=setTimeout(function(){
					oP.className="ok";
					oP.innerHTML="发送成功";
				},3000);
			}
			function cancel(){
				var oP=document.getElementById("msg");
				oP.className="error";
				oP.innerHTML="已撤销";
				clearTimeout(id);
			}
		</script>
		<style type="text/css">
		.ok{
			color: #0f0;
		}
		.error{
			color: #f00;
		}
		</style>
		</head>
		<body>
			<div>
				<input type="button" value="发送" 
				onclick="send();">
				<input type="button" value="撤销" 
				onclick="cancel();">
			</div>
			<p id="msg"></p>
		</body>

## 作业
1. 今天笔记过一遍
2. 学子商城登陆页面表单验证,敲一遍
3. 两个定时代码(第二个调BUG)
4. 预习DOM




















