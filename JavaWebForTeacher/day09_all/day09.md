# day09
## 复习
### function对象
		
	1. 返回值
	2. 参数

### 外部对象

### BOM和DOM的关系
### window
### 定时器
		
## window 常用属性

### 1. location对象
### location对象包含当前页面的URL的信息
### 常用于获取和改变当前浏览器的网址
### 属性,href  location.href=url
### reload();重新载入当前网页,等同于刷新按钮

	<input type="button" value="location" 
	onclick="fn1();">


	function fn1(){
		//跳转到目标url
		//location.href="http://www.tmooc.cn/web/index_new.html?tedu";
		//刷新
		//location.reload();
		var flag=confirm("你确定要离开本宝宝吗?");
		if(flag){
			location.href="http://www.tmooc.cn/web/index_new.html?tedu";
		}
	}


### 2.screen
### 包含有关各户端显示屏幕的信息
### 常用于获取屏幕的分辨率和色彩

	1. width/height
	2. availWidth/availHeight

### 总结,可用高,除了window的任务栏之外的高度

### 3.history
### 包含用户在浏览器窗口中访问过的URL
### length属性,浏览器历史列表中的url数量
### 方法:

		1. back()
		2. forward();
		3. go();//0是当前页,-1上一页 1下一页

### 4.navigator
### 包含浏览器的相关信息
### userAgent属性,当前浏览器的版本;

## DOM的操作
### DOM提供哪些操作

	1. 查找节点

	<p id="p1">1. <b>读写</b>节点</p>
	<p id="p2">2. <b>查询</b>节点</p>
	<p id="p3">3. <b>增删</b>节点</p>

	//var p1=document.getElementById("p1");
	//var p2=document.getElementsByTagName("p")[1];
	//console.log(p2);
	//console.log(p1);
	//console.log(p1.nodeName);
	//console.log(p1.nodeType);

	总结:nodeType返回值,对应了节点的类型
		
		1 --- 元素节点
		2 --- 属性节点
		3 --- 文本节点
		8 --- 注释节点
		9 --- 文档节点

		nodeName和nodeType,在写js框架时用的非常多
		正常开发,很少使用

	2. 读取节点信息
		
		双标签叫内容,
		所有的双标签都有内容,
		一般表单中的控件,数据称之为值
		input select textarea都有value

		<div>今天天气不错</div>
		<input type="button" value="适合睡觉"> 

		2.1 innerHTML
		2.2 innerText


	<p id="p1">1. <b>读写</b>节点</p>
	<p id="p2">2. <b>查询</b>节点</p>
	<p id="p3">3. <b>增删</b>节点</p>

	var p1=document.getElementById("p1");
	console.log(p1.innerHTML);
	console.log(p1.innerText);
	//p1.innerHTML="1. <u>读写</u>节点";
	p1.innerText="1. <u>读写</u>节点";

	总结:innerHTML,认识标签
		 innerText,不认识标签,会把标签当成字符串

		2.3 读写值

			btn.value;

### 2.4读写节点的属性

	1. 通过方法读写属性**

	//1.通过方法读写属性
	var oImg=document
	.getElementsByTagName("img")[0];
	oImg.setAttribute("src","../img/02.png");
	console.log(oImg.getAttribute("src"));

	2. 通过标准属性名读写属性**

	//2.通过标准的属性名读写属性
	//className,id,style
	var oP=document.getElementsByTagName("p")[0];
	console.log(oP.style.color);
	oP.style.fontSize="30px";

	3. 通过不标准属性名读写属性,只有高版本浏览器才支持

	//3.通过不标准属性名读写,不推荐
	// a.href img.src
	//使用方法去解决,不建议用
	console.log(oImg.src);

### 总结:
### 1.不标准的属性建议使用方法处理
### 2.标准属性中的style,是内联样式.除了学习和测试不建议使用

	3. 修改节点信息
	4. 创建新节点
	5. 删除节点

### 提高题,完全不要求.而且不建议做
### 只要会一个方框,从上挪到下,就可以了
### 最多两个方框


