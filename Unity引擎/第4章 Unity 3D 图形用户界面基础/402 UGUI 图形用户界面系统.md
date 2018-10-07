[toc]

Unity 3D 从 4.6 版本开始新增的图形用户界面系统 UGUI。

## 创建 UGUI 控件

1. 单击 "GameObject &rrar; UI" 就会出现所有的 UGUI 控件。
2. 选中一个想要的控件，单击它就可以完成创建。
3. 创建好一个控件后就会在 Hierarchy 面板中看到结构。
	- 其中，Canvas 是画布。
	- 在该界面中创建的所有控件都会自动变为 Canvas 游戏对象的子对象。
	- 如果场景中没有已经存在的 Canvas，系统就会自动创建一个。
	- 同时创建一个名为 "EventSystem" 的游戏对象，上面挂载了若干事件监听相关的组件可供设置。

## Canvas 画布

### UI 元素的绘制顺序

UI 元素在 Canvas 里的绘制顺序和它们在 Hierarchy 面板中的排序是一致的。
如果两个 UI 元素有重叠部分，那么之后绘制的元素会挡在先绘制的元素上面。

### Render Modes 渲染模式

在 Canvas 中还可以通过设置渲染模式来确定 UI 元素是渲染在 Screen Space 上还是 World Space 上。

在 Unity 3D 中支持的渲染模式有三种：

- Screen Space-Overlay
	- 默认的渲染模式。
	- 在该模式下会将所有的 UI 元素都渲染在场景的最上层。
	- 如果屏幕尺寸或者分辨率发生变化，Canvas 也会自动去和变化后的尺寸相适应。
- Screnn Space-Camera
	- 在该模式下 Canvas 游戏对象放置在一个预先设置好的摄像机的特定距离外，UI 元素通过该摄像机进行渲染。
	- 使用该模式时应该创建一个摄像机并将其指定给 Canvas 组件下的 Render Camera。
	- 改变摄像机位置时，UI 元素的显示效果也会跟着改变。
- World Space
	- 在该模式下，Canvas 类似一个游戏对象，可以手动改变其 RectTransform 组件。
	- 在渲染时，UI 元素会根据它们在 3D 场景中的位置被渲染在其他游戏对象之前或之后，使其成为游戏试图中的一个成分。

### Graphic Raycaster

- 每个 Canvas 都有一个 Graphic Raycaster 组件，用于获取用户选中的 UGUI 控件。
- 多个 Canvas 之间的时间相应顺序由其显示顺序决定。
- 当 Canvas 使用 World Space 或 Camera Space 渲染模式时，Graphic Raycaster 的 "Block" 选项可以用来设置遮挡目标。

## EventSystem

创建一个 UGUI 元素后，Unity 会同时创建一个游戏对象，其名为 "EventSystem"。

- 自带的两个 Input Module 组件。
	- 一个用于响应标准输入。
	- 一个用于响应触摸输入。
- 在各个 Input Module 中封装了对 Input 模块的调用。
	- 根据用户操作触发对应的 Event Trigger。

EventSystem 组件统一管理多个 Input Module 和各种 Raycaster。

- 该组件每帧调用多个 Input Module 处理用户的操作。
- 同时负责调用多个 Raycaster 用于获取用户点击到的 UGUI 控件或 2D、3D 物体。

## RectTransform 组件

UGUI 中每个控件包括 Canvas 都会带一个 RectTransform 组件。

- 该组件继承自 Transform，用于控制 UI 元素的 Transform 信息。
- 当开发人员向一个 Empty Object 添加一个 UI Component 组件时，Transform 组件会自动变为 RectTransform。

|参数名|含义|参数名|含义|
|-|-|-|-|
|PosX、PosY、PosZ|UI 元素的位置|Width、Height|UI 元素的宽度和高度|
|Anchors|相对于父对象的锚点|Pivot|UI 元素的中心|
|Rotation|按轴旋转|Scale|按轴缩放|

单击 RectTransform 组件中左上角的准星图标。

- 可以在弹出的 Anchor Presets 面板中进行快速设置。
- 按住 Shift 键时能同时设置 pivot，此时控件的 position 已经改变。
- 按住 Alt 键能够在设置 anchor 同时设置 position。
- 如果同时按住 Shift 键和 Alt 键，那么就能同时设置 anchor、pivot 和 position。

## Panel 控件

执行 "GameObject &rarr; UI &rarr; Panel" 命令，就会在 Canvas 游戏对象下创建一个 Panel 控件。

该控件是一个覆盖屏幕的平面，一般可以用来显示 UI 界面的背景。

在 Image 控件下，

- Source Image 用于放置需要显示的 Sprite。
- Color 属性可以更改其颜色以及透明度。
- Material 属性中可以添加材质。

> Panel 控件在默认情况下会自动根据屏幕的大小来调整自身的大小。

