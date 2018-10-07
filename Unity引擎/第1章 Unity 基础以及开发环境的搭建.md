[toc]

## Unity 基础知识概览

Unity 是由 Untiy Technologies 开发的一个能够轻松创建三维视频游戏、建筑可视化及实时三维动画等互动内容的、多平台的综合型开发工具，也是一个全面整合的专业游戏引擎。

- Unity 的图形引擎使用的是 *Direct3D（Windows）*、*OpenGL（Mac、Windows）* 和自有的 *APIs（Wii）*。
- Unity 支持很多主流的三维建模软件，但对 *3ds Max、Maya、Blender。Cinema 4D 和 Cheetah3D* 的支持效果比较好。
- Unity Shader（着色器）使用 *ShaderLab 语言*。Shader 对游戏画面的控制十分得心应手，具有易用、灵活和高性能的特性。
- Unity 内建强大的 *地形编辑器*，支持地形创建和树木与植被贴片等。
- Unity 内置了强大的 *多人联网游戏引擎*，具有 Unity 自带的客户端和服务器端。
- 物理引擎是模拟牛顿力学模型的一个计算机程序，使用质量、速度、摩擦力和空气阻力等变量，来预测各种不同情况下的效果。Unity 内置 NVIDIA 强大的 *PhysX 物理引擎*。
- Unity 音效系统基于 *OpenAL 程序库*，视频播放采用 *Theora 编码*，并支持实时三维图像混合音频流和视频流。
- Unity 游戏脚本为基于 Mono 的 *Mono 脚本*，是一个基于 .NET Framework 的开源语言，使用 *JavaScript、C#* 加以编写。
- Unity 资源服务器具有一个支持各种游戏和脚本版本的控制方案，使用 *PostgreSql* 作为后端。
- Unity 提供了具有柔和阴影与 lightmaps 的高度完善的光影渲染系统。*光照图（lightmap）* 是包含了视频游戏中面的光照信息的一种三维引擎的光强数据。Unity 5 融入了 Geomerics 的实时全局光照技术 *Enlighten*。
- Unity 4.3 版本以后正式加入了 *Unity 2D 游戏开发工具集*，集成了 Box2D 物理引擎并提供了一系列 2D 物理组件。

## Unity 开发环境的搭建

[Unity 官方网站](http://unity3d.com)

安装过程中注意 Choose Components 窗口中可选 *MonoDevelop（自带编辑器）*，如果已安装 Microsoft Visual Studio 可以不进行安装。

> Microsoft Visual Studio 需要额外关联 Unity 引擎。

**初次登陆需要注册账户，以后每次打开 Unity 都需要联网登陆。**

## 第一个 Unity 程序

1. 启动 Unity。
2. 单击 New project 来创建一个新工程。
3. 将工程重命名，选择 3D 选项。
4. 单击 Create project 按钮，完成创建。

进入 Unity 集成开发环境：

1. 单击菜单栏中 *GameObject* 菜单，选择 "3D Object" &rarr; "Cube"，创建一个 Cube。
2. 在 **Hierarchy** 窗口里双击刚刚创建的 Cube 对象，在 **Scene** 窗口的中心就会出现该 Cube 对象。
	- **Hierarchy** 窗口中会包含该工程包含的所有对象。
	- **Scene** 窗口为编辑状态下的预览，旁边的 **Game** 窗口为游戏开始时的预览。
3. 在 Hierarchy 窗口里单击刚刚创建的 Cube 对象，右侧的 **Inspector** 窗口会立即显示 Cube 对象的所有属性。
	- **Inspector** 窗口显示对象所有属性、组件和挂载脚本等。
4. 单击菜单栏的 *Assets* 菜单，选择 "Import New Asset" 命令，导入所需要使用的资源文件。
	- 可以通过直接将资源文件拖拽进 Unity 集成开发环境。
5. 为所创建的 Cube 对象添加合适的纹理贴图，就需要创建一个 **材质对象**。
	1. 执行 "Assets" &rarr; "Create" &rarr; "Material"，在 **Assets** 窗口就会生成一个 `New Materail.mat` 文件。
	2. 在 Inspector 窗口中单击 **Albedo** 前的 "⊙" 符号。
	3. 在弹出的 Select Texture 对话框中，选择合适的纹理贴图，关闭对话框。
6. 创建一个 Sphere 对象，将刚刚创建的材质对象拖拽到 Sphere 上。
7. 创建光源（平行光）："GameObject" &rarr; "Light" &rarr; "Directional Light"。
8. 在 Hierarchy 窗口单击 Main Camera（主摄像机），在 Inspector 窗口调整主摄像机的参数。
	- 单击住摄像机时，会在 Scene 窗口右下角弹出预览视角。
9. 为 Sphere 对象添加 **Rigibody（刚体）** 组件。
	1. 在 Hierarchy 窗口选中 Sphere。
	2. 单击 Inspector 窗口底部的 "Add Component" 按钮。
	3. 选择 "Physics" &rarr; "Rigibody"，并调整其属性。
	4. 在 Rigibody 属性中，一定要选中 "Use Gravity" 属性。
10. 如果想要球体具有弹性，就需要为球体对象添加 **物理材质**。
	1. "Assets" &rarr; "Create" &rarr; "Physic Material"。
	2. 在 Inspector 窗口设置 **Bounciness** 参数。
11. 一些准备完毕后，单击 **播放按钮**，运行 Unity 程序。
	- 再次单击即可结束。

注意：

- 如果球体没有下落，则可能没有添加刚体或未选中 "Use Gravity"。
- 如果球体在地面上静止不动，查看球体的初始高度并重新设置。
- 如果球体未反弹，则可能没有将物理材质挂在球体上。