### 鼠标悬停和鼠标离开事件

	onmouseover鼠标悬停
	onmouseout鼠标离开

		<div onmouseover="stop();" onmouseout="go();">
			<img src="../img/08.png" class="hide">
			<img src="../img/06.png" class="hide">
			<img src="../img/13.png" class="hide">
			<img src="../img/16.png" class="hide">
			<img src="../img/15.png" class="hide">
			<img src="../img/12.png" class="hide">
			<img src="../img/14.png" class="hide">
		</div>
		
		div{
			width: 256px;
			height: 256px;
			margin: 50px auto;
			border: 2px solid #f00;
		}
		.show{
			display: block;
		}
		.hide{
			display: none;
		}

		<script type="text/javascript">
		var n=1;//轮播总次数
		var id;//定时器的ID
		var imgs;
		window.onload=function(){
		    imgs=document.getElementsByTagName("img");
			//先把第一张显示
			imgs[0].className="show";
			//定时启动轮播
			go();
		}
		function go(){
			id=setInterval(function(){
				//计算要显示图片的下标
				//轮播总次数%数组长度
				var index=n%imgs.length;
				//隐藏全部图片
				for(var i=0;i<imgs.length;i++){
					//imgs[i].className="hide";
					imgs[i].setAttribute("class","hide");
				}
				//显示对的index图片
				imgs[index].className="show";
				//轮播总次数+1
				n++;
			},500);
		}
		function stop(){
			clearInterval(id);
		}
		</script>

### 1. 查询节点

1. 如果想要操作HTML元素,必须先要找到该元素
2. 查询节点方式方法

	2.1 通过id查询
	2.2 通过层次(节点关系)查询
	2.3 通过标签名称查询
	2.4 通过name属性查询

		<body>
			<ul>
				<li>北京</li>
				<li>上海</li>
				<li id="gz">广州</li>
				<li>深圳</li>
				<li>佳木斯儿</li>
				<li>葫芦岛</li>
			</ul>
			<div>
				<input type="radio" name="gender">男
				<input type="radio" name="gender">女
			</div>
		</body>


		<script type="text/javascript">
		window.onload=function(){
			//1.根据id查询
			//var gz=document.getElementById("gz");
			//2.根据标签层次查询(节点关系)
			//2.1查询父节点
			//console.log(gz.parentNode);
			//2.2查询孩子,子节点
			//var oUl=document.getElementsByTagName("ul")[0];
			//console.log(oUl.childNodes);
			//把查询节点的方位缩小到ul内部(重点掌握)
			//var oLis=oUl.getElementsByTagName("li");
			//console.log(oLis);
			//2.3查询兄弟节点
			//某节点.父亲.孩子们[index]
			//var gz=document.getElementById("gz");
			//var jms=gz.parentNode
			//.getElementsByTagName("li")[4];
			//console.log(jms);
			//2.4根据name属性查询节点
			//一般用于查询一组单选/多选
			var radios=document.getElementsByName("gender");
			console.log(radios);
		}
		</script>

### 创建新节点

		document.createElement(TagName);
		TagName:要创建的元素的标签名称
		返回值,就是这个标签的对象

		把这个新标签对象,挂到dom树上

### 追加

		<body>
			<div></div>
		</body>

		<script type="text/javascript">
		window.onload=function(){
			//创建新节点
			var newNode=document.createElement("input");
			//设置节点信息
			newNode.setAttribute("type","text");
			newNode.value="mary";
			newNode.style.color="red";
			//挂到DOM树上,必须使用父级元素添加新节点
			//获取父级元素对象
			var oDiv=document.getElementsByTagName("div")[0];
			console.log(oDiv);
			//通过父对象,把新节点挂在父对象下面
			oDiv.appendChild(newNode);
		}
		
		</script>

### 插入
### 删除

		<body>
			<ul>
				<li>北京</li>
				<li>上海</li>
				<li id="gz">广州</li>
				<li>深圳</li>
				<li>佳木斯儿</li>
			</ul>
			<div>
				<input type="button" value="追加"   
				onclick="fn1();">
				<input type="button" value="插入"   
				onclick="fn2();">
				<input type="button" value="删除"   
				onclick="fn3();">
			</div>
		</body>

		function fn1(){
			var oLi=document.createElement("li");
			oLi.innerHTML="重庆";
			var oUl=document.getElementsByTagName("ul")[0];
			oUl.appendChild(oLi);
		}
		function fn2(){
			var oLi=document.createElement("li");
			oLi.innerHTML="铁岭";
			//插入需要父级对象,和弟弟对象
			var oUl=document.getElementsByTagName("ul")[0];
			var gz=document.getElementById("gz");
			//把新节点插入到父亲下级,弟弟之前
			oUl.insertBefore(oLi,gz);
		}
		function fn3(){
			//需要父级元素对象和要删除的元素对象
			var oUl=document.getElementsByTagName("ul")[0];
			var gz=document.getElementById("gz");
			//通过父级对象删除孩子
			oUl.removeChild(gz);
		}

### 总结,我们需要父级去删除子元素

## 作业:

1. 7个demo都敲一遍
2. 必须把新建元素,挂到dom树上的代码,敲熟悉
3. 删除元素必须熟悉
4. 了解window的4个属性

