## Button 控件

执行 "GameObject &rarr; UI &rarr; Button" 命令，就可以创建一个按钮控件。

### 组件介绍

创建出来的 Button 空间包含了一个 Text 子对象（用于控制 Button 上显示的字样）。
每个按钮上都挂载有 Button 组件和 Image 组件。

- Image 组件管理按钮的显示图片。
	- 在 Source Image 中可以放上合适的 Sprite 图片精灵。
	- 通过 Color 和 Material 可以设置图片的颜色和材质。
- Button 组件管理单击按钮后的变化以及监听。
	- Transition 过度选项定义了四种过滤模式：
		- None
		- Color Tint
			- 使用该模式时，可以分别通过 Color 属性对按钮的 4 个状态进行设置。
		- Sprite Swap
			- 使用该模式时，同样有 4 个状态可以设置，可以为每个状态下的按钮设置一个图片 Sprite。
		- Animation
			- 使用动画状态机可以对不同状态下的按钮的位置、大小、旋转、图片等大量参数进行设置。
	- 除了 None 的每个模式中按钮都有 4 种状态：
		- Normal（正常状态）
		- Highlight（突出显示）
		- Pressed（按下状态）
		- Disable（禁用）

|参数名|含义|参数名|含义|
|-|-|-|-|
|Interactable|该按钮是否启用|Navigation|导航，使用键盘方向键切换选中按钮时的切换顺序|
|Transition|按钮状态变化模式|Visualize|可视化，使 Navigation 顺序在 Scene 窗口中可视化|

### 按钮点击监听挂载

通过 Button 组件中的 OnClick() 事件参数添加按钮点击监听。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	public void OnbtlClick(){
		Debug.Log ("This is btl");
	}
}
```

1. 编写好上面的脚本，挂载到 Canvas 游戏对象上。
2. 单击 Button 组件 OnClick() 下方的 "+" 按钮。
3. 将挂载脚本的游戏对象 Canvas 拖到带有 ⊙ 符号的选框上。
4. 展开有 No Function 字样的下拉框，选择 `Test.OnbtlClick` 即可。

在指定监听方法时还可以进行传参。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	public void OnbtlClick(int index){
		Debug.Log ("This is btl" + index);
	}
}
```

在下拉框下方输入参数，即可进行传参。

## Text 控件

主要功能为在对应的区域显示相应的文本。

|参数名|含义|参数名|含义|
|-|-|-|-|
|Text|显示的文本|Font Style|字体样式，包括加粗、斜体|
|Font|需要选用的字体|Font Size|字体大小|
|Line Spacing|行间距|Alignment|对齐方式|
|Rich Text|是否为多格式文本|Color|字体颜色|
|Material|字体材质|Vertical Overflow|竖直逸出方式|
|BestFit|最佳匹配方式|Horizontal Overflow|水平溢出方式|

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;  // 这里需要使用 UnityEngine.UI 命名空间

public class Test : MonoBehaviour {

	public Text tt;

	void Start(){
		tt.color = Color.red;
		tt.text = "this is text";
	}
}
```

1. 编写好脚本，挂载到 Canvas 游戏对象上。
2. 新建 Text 控件上，拖拽到脚本对应的变量上。

## Image 控件

该控件用于显示一个非交互式的图片精灵 "Sprite"。

|参数名|含义|参数名|含义|
|-|-|-|-|
|Source Image|用于显示的图片素材|Color|图片的色调|
|Material|图片的材质|Image Type|图片模式|
|Preserve Aspect|是否保持图片长宽比|&nbsp;|&nbsp:|

> 当开发人员需要使用自己的图片时需要将图片设置为 Sprite 格式，具体步骤为：
在 Inspector 面板中将 Texture Type 选为 "Sprite(2D and UI)"，然后单击 Apply 确定。

## Raw Image 控件

该控件用于显示一个非交互式的图像。
Image 组件只能显示 Sprite，而 Raw Image 控件可以显示任何纹理。

|参数名|含义|参数名|含义|
|-|-|-|-|
|Texture|用于显示的图片纹理|Color|图片的色调|
|Material|使用的材质|UV Rect|图片在控件矩形中显示的偏移和大小|

由于 Raw Image 控件不需要一个精灵纹理 "Sprite"，所以其可以用于显示在游戏中使用 WWW 类从某个 URL 下载的图像或者渲染纹理，也可以使用场景中某个摄像机的渲染图在 UI 界面中显示出该摄像机拍摄到的画面。

## Slider 控件

执行 "GamgeObject &rarr; UI &rarr; Slider" 命令，就可以创建一个 Slider 控件。

Slider 控件的子对象中：

- Background 是滑块主题背景，
- Fill Area 下的子对象 Fill 代表已经被选中的部分，会随着滑块的左右滑动改变其长度。
- Handle 子对象是玩家点击的滑块按钮。

|参数名|含义|参数名|含义|
|-|-|-|-|
|Interactable|是否启用该控件|Transition|过渡模式|
|Navigation|导航，使用键盘方向键切换选中按钮时的切换顺序|Visualize|可视化，使 navigation 顺序在 Scene 窗口中可视化|
|Fill Rect|Fill 子对象的 RectTransform 组件的引用|Handle Rect|Handle 子对象的 RectTransform 组件的引用|
|Direction|滑块的方向，默认是从左到右|Min Value|滑块的最小值|
|Max Value|滑块的最大值|Whole Number|滑块的值是否只能是整数|
|Value|滑块当前的值|&nbsp;|&nbsp;|

为 Slider 控件绑定事件监听方法：

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class Test : MonoBehaviour {

	public Slider sd;

	public void OnsdValueChange(){
		Debug.Log (sd.value);
	}
}
```

