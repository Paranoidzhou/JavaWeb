## BOM 对象的一些属性：

### location对象：
- location对象包含当前页面的URL的信息。

- 常用于获取和改变当前浏览器的网址。
  
- 常见属性：href
		location.href = url;
		
		//跳转到目标url
		var flag = confirm("你确定要离开本宝宝吗？");
		if(flag){
			location.href="http://www.tmooc.cn";
		}
		<input type="button" value="location" onclick="fn1();">

- reload(); 重新载入当前网页（等同于刷新）
		loction.reload();  //重新载入当前页面

### screen 对象：
- 包含有关各客户端显示屏幕的信息，常用于获取屏幕的分辨率和色彩。
		width/height            	  宽   /   高
		availWidth/availHeight      可用宽 / 可用高
		
		screen.availWidth   ：获取当前屏幕可用宽度
		screen.availHeight  ：获取当前屏幕可用高度

> 总结：可用高是除了window的任务栏之外的高度，非屏幕全屏。

### history 对象:
- 包含用户在浏览器窗口中访问过的URL。

- lebgth属性，浏览器历史列表中的url数量。
		history.length;

- 方法：
		back();          //返回上一个页面
		firward();       //去下一个页面
		go(参数);        //go(0)类似于刷新本页面、go(1)下一页、go(-1)上一页。 括号填几就跳转到哪个页面

### navigator 对象：
- 包含浏览器的相关信息。
- userAgent属性； 可查询当前浏览器的版本

## DOM的操作：
### DOM提供了哪些操作：

一、查找节点：

		/* 页面加载事件，页面加载完毕激活script代码 */
		window.onload=function(){
			var p1 = document.getElementById("p1");
			var p2 = document.getElementsByTagName("p")[1];
			console.log(p2);
			console.log(p1.nodeName);  //返回当前节点标签名
			console.log(p1.nodeType);  //返回当前节点对象的类型
		}
		
		<body>
			<p id="p1">1. <b>读写</b>节点</p>
			<p id="p2">2. <b>查询</b>节点</p>
			<p id="p3">3. <b>增删</b>节点</p>
		</body>


		总结： nodeType:返回值，对应了节点的类型：
		1. --- 元素节点
		2. --- 属性节点
		3. --- 文本节点
		8. --- 注释节点
		9. --- 文档节点
		nodeName和nodeType,在写js框架时用的非常多、正常开发很少使用。

二、读取节点信息：
		
		1.双标签（有开有关）内的文字叫内容、所有的双标签都有内容,一般表单中的控件数据称之为值。
		例如：inpput / select / textarea都有value
		2.单标签内的文字叫值。

		<div>今天天气真不错</div>
		<input type="button"  value="适合睡觉">
		
		* innerHTML：读某个标签内容所有的标签和文本（能解析渲染标签）
		* innerText：只读某个标签内容所有文本     （无法解析渲染标签,会把标签当字符串）
		  实例代码：
		  p1.innerHTML="innerHTML能解析渲染标签内的所有内容:<u>重点</u>";
		  p2.innerText="innerText只能读/写无法解析渲染标签内的所有内容:<b>重点</b>"

		* 读写值：
		  btn.value;

* **读写节点的属性：**
  1.通过方法读写属性：【重点】

		var oImg=document.getElementsByTagName("img")[0];
		console.log(oImg.getAttribute("src"));      //读属性
		oImg.setAttribute("src","../img/09.png");   //写属性

		<img src="../img/06.png">

  2.通过标准属性名读写属性： 【重点】

		// className / id / style :都是标准属性名
		var oP = document.getElementsByTagName("p")[0];
		console.log(oP.style.color);
		oP.style.fontSize = "100px";

		<p style="color:#f00;" align="center"> 标准属性就那么几个 </p>

  3.通过不标准属性名读写属性，只有高版本浏览器才支持：
		
		// a.href / img.src
		console.log(oImg.src);

> 总结：
> 1.不标准的属性建议使用方法
> 2.标准属性就几个,而且标准属性中的style是内联样式，除了学习和测试不建议使用

