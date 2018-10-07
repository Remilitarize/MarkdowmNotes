[toc]

## Unity 2D 基础介绍

使用 Unity 开发 2D 游戏需要创建一个专门的 2D 项目。
在 "New Project" 界面将项目类型设置为 2D 项目即可。

Unity 2D 主要包括 *2D 游戏对象 Sprite*、*2D 游戏换帧动画图片的制作工具* 以及 *2D 游戏物理引擎*。

## Unity 2D 核心功能对象——Sprite

### Sprite 对象的创建和基本用法

Sprite 对象的创建方法有两种。

- 执行 "GameObject &rarr; 2D Object &rarr; Sprite" 来创建一个空的 Sprite 对象。
	-	会包含一个 Sprite Renderer 组件，但是这个组件的 Sprite 参数是空的。
- 在项目中导入一张带有 Alpha 通道的贴图，设置贴图的 "Texture Type" 为 "Sprite"，然后将这张贴图拖拽到场景中。
	- 这种方法创建的 Sprite 对象的 Sprite Renderer 组件的 Sprite 参数就是这张贴图。

创建出来的 Sprite 对象和 3D 对象一样可以进行平移、旋转和缩放等基本变换。
只是因为 Sprite 对象是 2D 对象，所以对 z 轴的基本变换无效。

- Sprite 对象通过 Sprite Renderer 组件绘制在屏幕上。
	- 绘制的是 Sprite 参数设置的带有 Alpha 通道的贴图。
- Soring Layer 是专门用来设置 Sprite 对象之间的遮挡关系。
	- 通过在 Tag&Layers 界面的 Sorting Layer 中添加层，并且通过拖拽调整层遮挡的前后关系。
	- 设置 Sprite Renderer 组件的 Sorting Layer 参数，将 Sprite 对象放在某个层中。

### 换帧动画的制作

换帧动画制作之前首先需要制作换帧动画所需的图片。

1. 使用图片制作软件制作出包含每帧换帧贴图的整张图片。
2. 将图片导入到项目中，设置图片的 Texture Type 为 Sprite，设置 Sprite Mode 为 Multiple，表明改图片包含多张换帧贴图。
3. 点击 Sprite Editor 打开 Sprite Editor 工具。
	- Unity 默认通过图片 Alpha 通道的值自动分割贴图，但是尽量手动调整每个分离框的大小和位置。
4. Unity 2D 中制作换帧动画的方法有多种，原理都是通过定时改变 Sprite Renderer 组件的 Sprite 贴图来实现换帧动画的。
	- 常用的一种方法是通过脚本定时该笔那 Sprite Renderer 组件的 Sprite 参数来实现。
	- Unity 专门提供了一个制作动画的工具可以制作换帧动画。
		- 将制作换帧需要的贴图同时选中，一起拖拽到场景中就会弹出保存该换帧动画的对话框，保存完成后就会在场景中出现一个包含拖拽到场景中的贴图的换帧动画的精灵。
		- 选中该精灵，执行 "Window &rarr; Animation" 就会弹出修改该动画的 Animation 工具。
		- 通过 Animation 工具可以修改换帧动画的每帧贴图和换帧动画的播放速度。

## Unity 2D 中的物理引擎

### 2D 刚体

包含有该组件的游戏精灵对象，会遵循自然界的物理规律。

|属性|说明|
|-|-|
|velocity|速度向量|
|angularVelocity|角速度向量|
|drag|阻力|
|angularDrag|角阻力|
|fixedAngle|刚体是否可以旋转|
|gravityScale|受重力影响程度|
|mass|质量|
|sleepMode|休眠模式|
|isKinematic|是否受物理规律的影响|
|collisionDetectionMode|碰撞检测模式|
|interpolation|插值允许以固定的频率平滑物理运行效果|

- **质量（Mass）**
	- 表示刚体的质量。
	- 数据类型：`float`
	- 默认值：1
	- 该属性影响到刚体受到力后所表现的惯性力的大小。
- **线性阻力（Linear Drag）**
	- 表示刚体的线性阻力。
	- 数据类型：`float`
	- 默认值：1
- **旋转阻力（Angular Drag）**
	- 表示刚体的旋转阻力。
	- 数据类型：`float`
	- 默认值：0.05
- **重力影响程度（Gravity Scale）**
	- 表示刚体受重力影响的程度。
	- 数据类型：`float`
	- 默认值：1
	- 如果该属性值为 0，表示刚体不受重力影响。
- **冻结旋转（Fixed Angle）**
	- 表示该刚体的旋转是否收到物理规律的约束。
	- 默认状态下精灵对象绕自身中心点的旋转是受物理规律约束控制的。
	- 该属性被设为 `false` 时精灵对象的旋转将不受物理规律的控制。

|方法|说明|
|-|-|
|AddForce|施加一个力到刚体|
|AddForceAtPosition|在世界坐标系下指定位置给刚体施加一个力|
|AddRelativeForce|在物体自身坐标系下指定位置给刚体施加一个力|
|AddTorque|在刚体重心点施加一个力矩|
|GetPointVelocity|刚体在世界坐标空间中指定位置的速度|
|IsAwake|刚体是否在唤醒状态|
|IsSleeping|刚体是否在休眠状态|
|MovePosition|移动刚体到指定位置|
|MoveRotation|旋转刚体到指定角度|
|Sleep|强制刚体休眠至少一帧|
|WakeUp|强制唤醒一个刚体|

