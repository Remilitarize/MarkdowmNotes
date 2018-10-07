[toc]

## 网页中常见的图像格式

### GIF 格式

- Graphic Interchange Format 的缩写，即**图片交换格式**。
- 最多可使用 **256** 种颜色。
- 最适合**显示色调不连续**或**具有大面积单一颜色**的图像。
- 特点
	- 可制作动态图像。
	- 可以以渐显的方式在网页中呈现。
		- 渐显：当图像尚未下载完成时，浏览器会先以马赛克的形式将图像慢慢显示。

### JPEG 格式

- Joint Photographic Experts Group 的缩写，是一种**图片压缩格式**。
- 用于**摄影**或**连续色调**图像的高级格式。
- 包含**数百万种**颜色。
- 特点
	- 压缩十分紧凑。
	- 专门用于不含大色块的图像。
	- 有一定的**失真度**。
	- **不支持透明图和动态图**。

### PNG 格式

- Portable Network Graphics 的缩写，是一种**非破坏性的网页图像文件格式**。
- 将图像文件以**最小**的方式压缩却不造成图像失真。
- 具备 GIF 图像格式的大部分优点，还支持 **48-bits** 的色彩。

## 插入图像并设置图像属性

- 使用 `<img></img>` 标记将图像插入到网页中。
- 必要属性
	- `src`：图像的 URL 地址。
	- `alt`：**鼠标放在图像上**或**图像无法显示时**提示的文字。
		- 最多可以包含 **1024** 个字符的字符串。
		- 不允许有任何样式标签。
- 可选属性
	- `width`：设置图像的宽度
	- `height`：设置图像的高度
	- `ismap`：当用户点击图像时，将点击的坐标返回给服务器
	- `usemap`：设置图像热区链接
- 不推荐使用的属性
	- `border`：添加一个边框并设置边框宽度
	- `vspace`：设置垂直间距
	- `hspace`：设置水平间距
	- `align`：对齐方式
		- top：顶部对齐
		- bottom：底部对齐
		- middle：中间对齐
		- left：左侧对齐
		- right：右侧对齐

## 添加多媒体文件

- 使用 `<embed></embed>` 将多媒体文件嵌入到网页中。
- 允许嵌入的格式有 midi / wav / aiff / au 等。
- 必要属性
	- `src`：多媒体文件的 URL 地址
- 可选属性
	- `width`：宽度
	- `height`：高度
	- `autostart`：是否自动播放
	- `loop`：是否循环播放

> embed 标记在 HTML 4 中无效。

## 添加背景音乐

- 使用 `<bgsound></bgsound>` 标记嵌入声音文件。
- 必要属性
	- `src`：声音文件的 URL 地址
- 可选属性
	- `loop`：设置循环播放次数

> 需要显示播放界面的音乐情使用 `<embed></embed>` 标记。
> `<bgsound></bgsound>` 仅适用于 IE。

## 补：audio 标记

参考资料：[W3School Audio 标记](http://www.w3school.com.cn/tags/tag_audio.asp)

- 基本语法
	- `<audio src = "音频的 URL 地址"> 不能正常播放时显示该文字 </audio>`
- 可选属性
	- `autoplay = "autoplay"`：是否自动播放
	- `controls = "controls"`：是否显示控件
	- `loop = "loop"`：是否循环播放

> audio 标记在 HTML 4 中无效。
> IE 8 以下的版本不支持 audio 标记。
