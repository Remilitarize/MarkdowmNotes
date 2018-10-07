[toc]

## Unity 集成开发环境的整体布局

进入 Unity 集成开发环境，可以看到整体布局为

- *标题栏*
- *菜单栏*
- *工具栏（位于菜单栏下的一排按钮）*
- *Scene 窗口（场景设计面板）*
- *Game 窗口（游戏预览面板）*
- *Hierarchy 窗口（游戏组成对象列表）*
- *Projects 窗口（项目资源列表）*
- *Inspector 窗口（属性查看器）*
- *提示栏*
- *Console 窗口（控制台）*

开发人员可以根据自己的爱好和实际需求来创建自己的布局。

1. 在每个面板或者窗口的标签处按住鼠标左键，把面板或者窗口拖到适当的位置后松开鼠标左键。
2. 布局完成后可以执行 "Window" &rarr; "Layouts" &rarr; "Save Layout" 命令保存自己的布局。
3. 可以执行 "Window" &rarr; "Layouts" 命令找到曾经保存的布局。

### 菜单栏

- File（文件）菜单：打开和保存场景、项目，以及创建游戏。
- Edit（编辑）菜单：普通的赋值和粘贴功能，以及选择与其相应的设置。
- Assets（资源）菜单：与资源创建、导入、导出及同步相关的所有功能。
- GameObject（游戏对象）菜单：创建、显示游戏对象，以及为其创建父子关系。
- Component（组件）菜单：为游戏对象创建新的组件或属性。
- Window（窗口）菜单：显示特定视图。
- Help（帮助）菜单：包含到手册、社区论坛及激活许可证的链接。

### 工具栏

- Transform（变换）工具：在场景设计面板中用来控制和操控对象。
	- 按照从左到右的次序，分别是 *Hand（移动）工具、Translate（平移）工具、Rotate（旋转）和 Scale（缩放）工具*。
	- 第五个常用于 Unity 2D。
- Transform Gizmo（变换 Gizmo）切换：改变场景设计面板中 Translate 工具的工作方式。
- Play（播放）控件：用来在编辑器内开始或暂停游戏的测试。
- Layers（分层）下拉列表：控制任何给定时刻在场景设计面板中显示哪些特定的对象。
- Layout（布局）下拉列表：改变窗口和视图的布局，并且可以保存所创建的任意自定义布局。

### 场景设计面板

#### 摄像机导航

- Tumble（旋转，*Alt + 鼠标左键*）：摄像机会以任意轴为中心进行旋转。
- Track（移动，*Alt + 鼠标中键*）：在场景中把摄像机向左、向右、向上和向下移动。
- Zoom（缩放，*Alt + 鼠标右键或鼠标滚轮*）：在场景中缩小或放大摄像机视角。
- Flythrough（穿越）模式（*鼠标右键 + WASD 键*）：摄像机会进入 "第一人称" 模式，使得开发人员可以在场景中迅速地移动和缩放。
- Center（居中，*选择游戏对象并按 F 键*）：摄像机会放大并把选中的对象居中显示在视野中。

在场景设计面板还包含一个名为 "Persp" 的特殊工具。

- 单击 Persp 上的每个箭头都会改变观察场景的角度。
- 单击中间的立方体，可以把场景设计面板恢复到默认的透视视图。

> 可以执行 "Edit" &rarr; "Preference" &rarr; "Colors" 命令更改箭头的颜色。

#### 高级视图操作

场景设计面板的控制栏可以改变摄像机查看场景的方式。

- 第一个下拉列表（绘制模式）可以控制在游戏场景中如何绘制对象。
	- 默认值为 Shaded（带有材质的）。
	- 单击菜单吧绘制模式修改为 Wireframe（线框）会显示对象的物理网格，而不带有任何贴图。
	- Shaded Wireframe（带有材质的线框）会把对象的贴图和它们的线框叠加在一起显示
	- Miscellaneous（杂项）下拉列表对开发者游戏场景中的对象进行微调。
	- Global Illumination（全局光照模式设置）下拉列表可以对全局光照模式进行设置。
- Scene Lighting（场景光照）按钮可以在场景设计面板中是使用默认的内置光照还是使用开发人员自己实现的光照之间来回切换。
	- 如果开发人员没有在场景中放入任何光源，使用内置光照设置可以由系统为场景自动添加一个光照。
