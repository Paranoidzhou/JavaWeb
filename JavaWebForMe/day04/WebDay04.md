## CSS选择器

#### 选择器的作用、就是为了选出当前页面中符合要求的一个或者多个标签。

1. 标签选择器:
>     h2{ color:#f00}
       p{}
       a{}
       input{}

2. id选择器- - ->由于一个html中、id都是唯一的，所以id选择器的作用码是选取当前页面中符合要求的一个标签。**【注意重点：一个】**
>       <h3 id="h"> id选择器</h3>
>       #h{color:#f00;}
![](1.png)

3. 类选择器(class选择器)
>	    <h2 class="w300">类选择器</h2>
       .w300{width:300;}
>---
>      .col{ color:#006699;}
	   .w100{
			border:1px solid red;
			width:100px
		}
        <h2 class="col w100"> 类选择器 </h2>
		<p class="col w100">类选择器</p>
		<span class="col">类选择器</span>

4. 派生选择器：可以通过父标签找到符合要求的子孙标签。
>        <style type="text/css">
			ul li span a{ color:#f00; }
			ul li .gz{ color:#7C001f; }
			ul li a{ color:#0f0; }
			ul a{ color:#0f0; }    子孙标签都算
	    </style>
		  <body>
			<ul>
				<li><a href="#">北京</a></li>
				<li><a href="#">上海</a></li>
				<li><a href="#" class="gz">广州</a></li>
				<li><span><a href="#">深圳</a></span></li>
			</ul>
>	    </body>

5. 子类选择器：根据父标签、找到符合要求的子标签。
>		ul>a{ color:#0f0; }    子类选择器：只针对儿子下手
  		<a href="#">佳木斯儿</a>

6. 伪类选择器：在一系列动作中，添加某种样式。
>  :hover- -鼠标悬停和鼠标离开
>      <a class = "gz">....</a>
		<div id="d1"> 伪类选择器的演示 </div>

> 总结：选择器（派生/子类）写的越具体、优先级越高。【当选择器一致时、就进原则】

## CSS常用样式属性
- 布局相关：单位：px / 100%
     width:设置宽
     height:设置高
     margin:设置外边距
>       margin:10px;同时控制4个外边距的距离。
>       margin:10px  20px;意味着上下为10px，左右为20px.
>       margin:0px auto;块级标记的水平居中
>       margin:10px  20px  30px  40px; 分别代表上右下左。
>---
>       margin-top:设置上外边距。
>       margin-right:设置右边距。
>       marginbottom:设置下边距。
>       margin-left:设置左边距。

     padding:设置内边距
>		padding:10px;  同时控制4个方线的内边距。
>		padding:10px 20px;  意味着上下10px,左右20px.
>		padding:10px 20px 30px 40px; 分别代表上右下左。
>---
>	    padding-top：设置上内边距
>	    padding-right：设置右内边距
>	    padding-bottom：设置下内边距
>	    padding-left：设置左内边距

- 总结1：一个div如过不设置宽度则默认占父容器宽度的100%。
- 总结2：一个div如果不设置高度则默认高度为0px。如果有内容，那么内容多高，div就撑起多高。
- 总结3：盒子模型、元素之间的留白，元素背景的填充范围，元素的大小，这些东西的控制规定方在一其，就是和子模型。盒子模型一般用于集选整体布局的宽度。
> - 一个元素占用页面的宽度计算公式为：
> - 左外边距+左边框+左内边距+内容取与宽度+右内边距+右边框+右外边距

- 背景相关属性(background)：
> - background-color：背景颜色
> - background-image：背景图片
> - background-repeat：背景图片的平铺方式
> - background-position：背景图片的位置
> - background-size：背景图片的大小
> - - -
> - - background - color:背景颜色：
> - - 颜色值可以如下设置：
```
       1.纯英文单词，类似于red、green等...
       2.#ffffff 6位16进制字符串。例如：#006699
       3.#f00 相当于 #ff0000
       4.RGB(255,255,255)。0-ff == 0-255
       5.RGBa(255，255，255，0-1)：a是阿尔法、透明度的意思；数值1不透明、0.5半透明、0全透明。
```
> - - -
> - - **background-image:背景图片：**
> - - div设置了背景图片，那么div内部的元素将会在背景图片之上显示。
> - - -
> - - **background-repeat：背景图片的平铺方式 :**
```
       1.background-repeat:no-repeat; (不平铺)
       2.background-repeat:repeat; (平铺)
       3.background-repeat:repeat-x; (横向平铺)
       4.background-repeat:repeat-y; (纵向平铺)
```
> - - -
> - -**background-position：背景图片的位置 :**
> - - center / top / bottom / left / right / 具体数值
```
     background-position : x轴 y轴;
     backgrund-position:right bottom;
     backgrund-position:270px 20px;
     backgrund-position:center center;
```
> - -**background-size：背景图片的大小 :**
```
        background-size:330px 350px;
```

### 课堂练习：
```
    #d0{
        width: 1000px;
        height: 376px;
        margin: 0px auto;
    }
    #d1{
        width: 611px;
        height: 376px;
        background-color: #e8e8e8;
        background-image: url("../images/itemCat/study_computer_img1.png");
        background-repeat: no-repeat;
        background-position: 270px 20px;
        background-size:330px 350px; 
        margin-left: 2px;
        margin-right: 10px;
        float: left;/* 左浮动,为了让块级元素在一行显示 */
    }
    #d3{
        width: 375px;
        height: 376px;
        float: left;
        background-color: #e8e8e8;
        background-image: url("../images/itemCat/study_computer_img2.png");
        background-repeat: no-repeat;
        background-position: 84px 112px;
        background-size:296px 232px;
        margin-right: 2px;
    }
    #d2{
        width: 245px;
        height: 232px;
        margin-top: 68px;
        margin-left: 36px;
        padding: 5px;
    }
    .p1{
        color: #333;/* 字体颜色 */
        font-size: 32px;/* 字号大小 */
        font-weight: lighter;/* 字体权重(粗细) */
        margin-bottom: 12px;
        font-family: "黑体";/* 字体种类 */
    }
    .p2{
        color: #666;
        font-family: "黑体";
        font-size: 12px;
        font-weight: lighter;
        margin-bottom: 1px;
        margin-top: 0px;
    }
    .p3{
        margin-bottom: 12px;
        color: #0aa1ed;
        font-size: 24px;
        font-weight: bold;
    }
    input{
        width: 132px;
        height: 40px;
        font-size: 20px;
        color: #fff;
        background-color: #0aa1ed;
        font-family: "黑体";
    }
    #d1:hover{
        background-size:400px 410px;
        background-position: 250px 0px;
    }
    </style>
        <body>
        <div id="d0">
            <div id="d1">
                <div id="d2">
                    <p class="p1">灵越 燃7000系列</p>
                    <p class="p2">酷睿双核i5处理器|256GB SSD| 8GB内存</p>
                    <p class="p2">英特尔HD显卡620含共享显卡内存</p>
                    <p class="p3">￥4999.00</p>
                    <input type="button" value="查看详情">
                </div>
            </div>
            <div id="d3">
                <div id="d2">
                    <p class="p1">颜值 框不住</p>
                    <p class="p2">酷睿双核i5处理器|256GB SSD| 8GB内存</p>
                    <p class="p2">英特尔HD显卡620含共享显卡内存</p>
                    <p class="p3">￥6888.00</p>
                    <input type="button" value="查看详情">
                </div>
            </div>
        </div>
    </body>
```
![](2.png)

>小知识点：微调（调位置用margin）,（调大小用padding)！！！！
>小知识点： margin: 0px auto;(针对块级元素的居中而非字体)

- 字体相关属性：
> - font-size：字体大小 -> 单位：px / cm / em
> - - em:是一个想对度量单位.1em -> em随基础字号变化（用于屏幕自适应）
> - font-family：设置字体 -> “微软雅黑” / “黑体”
> - font-weight：设置字体的粗细(磅值) -> 100pt / lighter(细一点) / normal(正常) / bold(粗一点) / bolder(比粗更粗)
> - font-style：设置字体样式 -> normal（正常） / italic(斜体)

       <style typ="text/css">
			#d1{
				width: 50%;
				height: 200px;
				border: 3px solid #aaa;
				font-size: 40px;
				font-family: "黑体";
				font-weight: bolder;
				font-style: italic;
			}
		 </style>
	  </head>
	   <body>
		  <div id="d1">测试font的div标签</div>
	   </body>

- 文本属性：
> - color：设置字体颜色.
> - text-align：文本的对齐方式 -> left(左对齐) / center（居中） / right（右对齐）
> - text-decoration:文本装饰
> - - text-decoration:none; -> 给a标签去除下划线。
> - - text-decoration: underline; ->给文本设置下划线。
> - - text-decoration: line-through; ->给文本设置一条删除线。
> - - text-decoration: overline; ->给文本设置上划线。
> - line-height:设置文本行高：由于div的文本在默认情况下根据行高垂直居中、所以如果希望文本在div垂直居中显示，只需要把行高属性设置为div的高度。但是此处存在Bug、如果字数过多需要折行，那么行高的效果会每一行都遵循。

- 边框属性：
> - border:1px solid black;
> - - border-width:边框的宽度
> - - border-color:边框的颜色
> - - vorder-style:边框的样式 solid
> - - -> border-top:2px solid black; 设置上边框
> - - -> border-top-width:设置上边框宽度
> - - -> border-top-color:设置上边框的颜色
> - - -> border-top-style:设置上边框的样式
>
> 扩展:border-top / left / right / bottom :可以分开设置上下左右边框的宽度、颜色、样式
> - border:none;去除边框
                border-top: 20px solid red;      /*  实线  */
				border-left: 5px dotted blue;    /*   点   */
				border-right: 30px double green; /* 双实线 */
				border-bottom:30px dashed gray;  /*  虚线 */
> - border-radius:3px(原角半径);设置边框原角
> - 溢出属性： overflow
> - - 参数：visible：溢出部分可见
> - - 参数：hidden：溢出部分隐藏
> - - 参数：scroll：溢出部分显示滚动条

##### >总结：
#####       1.确定宽高(div不写宽默认是父级的宽)
#####       2.考虑背景问题（颜色和图片）
#####       3.内部字体问题（字号、颜色、字体、对齐）
#####       4.位置的微调(margin padding 浮动 定位)
#####  注意： margin会移动元素的位置>padding会改变元素占据页面的大小。

- 常见复杂属性：
> - disply 控制元素的显示方式
> - - disply:block; -> 按照块级元素进行显示。
> - - disply:inline; -> 按照行内元素进行显示。(一般不用)
> - - disply:inline-block; -> 行内块，与其他行内元素（包括行内块）共占一行，同时可以改变宽高、上右下左外边距。【会出现BUG，不建议使用。】
> - - disply:none; -> 隐藏元素。
           span{
				display: block;
				width: 200px;
				height: 200px;
				border: 2px solid red;
				font-size: 20px;
				color:rgb(0,0,255);
				margin-top:100px;
			}
           <span>我是span,是一个行内元素</span>

>总结：
> - 行内元素:一行中可以有多个，从左往右依次摆放行内元素、宽高、上下外边距失效，内边距无影响。（大小由内容撑起）
> - 块级元素：独占一行，只有块级元素可以设置宽高和上下外边距。（大小自行设置）

## **浮动 float**
- float : left; 元素浮动起来往左放。
- float : right; 元素浮动起来往右放。
- ->一旦元素设置了浮动属性、当前元素会脱离默认文档流，在默认文档流之上进行渲染绘制。
>总结：元素浮动后，先前的位置将会被其他元素占用。float最常见的用法,是把块级元素横向排列

- clear:both,清除浮动。本标签部被上面浮动的其他标签覆盖。