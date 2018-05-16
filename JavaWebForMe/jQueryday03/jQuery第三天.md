### jQuery事件：

- dom事件，操作繁琐，并且有严重的兼容性问题。
- jQuery对dom做了封装，简化了操作，消除了兼容性问题

### 动态绑定事件：

```
$(function(){
		obj.click(function(){});     //简写形式
		obj.bind("click",function(){});   //完整语法，认识即可，可以不用。 
        });
```

### 关于Js的window.onload和$(function( ){ } )：

- window.onload 在同一个html文件上有多个，后者会覆盖前者。
- $(function(){}) 有多个，每一个都有效果。

### 事件对象event ：

​	

```
<title>jQuery动态事件的绑定+获取event</title>
		<script type="text/javascript" src="../jquery-3.1.1.min.js"></script>
		<script type="text/javascript">
			$(function(){
				$(":button:first").click(function(event){
					console.log(event);
				});
			});
		</script>
	</head>
	<body>
		<input type="button" value="按钮" >
	</body>
```



### 事件机制：

- 事件冒泡机制，事件从内向外传播

  ​        作用： 少些事件，获取事件源绑定一个事件。(例如Demo计算器)

  Js写法： event.stopPropagation();

  ​      	       event.cancelBubble = true;


- jQuery中取消冒泡的做法
       

    ```
     $(function{
        $(":button:eq(1)").click(function(){
                alert("button");
                return false;
        });
    
    	$("p:first").click(function(){
                alert("p");
    	});
    		$("div:first").click(function(){
                alert("div");
            });
        });
    
        <body>
        <input type="button" value="按钮" >
        <div>
            <p>
       		<input type="button"  value="我要冒泡了" >
            </p>
        </div>
        </body>
    ```

    

> jQuery中，取消时间冒泡，只需要在函数中添加return false即可；

### 获取事件源：

​	js      ：var obj = event.srcElement || event.target;

​	jQ     ：var obj = event.target;            // jQuery直接兼容

**小总结：jQuery为我们提供了一套统一简洁API。【jQuery对事件操作需要背】**

### 合成事件，jQuery对事件的特殊贡献，是噱头不是重点。

	<title>合成事件</title>
	<script type="text/javascript" src="../jquery-3.1.1.min.js"></script>
	<script type="text/javascript">
	$(function(){     
		$("img:first").hover(function(){
			$("img:first").addClass("big");
			$("img:first").attr("src","../img/14.png");
		},function(){
			$("img:first").removeClass();
			$("img:first").attr("src","../img/06.png");
		});  
		setInterval(function(){
			$("img:eq(1)").toggle(500);
		},500)
		
	});
	
	</script>
	<style type="text/css">
		.big{
			width: 30%;
		}
		.small{
			width: 256px;
		}
	</style>
	</head>
	<body>
		<img alt="" src="../img/06.png">
		<img alt="" src="../img/06.png"> 
	</body>

> hover（）相当于onmouseover和onmouseout的结合。
>
> toggle（）相当于hide（）和show（）方法的结合。

### 模拟事件：

- 电脑模拟人的行为，做了一些操作，激发了某些事件.

> 例如：电脑帮你点击、一个网站显示广告，既可以认为点×关掉，不点的话、2秒后电脑模拟点击了×，自动关闭广告，同时调用了绑定事件函数。

		obj.trigger(事件类型)
		$(":button").trigger("click");
代码：

```
<title>模拟事件，模仿Tmooc首页广告</title>
	<script type="text/javascript" src="../jquery-3.1.1.min.js"></script>
	<script type="text/javascript">
		$(function(){
				$(":button").click(function(){
					$("div:eq(0)").slideUp(500);
				});
				setTimeout(function(){
					$(":button").trigger("click");
				},3000);
		});
	</script>
	<style type="text/css">
		
		div{
			height: 600px;
			background: #006699;
			opacity: .3;
		}
		div input{
			margin: 5px;
			float: right;
		}

	</style>
</head>
<body>
	<div>
		<input type="button" value="X">
	</div>
```

### 动画：

- 网页的动效来提高用户体验，有专门的动效设计。

- 动画的本质，是使用定时器连续不断的修改样式来实现的、启动了定时器就相当于启动了子线程，它与事件本身是不冲突的，事件本身是主线程，两者并发执行，相互不等待。

  一、 显示隐藏：

  show() / hide() : 其作用时同时改变元素的宽度和高度来实现显示或隐藏（还包括透明度）。

  用法： obj.show / hide( 执行时间 ,回调函数 )：底层定时器实现，开新线程执行。

  ​       执行时间：slow normal fast 写毫秒数.

  ​       回调函数：指传给某一个方法的函数，在方法结束时运行。

  ```
  function show(){
  		$("img:eq(0)").show(999,function(){console.log("显示完成");});
  	}
  	function hide(){
  		$("img:eq(0)").hide(999,function(){console.log("隐藏完成");});
  	}
  	
  	<input type="button" value="显示" onclick="show();">
  	<input type="button" value="隐藏" onclick="hide();">
  ```

  二、上下滑动显示

  用法： obj.slideUp / down(执行事件，回调函数) ： 

  

  ```
  		function down(){
  			$("img:eq(1)>div").slideDown(999);
  		}	
  		function up(){
  			$("img:eq(1)>div").slideUp(999);
  		}
  		<input type="button" value="收起" onclick="up();">
  		<input type="button" value="打开" onclick="down();">		
  ```

  

  三、 淡入淡出

  - obj.fadeIn / fadeOut();

    ```
    	function movid(){
    		$("img:eq(1)").fadeOut(1000).show(1000).slideUp(1000);
    	}
    	<input type="button" value="淡入淡出" onclick="hint();">
    ```

    

  四、自定义动画，动起来

  - 自定义动画给予相对 / 绝对 / 固定定位.

    ​	animate(偏移位置,执行事件，回调函数);

    ​	偏移位置：{'left' : '500px'}          /* 描述动画执行之后元素的样式位置 */

    ```
    	function diy(){
    		$("img").animate({'left':'500px'},500)
    				.animate({'top':'200px'},200)
    				.animate({'left':'0px'},500)
    				.animate({'top':'00px'},200);
    	}
    	<input type="button" value="动动" onclick="diy();">
    ```

    