- Scene Overlay（场景叠加）可以对摄像机显示的场景进行更新，使得场景的显示方式就像在游戏中一样——网格隐藏，其他的效果进行渲染。

#### 操作对象

除了把摄像机视角四处移动之外，还需要在场景中重新定位和移动对象，这些操作称为 **对象变换**。

对象变换方式有以下两种方式：

- 在 Inspector 中为这些变换输入新的值。
- 通过变换工具手动地移动和操作这些对象。

Transform 工具的使用：

首先单击某个游戏对象，

- 按下 **Q 键** 来激活移动工具。
- 按下 **W 键** 来激活平移工具。
	- 拖动箭头即可在箭头所指的方向上平移。
	- 拖动坐标中心的正方形可在其所在平面没进行平移。
- 按下 **E 键** 来激活旋转工具。
	- 拖动即可以进行任意角度的旋转。
- 按下 **R 键** 来激活缩放工具。
	- 拖动某个方块可以进行在某个方向上的缩放。

### 游戏预览面板

在该面板中可以随时进行测试或试玩游戏。

- 单击播放控件中第一个按钮，编辑器会激活游戏预览面板。
- 中间的按钮为暂停按钮，用于暂停游戏。
- 最后一个按钮是单帧播放按钮，按下时游戏会暂停，以后每按一次游戏就会运行一帧，可以进行调试。

在游戏预览面板上方同样具有控制栏。

- Aspect 下拉列表可以实时该笔那游戏预览面板的显示比例。
	-	Free Aspect 选项允许游戏预览面板填满当前游戏中所有可用的空间。
- 单击 Maximize on Play 按钮，可以使游戏运行时把游戏预览面板扩大到编辑器视图的整个区域。
- 单击 Gizmos（工具）按钮，可以切换游戏中绘制的渲染的所有工具。
- 单击 Stats 按钮可以显示 Statistics 页面，用于显示游戏绘制的数据。
	- FPS：每一秒游戏渲染的帧数。
	- Batches：最初单独描绘调用被添加到批处理的数量。
		- 批处理是引擎试图结合多个物体渲染进行一次描绘调用，以降低 CPU 开销。
		- 为了确保良好的批处理，应当尽可能多地在不同物体之间共享材质。
	- Tris：绘制三角形的数目。
		- 在游戏开发中应尽量减少三角形的数量。
	- Screen：屏幕的分辨率，和连同其抗锯齿级别和内存的使用量。
	- Visible Skinned Meshes：渲染蒙皮网络的数量。
	- Animations：正在播放动画的数量。

### 游戏组成对象列表

游戏组成对象列表列出了游戏场景中所有的游戏对象。
一个资源的每个实例都会独立地列出来，使得良好的命名规范变得尤为重要。
命名的规范也就是达到见名知意的目的。

> 在游戏组成对象列表中选择一个对象并按 Delete 键（或是单击鼠标右键并选择 "Delete"），可以从游戏的当前场景中删除这个对象。

游戏组成对象列表中可以为对象建立父子关系。
为对象建立父子关系，基本上就是将一组相似的对象收集到一起并进行分组，使它们位于一个单一的对象（**父对象**）之下。
在该父对象下的所有其他对象，都称为 **子对象**。
当对父对象进行移动或是操作时，也会依次对其下的所有子对象 **进行同样的操作**。

### 项目资源列表

项目资源列表中列出了项目中的所有文件，包括脚本、贴图、模型、场景等文件。
这些文件都组织到一个 *Assets（资源）文件夹* 中。

> 在 Unity 编辑器外部移动资源文件时要注意，移动操作可能会破坏原有的调用。

可以在项目资源列表中直接打开文件并进行编辑。
正常保存这个文件，Unity 编辑器就会自动地把这个文件更新到项目中。

在搜索栏中输入文件名的任何部分即可在项目各个层次的子目录中进行查找。

### 属性查看器

属相查看器显示了游戏中每个游戏对象所包含的所有组件的详细属性。
在后面会对不同种类的属性进行详细的介绍。

### 状态栏与控制台

状态栏总是出现在编辑器的底部。
可以通过菜单执行 "Window" &rarr; "Console" 命令或按快捷键 Ctrl + Shift + C 打开控制台，也可以单击状态栏来打开控制台。

