[toc]

## 设置网页的本经

- 背景颜色
	 - 语法：`background-color: 颜色取值;`
	 - 默认值是**透明色**。
- 背景图像
	- 语法：`background-image: url(图像地址)`

## 设置背景图像的属性

- 设置背景重复
	- 语法：`background-repeat: 取值;`
	- 取值有 no-repeat / repeat / repeat-x / repeat-y。
		- no-repeat 背景图像不重复，只显示一次。
		- repeat 默认，在垂直和水平方向上重复。
		- repeat-x 只在水平方向上重复。
		- repeat-y 只在垂直方向上重复。
- 设置固定背景
	- 语法：`background-attachment: 取值;`
	- 取值有 scroll / fixed。
		- scroll 背景图像随对象内容滚动。
		- fixed 背景图像固定。
- 设置背景定位
	- 语法：`background-position: 数值x 数值y;`

## 设置网页图像的样式

- 设置图像边框
	- 语法：`border: 宽度 类型 颜色;`

|类型值|描述|
|-|-|
|none|无边框|
|dotted|点状边框（在大多数浏览器中呈现为实线）|
|dashed|虚线边框（在大多数浏览器中呈现为实线）|
|solid|实线边框|
|double|双线边框|
|groove|3D 凹槽边框|
|ridge|3D 垄状边框|
|inset|3D 凹陷效果边框|
|outset|3D 凸出效果边框|

- 设置图文混合排版
	- 语法：`float: 属性值`
	- 取值有 left / right / none。
		- none 表示无浮动。
		- left 表示元素向左浮动。
		- right 表示元素向右浮动。

## 应用 CSS 滤镜设计图像特效

- 控制图像和背景的透明度
	- 语法：`filter: Alpha(参数1 = 参数值, 参数2 = 参数值, ...)`

|参数|含义|
|-|-|
|opacity|设置对象的不透明度，取值范围 0~100，默认值为 0。|
|finishopacity|设置对象透明渐变的结束透明度，取值范围 0~100。|
|style|指定渐进的形状，0 为无渐进，1 为直线渐进，2 为圆形渐进，3 为矩形渐进。|
|startx|设置透明渐变开始点的水平坐标，默认值为 0。|
|starty|设置透明渐变开始点的垂直坐标。|
|finishx|设置透明渐变结束点的水平坐标。|
|finishy|设置透明渐变结束点的垂直坐标。|

- 灰度
	- 将一幅图片变为**灰度图**。
	- 语法：`filter: Gray;`
- 反色
	- 将对象的可视化属性全部**翻转**。
	- 语法：`filter: Invert;`
