[toc]

## 设计网页中的文字样式

使用 CSS 样式表可以定义丰富多彩的文字格式。

- 字体
	- 语法：`font-family: "字体1", "字体2", ...`
	- 浏览器从用户计算机中寻找**第一个字体**，如果计算机没有这个字体，就**向右**继续寻找。
	- 建议在设置中文字体属性时，应选择**宋体或黑体**。
	- 如果需要安装装饰性的字体，可以使用图片代替。
- 字号
	- 语法：`font-size: 取值`
	- 取值可以是绝对尺寸、相对尺寸、长度、百分比。

> 在 CSS 中，有两种单位，一种是绝对长度单位，包括英寸（in）、厘米（cm）、点（pt）等；另一种是相对长度单位，包括像素（px）等。

- 加粗
	- 语法：`font-weight: 粗度值`
	- 取值有 normal / bold / bolder / lighter / number。
		- normal 表示正常。（默认）
		- bold 表示粗体。
		- bolder 表示特粗体。
		- lighter 表示特细体。
		- number 指在 **100~900** 范围内具体的数值，一般情况下都是**整百**的数值。
			- 400 等价于 normal，700 等价于 bold。
- 样式
	- 语法：`font-style: 取值`
	- 取值有 normal / italic / oblique。
		- normal 表示正常。（默认）
		- italic 表示斜体。
		- oblique 表示倾斜。
- 变体属性
	- 将小写的英文字母转变为大写，而且保持与小写一样的尺寸高度。
	- 语法：`font-variant: 变体属性值`
	- 取值有 normal / small-caps。
		- normal 表示正常。（默认）
		- small-caps 表示将小写字母转换为大写字母。
- 文字装饰
	- 语法：`text-decoration: 取值`
	- 取值有 none / underline / overline / line-through / blink。

|text-decoration 取值|含义|
|-|-|
|none|默认值|
|underline|下划线|
|overline|上划线|
|line-through|删除线|
|blink|文字闪烁|

> IE、Chrome 或 Safari 不支持 `blink` 属性值

## 设计文本的段落样式

- 行高
	- 语法：`line-height: 数值`
	- 行距的常规比例是 **10:12**。
- 对齐
	- 语法：`text-align: 取值`
	- 取值有 left / right / center / justify
		- left 左对齐
		- right 右对齐
		- center 居中对齐
		- justify 两端对齐
- 缩进
	- 语法：`text-indent: 缩进值`
	- 缩进值必须是长度或百分比。
- 单词间距
	- 语法：`word-spacing: 取值`
	- 取值有 normal / 长度值。
		- normal 表示正常。（默认）
		- 长度值允许使用**负值**。
- 大小写转换
	- 语法：`text-transform: 转换值`
	- 转换值有 none / lowercase / uppercase / capitalize。
		- none 表示使用原始值。（默认）
		- lowercase 表示使每个单词的第一个字母大写。
		- uppercase 表示使每个单词的所有字母大写。
		- capitalize 表示使每个字的所有字母小写。

## 补：伪元素

参考资料：[W3School CSS 伪元素](http://www.w3school.com.cn/css/css_pseudo_elements.asp)

- 基本语法
	- `选择器 : 伪元素{属性1: 值1; 属性2: 值2; ...}`
- `first-line` 伪元素
	- 用于向文本的**首行**设置特殊样式。
	- 只可用于块级元素。
- `first-letter` 伪元素
	- 用于向文本的**首字母**设置特殊样式

> 例：实现首字下沉效果
```xml
<!DOCTYPE html>
<html>
<head>
    <title> 首字下沉 </title>
    <meta name="generator" content="Visual Studio 2015" />
    <meta name="author" content="Remilitarize" />
    <meta name="content-type" content="html/text; charset=utf-8" />
    <style type="text/css">
        <!--
        p{
            font-family:'宋体';
            font-size:20px;
            text-decoration:underline;     
            color:blue;
        }
        p:first-line{
            color:black;
            text-decoration:line-through;
        }
        p:first-letter{
            font-size:200%;
            font-weight:bold;
            float:left;
            color:red;
        }
        -->
    </style>
</head>
<body>
    <p>秋天来临了天空像一块覆盖大地的蓝宝石。<br />
    村外那个小池塘睁着碧澄澄的眼睛，凝望着这美好的天色。<br />
    一对小白鹅侧着脑袋欣赏自己映在水里的影子。<br />
    山谷里枫树的叶子，不知是否喝了过量的酒，红的像一团火似的。<br />
    村前村后的稻子，低着头弯着腰，在秋风中默默地等待着人们去收割，<br />
    半空中，排着“人”字形的雁群，高兴的唱着歌，告别人们，向天边慢慢飞去……</p>
</body>
</html>
```

## 用 CSS 滤镜设计特效文字

### 滤镜概述

滤镜是对 CSS 的扩展，它可以用很简单的方法对页面中的文字进行特效处理。

- 使用 `filter` 添加一些滤镜、
- 基本语法
	- `fliter:滤镜名(参数1 = 值1; 参数2 = 值2; ...)`

### 光晕

- 滤镜 `glow` 用于设置在对象周围发光的效果。
- 常用参数
	- `color` 设置发光的颜色。
	- `strength` 设置发光的强度。
		- 范围为 **1~255**，默认值为 **5**。

### 模糊

- 滤镜 `blur` 可产生模糊效果。
- 常用参数
	- `add` 布尔值，设置滤镜是否激活。
	- `direction` 设置模糊的参数。
		- 按顺时针的方向以 45 度为单位进行累积。
	- `strength` 设置受影响的宽度。
		- 取值必须为**整数**。
		- 默认值为 **5**。

### 遮罩

- 滤镜 `mask` 用于为对象建立一个覆盖于表面的莫。
- 常用参数
	- `color` 最后遮罩显示的颜色。

### 透明色

- 滤镜 `chroma` 用于将对象中指定的颜色显示为透明。
- 常用参数
	- `color` 要变为透明的颜色。

### 阴影

- 滤镜 `dropShadow` 可以为图像设置阴影效果。
- 常用参数
	- `color` 设置阴影的颜色。
	- `offX` 设置阴影相对图像移动的水平距离。
	- `offY` 设置阴影相对图像移动的垂直距离。
	- `positive` 是否为透明像素生成阴影
		- 0 是
		- 1 否

### 波浪

- 滤镜 `wave` 用于为对象内容建立波浪效果。
- 常用参数
	- `add` 是否要把对象按照波形样式打乱。
		- 默认值为 true。
	- `frep` 设置滤镜建立的波浪数目、
	- `lightstrength` 设置波纹增强光影的效果。
		- 范围 **0~100**。
	- `phase` 设置正弦波开始出的相对偏移。
	- `strength` 设置波浪的振幅大小。

### X 射线

- 滤镜 `xray` 用于加亮对象的轮廓。
- 该滤镜不需要设置参数。