当按下 "播放" 按钮开始测试项目或是导出运行项目时，在状态栏和控制台都会显示出相关的提示信息，也可以在脚本中让项目向控制台和状态栏输出一些信息帮助调试和修复错误。

### 动画视图

动画视图使开发人员可以在这里查看或是调整动画曲线。
可以通过执行 "Window" &rarr; "Animation" 命令或按快捷键 Ctrl + 6 来查看。

### 动画控制器编辑视图

动画控制器编辑试图用于编辑动画控制器。
可以通过执行 "Window" &rarr; "Animator" 命令或在项目资源列表中双击一个动画控制器文件来打开它。

## 菜单栏

### 文件（File）

New Scene

- 该命令功能为新建场景，即新建一个游戏场景。
- 每一个新创建的游戏场景包含了一个 Main Camera（主摄像机）和一个 Directional Light（平行光光源）。

Open Scene

- 该命令功能为打开场景，即打开以前所保存的场景。
- 单击后会弹出一个 "Load Scene" 对话框，选择所要打开的场景文件（后缀名为 **".unity"** 的文件），单击 "打开" 按钮即可打开场景文件。

Save Scene

- 该命令功能为保存场景，即保存当前所搭建的场景。
- 如果是第一次保存当前场景，单击后会弹出一个 "Save Scene" 对话框，输入名称，单击 "保存" 按钮，就会生成一个场景文件。
- 如果之前保存过该场景，单击后会将之前保存的场景文件覆盖，不会弹出 "Save Scene" 对话框。

Save Scene as ...

- 该命令功能为场景另存为...，即把当前场景另存为一个新的场景文件。
- 单击后会弹出一个 "Save Scene" 对话框。

New Project...

- 该命令功能为新建项目工程，即创建一个新的项目工程。
- 单击后会弹出一个 "New Project" 对话框。
	- 在 Project name 处输入项目名称。
	- 在 Location 处选择合适的路径。
	- 在 Asset packages... 处选择所需要导入的资源包。
	- 新建项目默认 3D 项目（如果需要创建 2D 项目，则需要选中 "2D" 字样的选项）。
	- 最后单击 "Create project" 按钮，就会自动创建一个项目并打开 Unity 开发环境。

Open Project...

- 该命令功能为打开项目工程，即打开以前所创建的项目。
- 单击后会弹出一个 "Recent projects" 对话框，以前创建的项目都会显示在列表中。
- 如果没有想要的项目，则需要单击 "Open other..." 按钮。

Save Project

- 该命令功能为保存项目工程。

Build Settings...

- 该命令功能为发布设置，即在发布游戏前对一些准备工作的设置。
- 单击后会弹出 "Build Setting" 对话框。
	- 在 Platform 下选择该项目发布后所要运行的平台。
	- 单击 Player Setting... 按钮，在 Inspector 视图中针对要发布的平台做相应的参数设置。
	- 完成设置后，单击 "Build" 按钮，为生成的安装文件添加文件名，然后单击保存按钮，开始生成文件。

Build&Run

- 该命令功能为发布并运行，即在编译完游戏后，直接将游戏发布到目标平台上。

Build in Cloud...

- 该命令功能为云版本发布，即在云端搭建的调制环境中测试程序。

Exit

- 该命令功能为退出，即退出 Unity 程序。

> 在 Unity Cloud Build 中，开发者可以拥有一个横跨所有平台的编译、测试环境。

### 编辑（Edit）

Undo

- 该命令功能为撤销，即取消当前的操作。
- 快捷键为 "Ctrl + Z"。

Redo

- 该命令功能为 Undo 的反向操作，即重新做一遍当前的操作。
- 快捷键为 "Ctrl + Y"。

Cut

- 该命令功能为剪切。
- 快捷键为 "Ctrl + X"。

Copy

- 该命令功能为复制。
- 快捷键为 "Ctrl + C"。

Paste

- 该命令功能为粘贴。
- 快捷键为 "Ctrl + V"。

Duplicate

- 该命令功能为复制并粘贴。
- 快捷键为 "Ctrl + D"。

Delete

- 该命令功能为删除。
- 快捷键为 "Shift + Del"。

Frame Selected

- 该命令功能为居中并最大化显示当前选中的物体。
- 快捷键为 "F"。

Lock View to Selected

- 该命令功能为居中并最大化显示层级试图中选中的物体。
- 效果与 Frame Selected 相同。