1. 编写好脚本，挂载到 Canvas 游戏对象上。
2. 将创建的 Slider 控件拖拽到脚本指定的变量上。
3. 单击 Slider，单击 OnValueChanged（Single）下方的 "+" 按钮添加一个事件监听。
4. 将挂载脚本的游戏对象 Canvas 拖拽到 Runtime 下的 GameObject 选框中。
5. 在右边选择监听方法为 `Test.OnsdValueChange`。

## Scrollbar 控件

执行 "GameObject &rarr; UI &rarr; Scrollbar" 命令就可以创建出一个滚动条控件。

|参数名|含义|参数名|含义|
|-|-|-|-|
|Interactable|是否启用控件|Transition|过渡模式|
|Handle Rect|Handle 子对象的 RectTransform 组件的引用|Direction|Scrollbar 的方向，默认是从左到右|
|Value|Scrollbar 的值|Size|滑块的大小|
|NumberOfSteps|进行分段，滚动条显示分段|&nbsp;|&nbsp;|

## Toggle 控件

执行 "GameObject &rarr; UI &rarr; Toggle" 命令就可以创建一个开关。

Toggle 控件的子对象中包含：

- Background 作为开关的背景。
- Checkmark 用于显示选中后显示的团。
- Label 用来显示开关的信息。

|参数名|含义|参数名|含义|
|-|-|-|-|
|Interactable|是否启用该控件|Transition|过渡模式|
|Navigation|导航，确定控件的顺序|Visualize|使导航顺序在 Scene 窗口中可视化|
|Is On|开关的状态|Toggle Transition|开关的消隐模式（none 和 fade）|
|Graphic|Checkmark 子对象的引用|Group|成组|

如何使用开关的 Group 参数：

1. 在 Hierarchy 窗口中选中 Canvas 游戏对象。
2. 单击鼠标右键选择 "Create Empty" 命令创建一个空对象。
3. 依次创建 3 个 Toggle 控件，将其设置为 GameObject（空对象）的子对象。
4. 将 3 个 Toggle 控件中的 Is On 设置为关闭状态。
5. 选中空对象，执行 "Component &rarr; UI &rarr; Toggle Group" 添加一个 Toggle Group 组件。
6. 将 "Allow Switch Off" 参数（决定是否可以把打开的开关取消选中）取消选中。
7. 依次选中创建的 3 个 Toggle 控件，将其中的 Group 参数选为挂载有 Toggle Group 组件的 GameObject 游戏对象。

## Input Field 控件

Input Field 控件是 UGUI 中的输入框控件。

> 在移动设备上使用时，当用户点击到该控件时，就会弹出用于输入的键盘。

在 Input Field 控件的子对象中：

- Placeholder 是用于显示默认提示信息的文本框。
- Text 则用于显示用户输入的文本。

|参数名|含义|参数名|含义|
|-|-|-|-|
|Interactable|是否启用控件|Transition|过渡模式|
|Navigation|导航|Text Component|用于用户输入的文本框的引用|
|Text|用户输入的文本框中的内容|Character Limit|可以输入到输入框中最大文字数|
|Content Type|指定输入框的类型|Standard|可以输入任何类型的字符|
|Autocorrected|自动校正未知字符，显示更合适的替代字符|Integer Number|只能输入整数|
|Decimal Number|只能输入带有一个小数点的小数|Alphanumeric|只能输入字母和数字|
|Name|自动大写首字母|Email Address|允许输入 Email 地址格式的字串|
|Password|用\*号自动隐藏用户输入的内容，可以输入符号|Pin|用\*号自动隐藏用户输入的内容，只能输入数字|
|Custom|允许自定输入类型|Line Type|换行方式，包括单行显示、自动换行、自定义换行|
|Placeholder|提示文本框的引用|Caret Blink Rate|光标的闪烁速度|
|Selection Color|选中输入框中文本时选中框的颜色|Hide Mobile Input|在移动设备上输入时是否隐藏|