### 2D 碰撞器

Unity 中 2D 物理引擎提供了 4 种不同类型的碰撞器组件。
这 4 种碰撞器的基本功能相同，但碰撞器形状不同。

- 圆圈碰撞器（Circle Collider 2D）
	- 调整 Radius 参数可以改变半径长度
	- 调整 Offset 参数可以修改碰撞器的 x 和 y 轴偏移量。
- 盒子碰撞器（Box Collider 2D）
	- 调整 Size 参数可以改变碰撞器的长和宽。
	- 调整 Offset 参数可以修改碰撞器的 x 和 y 轴偏移量。
- 边缘碰撞器（Edge Collider 2D）
	- 适用于边缘许ing装非常复杂并且需要突出边缘形状细节的精灵对象。
	- 边缘碰撞器的边和可编辑的点的个数是不固定的，可以有无数多的边。
- 多边形碰撞器（Polygon Collider 2D）
	- 多边形碰撞器是由一个或多个多边形组成的碰撞器。
	- 当给精灵对象添加多边形碰撞器组件后，系统就会根据精灵对象贴图的 Alpha 通道值自动添加一个或多个多边形碰撞包围体。

> 多边形碰撞器与边缘碰撞器的不同之处是：边缘碰撞器只能在碰撞中表现出边缘形状，而多边形碰撞器可以通过多个多边形在精灵对象内部和外部同时在碰撞中表现。

碰撞器的共同属性：

|属性|说明|
|-|-|
|attachedRigidbody|碰撞器附加的刚体|
|bounds|碰撞器在世界坐标空间的包围盒|
|isTrigger|碰撞器是否是一个触发器|
|shapeCount|碰撞器中多边形的数量|
|material|碰撞器使用的材质|

碰撞器的共同方法：

- **OnCollisionEnter2D**
	- 当碰撞器/刚体开始触动另一个碰撞器/刚体时该方法被调用一次。
- **OnCollisionExit2D**
	- 当碰撞器/刚体停止触动另一个碰撞器/刚体时该方法被调用一次。
- **OnCollisionStay2D**
	- 当碰撞器/刚体触动碰撞器/刚体时，将在每帧调用该方法。
- **OnTriggerEnter2D**
	- 当碰撞器进入另一个触发器时该方法被调用一次。
- **OnTriggerExit2D**
	- 当碰撞器离开另一个触发器时该方法被带哦用一次。
- **OnTriggerStay2D**
	- 当碰撞器进入另一个触发器时，将在每帧调用该方法。

执行 "Create &rarr; Physics2D Material" 创建 2D 物理材质。

- Friction 参数用于设置物体的摩擦因数。
- Bounciness 参数用于设置物体的弹性系数。

### 2D 关节

添加 2D 关节组件的物体和关节的连接体都各自有一个锚点。
2D 关节模拟的物体间相对位置的内在联系事实上是两个锚点相对位置的内在联系。

Unity 中 2D 物理引擎提供了 5 种不同类型的 2D 关节组件。
这 5 种 2D 关节都是用于限制两个物体的相对位置，但功能各不相同。

- 弹簧关节（Spring Joint 2D）
	- 弹簧关节模拟了现实生活中弹簧的效果。
	- Distance 参数为弹簧在没有压缩和拉伸时的长度。
	- Damping Ratio 参数为弹簧的阻尼系数。
	- Frequency 参数为弹簧弹性运动的频率。
- 距离关节（Distance Joint 2D）
	- 距离关节模拟了现实生活中两个物体之间的距离固定不变的效果。
	- Distance 参数为两个物体固定不变的距离。
	- Max Distance Only 参数为是否保持最大距离。
- 铰链关节（Hinge Joint 2D）
	- 铰链关节模拟了现实生活中铰链的效果。
	- 具体效果是 2D 关节组件的物体和关节的连接体的两个锚点重合，连接体可以绕着这个锚点自由旋转。
	- Use Motor 参数为是否使用电动机。
		- 如果 Use Motor 参数为 "true"，关节的连接体就会根据 Motor 参数的值绕锚点自动旋转。
	- Use Limits 参数为是否限制旋转角度。
		- 如果 Use Limits 参数为 "true"，连接体就会限制旋转角度。
- 滑动关节（Slider Joint 2D）
	- 滑动关节模拟了现实生活中两个物体滑动的效果。
	- Use Limits 参数为是否限制最大相对距离。
		- 如果 Use Limit 参数为 "true"，两个物体就会根据 Translation Limits 参数限制最大相对距离。
	- Use Motor 参数为是否使用电动机。
		- 如果 Use Motor 参数为 "true"，物体就会自动滑动。
- 滚轮关节（Wheel Joint 2D）
	- 滚轮关节模拟了现实生活中滚轮的效果。
	- 与弹簧关节相似，但弹簧关节当没有压缩和拉伸时的长度为 0，且可以绕着锚点自由旋转。
	- Suspension 参数用于设置压缩和拉伸的阻尼系数和弹性运动的频率。
	- Use Motor 参数为是否使用电动机。
		- 如果 Use Motor 参数为 "true"，关节的连接体就会根据 Motor 参数的值绕锚点自动旋转。

关节的共同属性：

|属性|说明|
|-|-|
|collideConnected|关节组件的物体和关节的连接体是否能发生碰撞|
|connectedBody|关节的连接体|
|anchor|2D 关节组件的物体的锚点|
|connectedAnchor|连接体的锚点|