Find

- 该命令功能为查找，即查找场景中的对象。
- 快捷键为 "Ctrl + F"。

Select All

- 该命令功能为选择全部。
- 快捷键为 "Ctrl + A"。

Preferences...

- 该命令功能为偏好设置，即对 Unity 集成开发环境的相应参数进行设置。
- 单击后会弹出一个 "Unity Preference" 对话框。

Prefereces... 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|General|综合设置|Keys|键值|
|External Tools|外部工具|GI Cache|实时光照缓存|
|Colors|颜色|Cache Server|缓存服务器|

General 选项下属子项及其具体含义

|子项|含义|
|-|-|
|Auto Refresh|自动更新|
|Compress Assets on Import|导入时压缩资源|
|Show Asset Store search hits|显示资源商店中资源的数量|
|Editor Skin|界面|
|Load Previous Project on Startup|启动时加载以前的项目|
|Disable Editor Analytics(Pro Only)|自动将分析报告发送给 Unity（专业版专有）|
|Verify Saving Assets|退出时验证所要保存的资源|
|Enable Alpha Numeric Sorting|允许 Hierarchy 窗口中的对象按字母排序|

External Tools 选项下属子项及其具体含义

|子项|含义|子项|含义|
|-|-|-|-|
|External Script Editor|外部脚本编辑器|External Script Editor Args|外部脚本编辑器参数|
|Editor Attaching|编辑器附加操作|Image Application|打开图像文件的工具|
|Revision Control Diff/Merge|文件比较/合并工具|Android SDK Location|安卓 SDK 路径|

- 单击 Colors（颜色）选项，进行对窗口、工具的背景颜色、显示颜色进行设置。
- 单击 Keys（键值）选项，进行对 Unity 集成开发环境中需要改变的键值进行设置。

GI Cache 选项下属子项及其具体含义

|子项|含义|子项|含义|
|-|-|-|-|
|Maximum Cache Size(Gb)|最大缓存设置|Custom Cache Location|是否自定义缓存位置|
|Cache compression|缓存压缩|Clean Cache|清除缓存|
|Cache Size|当前缓存大小|Cache Location|当前缓存位置|

- 单击 Cache Server（缓存服务器）选项，进行对缓存服务器的设置。
- 当启动缓存服务器，即勾选 Use Cache Server 的复选框，就需要在 IP Address（IP 地址）栏中填入正确的 IP 地址，否则不要使用。

Modules...

- 该命令功能为模块管理。
- 展示了针对各个平台的回访引擎，以及拓展的性能优化工具。

Play

- 该命令功能为播放/运行，即播放当前场景动画。
- 快捷键为 "Ctrl + P"。

Pause

- 该命令功能为暂停/中断，即暂停当前场景动画。
- 快捷键为 "Ctrl + Shift + P"。

Step

- 该命令功能为单帧，即播放当前动画的下一帧。
- 快捷键为 "Ctrl + Alt + P"。

Selection

- 该命令功能为选择，即选择所要载入/存储的游戏对象的编号。
- 选择命令中的加载选项即可载入以前所保存的游戏对象。
- 选择命令中的存储选项即可保存当前场景设计面板中所选中的游戏对象，并赋予相应的编号。

Project Settings

- 该命令功能为工程设置，即对工程进行相应的设置。

Project Settings 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Input|输入|Physics2D|2D 物理属性|
|Tags&Layers|标签和层|Quality|质量|
|Audio|音频|Graphics|图形|
|Time|时间|Network|网络|
|Player|播放|Editor|编辑|
|Physics|物理属性|Script Execution Order|脚本执行顺序|

Network Emulation

- 该命令功能为网络模拟，即选择适当的网络传输方式。

Graphics Emulation

- 该命令功能为图形模拟，即选择所需要的着色器模型。

Snap Settings...

- 该命令功能为对齐设置，即适当的对齐方式。

### 资源（Assets）

Create