Input Field 控件可以发出两个事件：OnValueChange 和 EndEdit，分别是当值发生改变时发出和结束编辑时发出。

## UGUI 布局管理的使用及相关组件介绍

Unity 自带的布局模式有：

- Horizontal Layout Group 水平布局
- Vertical Layout Group 垂直布局
- Grid Layout Group 网格布局

创建 5 个 Image 控件，并放在一个空对象 "UIMain" 下称为其子对象。

### Horizontal Layout Group 水平布局

选中 "UIMain" 空对象，执行 "Component &rarr; Layout &rarr; Horizontal Layout Group" 命令。

|参数名|含义|参数名|含义|
|-|-|-|-|
|Padding|布局的边缘填充（即偏移）|Spacing|布局内的元素间距|
|Child Alignment|对齐方式|Child Force Expand|自适应宽和高|

### Horizontal Layout Group 水平布局

选中 "UIMain" 空对象，执行 "Component &rarr; Layout &rarr; Vertical Layout Group" 命令。

|参数名|含义|参数名|含义|
|-|-|-|-|
|Padding|布局的边缘填充（即偏移）|Spacing|布局内的元素间距|
|Child Alignment|对齐方式|Child Force Expand|自适应宽和高|

### Grid Layout Group 网格布局

### Horizontal Layout Group 水平布局

选中 "UIMain" 空对象，执行 "Component &rarr; Layout &rarr; Grid Layout Group" 命令。

|参数名|含义|参数名|含义|
|-|-|-|-|
|Padding|布局的边缘填充（即偏移）|CellSize|内部元素的大小|
|Spacing|布局内的元素间距|Start Corner|第一个元素的位置|
|Start Axis|元素的主轴线|Horizontal|在填满一行后启用一个新行|
|Vertical|在填满一列后启用一个新列|Child Alignment|对齐方式|
|Constraint|指定网格布局的行货列|&nbsp;|&nbsp;|

> 在游戏运行时，将新实例化的 UI 控件或者游戏对象设置为挂载有 Layout Group 组件的游戏对象的子对象，Layout Group 组件便会对其进行自动布局排列。

## UGUI 中不规则形状的按钮的碰撞检测

UGUI 中自带的按钮是标准的矩形，虽然可以由玩家任意换图，但是其碰撞检测区域始终是阻型的。

1. 创建 Button 控件，将 Text 子对象删除。
2. 选中 Button 控件，执行 "Component &rarr; Physics2D &rarr; Polygon Collider 2D" 命令。
3. 单击 Polygon Collider 2D 组件中的 Edit Collider 按钮，在 Scene 界面中将想要的碰撞检测区域勾选出来。
4. 重写 Image 类，需要引用 `UnityEngine.UI`，并继承 `Image` 类。
5. 将 Button 控件上的 Image 组件移除，将脚本拖拽到 Button 控件上形成组件以代替。
6. 重新为该组件指定好纹理图。
7. 为 Button 控件挂载点击事件监听。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class Test : Image {

	PolygonCollider2D collider;

	void Awake(){
		collider = GetComponent<PolygonCollider2D> ();
	}

	public override bool IsRaycastLocationValid(Vector2 screenPoint, Camera eventCamera){
		// 判断是否在圈出的多边形区域内
		bool inside = collider.OverlapPoint (screenPoint);
		// 返回是否在多边形内
		return inside;
	}
}
```

## Scroll View 的制作

所谓 Scroll View 就是滚动视窗。

1. 在 Hierarchy 面板中单击鼠标右键，执行 "UI &rarr; Panel" 命令创建一个 Panel 控件。
2. 命名为 "ScrollView"，更改其锚点值为 "middle/center" 并调整大小。
3. 选中 "ScrollView" 游戏对象，在 Hierarchy 面板中单击鼠标右键，执行 "Create Empty" 命令创建一个空对象，并将其命名为 "Grid"，设置其大小。
4. 选中该空对象，创建多个 Image 组件，并设置为 "Grid" 的子对象。
5. 为游戏对象 "Grid" 添加 Grid Layout Group 组件吗，调整 "Grid" 的高度。
6. 为 "ScrollView" 添加 "Mask" 组件，将超出范围的 Image 遮住。
7. 选中 "ScrollView" 游戏对象，添加 "Scroll Rect" 组件，并将游戏对象 "Grid" 拖到 "Scroll Rect" 组件中的 "Content" 选框中。
8. 为了直观，在右边创建一个 Scrollbar 控件，将其选择为垂直拖动模式。
9. 将 "ScrollView" 游戏对象上的 "Scroll Rect" 组件中的 "Vertical Scrollbar" 选为上面创建的 "Scrollbar"。
10. 为 Image 组件赋予贴图。