## 轮播图练习：
### 鼠标悬停和鼠标离开时间：
    onmouseover：鼠标悬停
	onmouseout：鼠标离开
		<title>假的轮播图的演示</title>
		<script type="text/javascript">
			var n = 1;
			var id;
			var imgs;
			window.onload=function(){
				//1.获取图片
				imgs = document.getElementsByTagName("img");
				imgs[3].className="show";
				go();
			}
			
			function go(){
				//3.用定时器启动轮播总次数
				id = setInterval(function(){
					//4.计算要显示图片的下标、公式为：轮播总次数 % 数组长度
					var index = n % imgs.length;
					
					for( i=0;i<imgs.length;i++ ){  //设置隐藏全部图片
						imgs[i].setAttribute("class","hide");
					}
					imgs[index].className="show";
					
					n++;  //总次数+1;
					
				},500);
			}
			
			function stop(){
				clearInterval(id);
			}
		</script>
		<style type="text/css">
			div{
				width:1000px;
				height:350px;
				margin: 50px auto;
				border:  5px solid #f0f;
			}
			.hide{
				display: none;
			}
			.show{
				display: block;
			}
		</style>
		</head>
		<body>
			<div onmousemove="stop();" onmouseout="go();">
				<img src="../image/1.jpg" class="hide">
				<img src="../image/2.jpg" class="hide">
				<img src="../image/3.jpg" class="hide">
				<img src="../image/4.jpg" class="hide">
			</div>
		</body>

三、查询节点：
- 如果想要操作HTML元素，必须要先找到该元素
- 查询节点方式方法：
  1.通过id查询:
		var bj = document.getElementById("bj");
		console.log(bj);

  2.通过层次（节点关系）查询:
		
		console.log(bj.parentNode);     //查询父节点
		
		var oUl = document.getElementsByTagName("ul")[0]; //先获取想要查询子标签的父标签名

		console.log(oUl.childNodes);	//查询子节点

		var oLis = oUl.getElementsByTagName("li"); //通常都会把查询节点的方位缩小到ul内部（重点掌握）
		console.log(oLis);
		
		var gz = document.getElementById("gz"); //查询兄弟节点：某节点.父亲.孩子们[index]
		var jms= gz.parentNode.getElementsByTagName("li")[5];
		console.log(jms);
		
  3.通过标签名查询：
		var oUl = document.getElementsByTagName("ul")[0]；
		var oLis = oUl.getElementsByTagName("li");

  4.通过name属性查询：

		/*根据Name属性查询节点:一般用于查询一组单选或者多选框*/
		var radios = document.getElementsByName("gender");	
		console.log(radios);

四、创建新节点：

		document.createElement(TagName);
		TagName:要创建的元素的标签名称；
		返回值：就是这个标签的对象;
		把这新标签对象，挂到dom树上才能使用新节点。
		
		<title>创建新节点的演示</title>
		<script type="text/javascript">
			window.onload=function(){
				//1.创建新节点:
				var newNode = document.createElement("input");
				//2.设置节点信息：
				newNode.setAttribute("type","text");
				newNode.value = "框内文字";
				newNode.style.color = "red";
				//3.挂到DOM树上：必须使用父级元素添加新节点
				var oDiv=document.getElementsByTagName("div")[0];//获取父级元素对象
				oDiv.appendChild(newNode);    //通过父对象把新节点挂在父对象下面
			}
		</script>
		</head> 
		<body>
			<div></div>
		</body>


五、修改节点信息：
	


六、删除、追加、插入节点：

		function add(){      //追加
			var oLi=document.createElement("li");    //创建新节点
			oLi.innerHTML="重庆";
			var oUl = document.getElementsByTagName("ul")[0];
			oUl.appendChild(oLi);
		}		
				
		function insert(){	  //插入
			var oLi = document.createElement("li");
			oLi.innerHTML="铁岭";
			//插入对象需要父级对象、弟弟对象：
			var oUl = document.getElementsByTagName("ul")[0];
			var gz = document.getElementById("gz");
			//把新节点插入到父亲下级，弟弟之前
			oUl.insertBefore(oLi,gz);
		
		function del(){		 //删除
		 	//需要父级元素对象和要删除的元素对象:
			 var oUl = document.getElementsByTagName("ul")[0];
	 		 var gz = document.getElementById("gz");
	 		 //删除指定元素是通过其父级对象删除孩子
	 		 oUl.removeChild(gz);
		 }
	
		<body>
		<ul>
			<li>北京</li>
			<li>上海</li>
			<li id="gz">广州</li>
			<li>深圳</li>
			<li>葫芦岛</li>
			<li>佳木斯儿</li>
		</ul>
		<div>
			<input type="button" value="追加" onclick="add();">
			<input type="button" value="插入" onclick="insert()">
			<input type="button" value="删除" onclick="del()">
		</div>
		</body>
		}
> 总结：删除元素需要通过父级来删除，追加节点元素只需要创建新节点，插入元素则需要父级对象和弟弟对象。