- 该命令功能为创建 Unity 内置的资源，其选项为 Unity 内置的各个资源。
- Folder：创建一个项目文件夹。
- C# Script：创建一个 C# 脚本。
- Javascript：创建一个 Javascript 脚本。
- Shader：创建一个着色器脚本。
- Compute Shader：创建一个计算着色器脚本。
- Prefab：创建一个预制件。
- Audio Mixer：创建一个音频混合器。
- Animator Override Controller：创建一个动画重写控制器。
- Avatar Mask：创建一个身体遮罩资源。
- Material：创建一个材质资源。
- Lens Flare：创建一个光晕资源。
- Render Texture：创建一个渲染纹理资源。
- Lightmap Parameters：创建一个光照贴图参数资源。
- Animator Controller：创建一个动画控制器。
- Animation：创建一个动画片段资源。
- Physic Material：创建一个物理材质。
- Physics2D Meterial：创建一个 2D 物理材质。
- GUI Skin：创建一个绘制样式资源。
- Custom Font：创建一个文本样式资源。
- Shader Variant Collection：创建一个着色器列表资源。
- Legacy &rarr; Cubemap：创建一个立方体纹理映射资源。

Show in Explorer

- 该命令功能在资源管理器中显示资源文件。

Open

- 该命令功能为打开项目资源列表中的资源文件。

Delete

- 该命令功能为删除项目资源列表中的资源文件。

Import New Asset...

- 该命令功能为导入工程所需要的资源。
- 单击后就会弹出 "Import New Asset" 对话框，选中后单击 Import 即可导入。

Import Package

- 该命令功能为导入工程所需要的 Unity 资源包。
- 单击下属的 "Custom Package..." 选项就会弹出 "Import Package" 对话框。

Export Package...

- 该命令功能为将所需要的资源导出资源包。
- 选中需要导出的资源文件后单击，就会弹出一个 "Export Package" 对话框，单击 "Export..." 按钮即可导出资源包。

Find References In Scene

- 该命令功能为在场景中找出使用选中的资源的游戏对象。
- 在项目资源列表中选中一个资源，单击该命令，就会在游戏组成对象列表中显示使用该资源的游戏对象。

Select Dependencies

- 该命令功能为选择游戏对象的依赖资源。
- 在游戏组成对象列表中选中需要找出依赖资源的游戏对象，单击该命令，就会在项目资源列表中显示出游戏对象的依赖资源。

Refresh

- 该命令功能为刷新项目资源列表。
- 在 Unity 编辑器外部改动项目资源后，需要单击该命令来刷新项目资源列表。

Reimport

- 该命令功能为重新导入项目资源。

Reimport All

- 该命令功能为重新导入项目的所有资源。

Run API Updater...

- 该命令功能为将脚本中已经过时的 API 自动更新为最新的 API。

Sync MonoDevelop Project

- 该命令功能为将 Unity 项目脚本同步到 MonoDeveloper 项目中。

### 游戏对象（GameObject）

Create Empty

- 该命令为创建空游戏对象。
- 空游戏对象就是不带有任何组件的游戏对象。
- 快捷键为 "Control + Shift + N"。

Create Empty Child

- 该命令为创建子游戏对象。
- 快捷键为 "Alt + Shift + N"。
- 选中一个游戏对象，单击该命令或按下快捷键就会为选中的游戏对象创建一个子游戏对象。

3D Object 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Cube|立方体|Sphere|球体|
|Capsule|胶囊|Cylinder|圆柱体|
|Plane|平面|Quad|四边形|
|Pagdoll...|布偶系统|Terrain|地形|
|Tree|树|Wind Zone|风区|
|3DText|3D 文本|&nbsp;|&nbsp;|

2D Object

- 其下属的选项只有一个游戏对象，为开发 2D 游戏必须使用的 Sprite 对象。

Light 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Directional Light|平行光|Point Light|点光源|
|Spotlight|聚光灯|Area Light|区域光|
|Reflection Probe|反射探头|Light Probe Group|灯光探测器组|

Audio

- "Audio Source" 选项的功能为创建声音源。
- "Audio Reverb Zone" 选线的功能为创建音频混响区对象。

UI 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Panel|面板|Button|按钮控件|
|Text|文本控件|Image|图片控件|
|Raw Image|原始图片控件|Slider|拖动条控件|
|Scrollbar|拖动块控件|Toggle|选项控件|
|Input Field|输入框控件|Canvas|画布|
|Event System|事件监听系统|…&nbsp;|&nbsp;|

Particle System

- 该命令功能为创建粒子系统对象。

Camera

- 该命令功能为创建摄像机对象。

Center On Children

- 该命令功能为将父对象的位置设置到子对象的中心点上。
- 在游戏组成对象列表中选中一个父对象，单击该命令，就会将该父对象的位置移动到所有子对象的平均中心点上。

Make Parent

- 该命令功能为将多个游戏对象创建父子关系。
- 在游戏组成对象列表中选中多个游戏对象，单击该命令，就会将除选中的最上面的对象外的其他所有游戏对象设置为最上面的对象的子对象。

Clear Parent

- 该命令功能为解除子对象与父对象的父子关系。

Apply Changes To Prefab

- 该命令功能为将使用预制件实例化的游戏对象的改变应用到预制件上。

Set as first sibling

- 该命令功能为在游戏组成列表中奖子对象移动到其父对象下属的所有子对象的最上面。
- 快捷键为 "Ctrl + -"。

Move To View

- 该命令功能为移动游戏对象与视窗的中心位置。

Align With View

- 该命令功能为移动游戏对象与视窗对齐。

Align View to Selected

- 该命令功能为移动视窗与游戏对象。
- 该命令不会使游戏对象的位置改变。

Toggle Active State

- 该命令功能为控制游戏对象的激活状态。
- 快捷键为 "Alt + Shift + A"。
- 选中游戏对象，如果游戏对象处于激活状态，单击该命令或按下快捷键，该游戏对象就会变为未激活状态，反之亦然。

### 组件（Component）

Add...

- 该命令功能是为场景中的游戏对象添加组件。
- 快捷键为 "Ctrl + Shift + A"。

Mesh 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Mesh Filter|网格过滤器|Text Mesh|文本网格|
|Mesh Renderer|网格渲染器|Skinned Mesh Renderer|带骨骼动画的网格渲染器|

Effects 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Particle System|粒子系统|Trail Renderer|拖尾渲染器|
|Line Renderer|线性渲染器|Lens Flare|镜头光晕|
|Halo|光晕|Projector|投影器|

Legacy Particles 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Ellipsoid Particle Emitter|椭球粒子发射器|Mesh Particle Emitter|网格粒子发射器|
|Particle Animator|粒子动画|World Particle Collider|世界粒子碰撞器|
|Particle Renderer|粒子渲染器|&nbsp;|&nbsp;|

Physics 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Rigidbody|刚体|Character Controller|角色控制器|
|Box Collider|盒子碰撞器|Sphere Collider|球星碰撞器|
|Capsule Collider|胶囊碰撞器|Mesh Collider|网格碰撞器|
|Wheel Collider|轮体碰撞器|Terrain Collider|地形碰撞器|
|Cloth|布料|Hinge Joint|铰链关节|
|Fixed Joint|固定关节|Spring Joint|弹性关节|
|Character Joint|角色关节|Configurable Joint|可配置关节|
|Constant Force|恒力|&nbsp;|&nbsp;|

Physics 2D 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Rigidbody 2D|2D 刚体|Circle Collider 2D|圆圈碰撞器|
|Box Collider 2D|盒子碰撞器|Edge Collider 2D|边缘碰撞器|
|Polygon Collider 2D|多边形碰撞器|Spring Joint 2D|弹性关节|
|Distance Joint 2D|距离关节|Hinge Joint 2D|铰链关节|
|Slider Joint 2D|滑动关节|Wheel Joint 2D|滚轮关节|
|Constant Force 2D|恒力|Area Effector 2D|区域效应器|
|Point Effector 2D|点效应器|Platform Effector 2D|平台效应器|
|Surface Effector 2D|表面效应器|&nbsp;|&nbsp;|

Navigation

- 该下属选项的功能是为游戏对象添加导航组件。

Audio 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Audio Listener|声音监听器|Audio Source|声音源|
|Audio Reverb Zone|音频混响区|Audio Low Pass Filter|音频低通滤波器|
|Audio High Pass Filter|音频高通滤波器|Audio Echo Filter|音频回音滤波器|
|Audio Distortion Filter|音频失真滤波器|Auido Reverb Filter|音频混响滤波器|
|Audio Chorus Filter|音频合唱滤波器|&nbsp;|&nbsp;|

Rendering 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Camera|摄像机|Occlusion Area|闭塞区域|
|Skybox|天空盒|Occlusion Portal|闭塞入口|
|Flare Layer|光晕层|LOD Group|层次级别分组|
|GUI Layer|UI 层|Sprite Renderer|精灵渲染器|
|Light|光照|Canvas Renderer|标签渲染器|
|Light Probe Group|光探针组|GUI Texture|UI 图片|
|Reflection Probe|反射探头|GUI Text|UI 文本|

Layout 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Rect Transform|矩阵变换|Canvas|标签|
|Canvas Group|标签组|Canvas Scaler|UI 屏幕自适应|
|Layout Element|布局元素|Content Size Fitter|内容大小适配器|
|Aspect Ratio Fitter|屏幕长宽比适配器|Horizontal Layout Group|水平布局|
|Vertical Layout Group|垂直布局|Grid Layout Group|网格布局|

Miscellaneous 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Animator|动画控制器|Animation|动画播放器|
|Netword View|网格视图|Wind Zone|风区|
|Terrain|地形|Billboard Renderer|标志板渲染器|

Event

- 该下属选项的功能是添加与事件监听相关的组件。

UI 命令下属选项及其具体含义

|选项|含义|选项|含义|
|-|-|-|-|
|Effects|特效组件|Image|图片组件|
|Text|文本组件|Raw Image|原始图片组件|
|Mask|遮挡组件|Button|按钮组件|
|Input Field|输入框组件|Scrollbar|滑动块组件|
|Scroll Rect|滚动条组件|Silder|滑动条组件|
|Toggle|选项组件|Toggle Group|选项组组件|
|Selectable|可选择组件|&nbsp;|&nbsp;|

### 窗口（Window）

Next Window

- 该命令功能为将当前的视图转换到下一个窗口。

Previous Window

- 该命令功能为将当前的视图转换到上一个窗口。

Layouts

- 该命令功能为设置整个 Unity 集成开发环境的整体布局。

Scene

- 该命令功能为打开场景设计面板。
- 快捷键为 "Ctrl + 1"。

Game

- 该命令功能为打开游戏预览面板。
- 快捷键为 "Ctrl + 2"。

Inspector

- 该命令功能为打开属性查看器。
- 快捷键为 "Ctrl + 3"。

Hierarchy

- 该命令功能为打开游戏组成对象窗口。
- 快捷键为 "Ctrl + 4"。

Project

- 该命令功能为打开项目资源列表。
- 快捷键为 "Ctrl + 5"。

Animation

- 该命令功能为打开动画设计面板。
- 快捷键为 "Ctrl + 6"。

Profiler

- 该命令功能为对 Unity 集成开发环境中各个功能选项的使用情况及其 CPU 的利用率进行检查。
- 快捷键为 "Ctrl + 7"。

Audio Mixer

- 该命令功能为打开音频混合器编辑界面。
- 快捷键为 "Ctrl + 8"。

Asset Store

- 该命令功能为打开资源商店。
- 快捷键为 "Ctrl + 9"。

Version Control

- 该命令功能为版本控制。
- 单击后会弹出版本控制面板，单击 Setting 按钮，Inspector 视窗中就会显示版本控制的模式。

Animator Parameter

- 该命令功能为打开动画控制器参数设置面板。

Animator

- 该命令功能为打开动画控制编辑器。

Sprite Packer

- 该命令功能为打开精灵打包器面板。

Lighting

- 该命令功能为打开光照设置买你把你。

Occlusion Culling

- 该命令功能为打开遮挡剔除面板。

Frame Debugger

- 该命令功能为打开帧调试器面板。

Navigation

- 该命令功能为打开导航网格设置面板。

Console

- 该命令功能为打开控制台面板。
- 快捷键为 "Ctrl + Shift + C"。

### 帮助（Help）

About Unity

- 该命令功能为对此 Unity 集成开发环境的说明。

Manage License

- 该命令功能为对此 Unity 集成开发环境进行激活操作。

Unity Manual

- 该命令功能为打开 Unity 手册。

Scripting Reference

- 该命令功能为打开脚本手册。

Unity Connect

- 该命令功能为打开 Unity 云服务页面。

Unity Forum

- 该命令功能为打开 Unity 官方论坛。

Unity Answers

- 该命令功能为打开 Unity 问答页面。

Unity Feedback

- 该命令功能为打开 Unity 反馈页面。

Check for Updates

- 该命令功能为检查更新。

Download Beta

- 该命令功能为下载 Beta 版的 Unity。

Release Notes

- 该命令功能为打开发行说明页面。

Report a Bug

- 该命令功能为报告错误。
