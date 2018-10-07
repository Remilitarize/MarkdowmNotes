[toc]

这里感谢：

[猫都能学会的Unity3D Shader入门指南（一）](https://onevcat.com/2013/07/shader-tutorial-1/)
[猫都能学会的Unity3D Shader入门指南（二）](https://onevcat.com/2013/08/shader-tutorial-2/)
[Unity3D Normal map、Diffuse map 和 Speculer map](https://www.cnblogs.com/xiuj/p/5875461.html)

## 初识着色器

游戏开发中的很多特效，如镜面反射和折射、动物毛发、卡通效果等，都是使用着色器来实现的。

### 着色器概述

着色器——Shader 是一款运行在 **图形处理单元（Graphic Processor Unit，GPU）** 上的程序，其可以让开发人员对图形硬件的渲染功能进行设置。
Unity 中大多数的渲染都是通过着色器来完成的。
Unity 中有大量内置着色器程序，开发人员可以直接使用，也可以根据需求开发自己的着色器程序。

目前这种面向 GPU 的编程有以下 3 种高级图像语言可供选择。

- *HLSL 语言*
	- Microsoft 公司提供的 HLSL（High Level Shading Language）语言，是通过 Direct3D 图形软件库来编写着色器程序。
	- 只能供 Microsoft 的 Direct3D 和 XNA 使用。
- *Cg 语言*
	- NVIDIA 公司和微软公司合作提供了 Cg（C for Graphics）语言。
	- Cg 语言与 C 语言相似，不过有了自己的一套关键词和函数库。
	- Cg 是独立于三维编程接口的，完全和 Direct3D 或者 OpenGL 结合在一起。
- *GLSL 语言*
	- OpenGL 委员会提供了 GLSL（OpenGL Shading Language）语言。
	- 它是用来在 OpenGL 中继续着色编程的语言。

Unity 引擎对着色语言的支持非常全面，但为了实现对跨平台性的支持，Unity 对着色语言的重点支持 **Cg 语言**。
作为一款跨平台性最好的游戏开发引擎，Unity 使用自定义 **ShaderLab** 来组织着色器程序的内容。

### ShaderLab 语法基础

#### Shader

**Shader** 是一个着色器程序的根命令

- 每个着色器程序都必须定义唯一一个 Shader。
- 其中定义了材质如何使用这个着色器渲染对象。

```
Shader "name"{
	[Properties]
	Subshader {...}
	[Fallback]
}
```

- 上面的语句定义了一个名为 **"name"** 的 Shader，这些内容在材质查看器上列于 "name" 下。
- 着色器程序通过 **"Properties"** 来可选地定义一个显示在材质设定界面的属性列表。
	- 任何定义在着色器程序中的属性都会显示在属性查看器中。
- 后面紧跟着 **"SubShader"** 的列表。
	- 至少有一个子着色器。
	- 当加载一个着色器程序时，Unity 将遍历这个列表，获取 **第一个能被用户机器支持的子着色器**。
	- 如果没有子着色器被支持，Unity 将尝试使用降级着色器，即 **Fallback** 操作。
- 可额外添加一个代码块用于应对 **"Fallback"** 的情况。

#### Properties

着色器程序中的 Properties 块就是用来 **定义参数** 的地方，可以在属性查看器面板中进行编辑和调整。

```
Properties { 属性块 }
```

|类型|说明|
|-|-|
|name("display name", **Range(min, max)**) = num|定义浮点数范围属性，在属性查看器中可通过一个标注了最大值和最小值的滑动条来修改|
|name("display name", **Float**) = num|定义浮点数属性|
|name("display name", **Int**) = num|定义整型属性|
|name("display name", **Color**) = (num, num, num, num)|定义颜色属性，num 取值范围 0 ~ 1|
|name("display name", **Vector**) = (num, num, num, num)|定义四维向量属性|
|name("display name", **2D**) = "name" {options}|定义 2D 纹理属性，缺省值为："white"/"black"/"gray"/"bump"|
|name("display name", **Rect**) = "name" {options}|定义矩形纹理（尺寸非 2 次方）属性，缺省值同 2D 纹理属性|
|name("display name", **Cube**) = "name" {options}|定义立方贴图纹理属性，缺省值同 2D 纹理属性|
|name("display name", **3D**) = "name" {options}|定义 3D 纹理属性|

```
Properties{
	_RangeValue("Range Value", Range(0.1, 0.5)) = 0.3
}
```

- 包含在着色器程序中的每一个属性通过 **"name"** 索引。
	- 在 Unity 中，通常使用 **下划线** 来开始一个着色器属性的名字。
	- 属性值通过 "name" 来访问。
- 属性会将 "display name" 显示在属性查看器中。
- 等号后可以为每个属性提供 **缺省值**。
- 包含在纹理属性的大括号中的 **"options"**（选项）是可选的。
	- 选项名称：*TexGen*
		- 纹理生成模式，纹理自动生成纹理坐标时的模式。
		- 可以是 *ObjectLinear、EyeLinear、SphereMap、CubeReflect 或 CubeNormal*。
		- 这些模式和 OpenGL 纹理生成模式相对应。
		- 如果使用自定义顶点片元着色器，那么纹理生成将被忽略。
	- 选项名称：*LightmapMod*
		- 光照贴图模式。
		- 如果给出这个选项，纹理会被渲染器的光线贴图所影响。
		- 即纹理不能被应用在材质中，而是使用渲染器中的设定。

```
Properties{
	_RangeValue ("Range Value", Range(0.1, 0.5)) = 0.3  // 定义一个浮点数范围属性
	_FloatValue ("Float Value", Flott) = 1.5            // 定义一个浮点数属性
	_Color ("Color", Color) = (1, 1, 1, 1)              // 定义一个颜色属性
	_Vector ("Vector", Vector) = (1, 1, 1, 1)           // 定义一个四维向量属性
	_MainTex ("Albedo (RGB)", 2D) = "white" {TexGen EyeLinear} // 定义 2D 纹理属性
	_Cube ("CubeTex", Cube) = "skybox" {TexGen CubeReflect} // 定义立方贴图纹理属性
}
```

#### SubShader

真正用于呈现渲染物体的是在 SubShader 中实现的，使用 SubShader 的目的在于能使开发者 *针对不同性能的显卡编写不同的着色器程序*。
Unity 中的每一个着色器都包含一个 SubShader 的列表，Unity 运行时会针对实际的运行环境，在列表中从上到下选出第一个被用户显卡支持的 SubShader 来呈现效果。

```
SubShader { [Tags] [CommonState] Pass{}}
```

- 子着色器由 **可选标签（Tags）、通用状态（CommonState）和一个通道（Pass）列表** 构成。

#### SubShader Tags

子着色器使用标签（Tags）来告诉 Unity 渲染引擎或者其他开发人员如何认证这个 SubShader。

```
Tags {"标签1" = "值1" "标签2" = "值2"}
```

> 标签的标准是 **键值对**，可以有任意多个。

常用的标签如下：

***Queue tag —— 队列标签***

- Queue 标签用来决定对象被渲染的次序。
- 着色器决定对象所归属的渲染队列，任何透明物体都可以通过这种方法确保自身在不透明物体渲染之后渲染。

ShaderLab 中有 5 中预定义的可选值。

- *Background（背景）*，对应值为 1000。
- *Geometry（几何体，默认值）*，对应值为 2000。
- *AlphaTest（Alpha 测试）*，对应值为 2450。
- *Transparent（透明）*，对应值为 3000。
- *Overlay（覆盖）*，对应值为 4000。

```
Tags {"Queue" = "Transparent"}
```

> 透明渲染队列为了达到最优的性能，优化了对象绘制次序，其他渲染队列根据距离来排序对象，从最远的对象开始，**由远至近** 渲染。

自定义队列标签，对于特殊的要求可以使用中间队列来满足。
每一个队列都有自己的对应值，通过着色器可以自定义一个队列。

```
Tags {"Queue" = "Geometry + 600"}
```

上面的代码是对象的设置渲染队列为 Geometry + 600，即 2600，在 AlphaTest 队列和 Transparent 队列之间渲染。

***RenderType tag —— 渲染类型标签***

- RenderType 标签将着色器分为若干个预定义组，由着色器替换使用。

渲染类型标签可选值

|队列名称|说明|
|-|-|
|Opaque|不透明，用于大多数着色器（法线着色器、自发光着色器、反射着色器以及地形着色器）|
|Transparent|透明，用于大多数半透明着色器（透明着色器、粒子着色器、字体着色器、地形额外通道着色器）|
|TransparentCutout|遮蔽的透明着色器（透明镂空着色器、两个通道植被着色器）|
|Background|天空盒着色器|
|Overlay|GUITexture、光晕着色器、闪光着色器|
|TreeOpaque|地形引擎树皮着色器|
|TreeTransparentCutout|地形引擎树叶|
|TreeBillboard|地形引擎布告板树|
|Grass|地形引擎草|
|GrassBillboard|地形引擎布告板草|

***DisableBatching tag —— 禁用批处理标签***

某些着色器（大部分是进行物体空间顶点变形的）在进行描绘调用批处理时会不起作用。
使用 DisableBatching 标签可以用来指示这种情况。

DisableBatching 标签有三个可选值：

- "True"（这个着色器将一直禁用批处理）
- "False"（不禁用批处理，默认值）
- "LODFading"（当 LOD Fading 被激活时禁用批处理）

***ForceNoShadowCasting tag —— 强制不投影标签***

当给定 ForceNoShadowCasting 标记并且该标记有 "true" 时，使用该子着色器渲染的对象将永不投射阴影。
当在透明对象上使用着色器替换，但不想从另一个子着色器获得阴影通道时，这会非常有用。

***IgnoreProjecttor tag —— 忽略投影标签***

如果设置 IgnoreProjecttor 标签为 "true"，那么使用这个着色器的对象将不会被投影器所影响。
对 *半透明* 物体来说最有用，因为这样它就不会受到投影器的影响而产生阴影。

***CanUseSpriteAtlas tag —— 使用精灵图集标签***

若该着色器用于精灵对象上，如果设置为 "false"，当精灵被打包进图集后，着色器就不会起作用。

***PreviewType tag —— 预览类型标签***

PreviewType 标签指示出材质检视器应该怎样展示材质文件。
默认情况下，是以材质球的形式展示。
该标签可以设置为 "Plane"（以 2D 形式展示）或者 "Skybox"（作为天空盒展示）。

#### Pass

SubShader 包装了一个渲染方案，而这个方案是由一个个 **通道（Pass）** 来执行的。
SubShader 可以包括多个 Pass 块，每个 Pass 都能使几何对象被渲染一次。

```
Pass {[Name and Tags] [RenderSetup] [TextureSetup]}
```

- 基本的通道命令包含一个 **可选的渲染设置命令（RenderSetup）的列表** 和 **可选的纹理设置命令（TextureSetup）的列表**。
- 一个通道能定义它的 **Name** 和任意数量的 **Tags（用于向渲染引擎传递通道的意图的名称/值的字符串）**。
- Pass 块的 Name 一般用来引用此 Pass，可以在其它着色器程序的 Pass 块中多次引用。

> 由于 Unity 的原因，Name 命名时必须大写。

通道渲染设置命令

|命令|含义|说明|
|-|-|-|
|Lighting|光照|开启或关闭顶点光照，开关状态的值为 On 或 Off|
|Material（材质块）|材质|定义一个使用顶点光照管线的材质|
|ColorMaterial|颜色集|当计算顶点光照时使用顶点颜色，颜色集可以是 AmbientAndDiffuse 或 Emission|
|SeparateSpecular|开关状态|开启或关闭顶点光照相关的镜面高光颜色，开关状态的值为 On 或 Off|
|Color|颜色|设置当顶点光照关闭时所使用的颜色|
|Fog（雾块）|雾|设置雾参数|
|AlphaTest|Alpha 测试|Less、Greater、LEqual、GEqual、Equal、NotEqual、Always（小于、大于、小于等于、大于等于、等于、不等于、一直），默认值为 LEqual|
|ZTest|深度测试模式|设置深度测试模式，有 Less、Greater、LEqual、GEqual、Equal、NotEqual、Always|
|ZWrite|深度写模式|开启或关闭深度写模式，开关状态的值为 On、Off|
|Blend|混合模式|设置混合模式，混合模式有 SourceBlendMode、DestBlendMode、AlphaSourceBlendMode、AlphaDestBlendMode|
|ColorMask|颜色遮罩|设置颜色遮罩，颜色值可以是 RGB 或 A 或 0 或任意 R/G/B/A 的组合，设置为 0 将关闭所有颜色通道的渲染|
|Offset|偏移因子|设置深度偏移，设置深度偏移，这个命令仅接受常数参数|

上面讲到的通道为 **普通通道（RegularPass）**。
还有两个特殊的通道能用于反复利用普通通道或是实现一些高级特效。

|通道名称|语法|说明|
|-|-|-|
|UsePass|UsePass"Shader/Name"|插入所有来自给定着色器中的给定名字的通道。Shader 为着色器的名字，Name 为通道的名字。|
|GrabPass|GrabPass{["纹理名"]}|捕获屏幕到一个纹理，该纹理通常使用在靠后的通道中。"纹理名"是可选项。|

- 在着色器中通过 `UsePass` 重用其他着色器中已存在的通道，提高代码重用率。
- 为了让 `UsePass` 能正常工作，必须给希望使用的通道命名，使用 `Name` 命名。

```
UsePass "Specular/BASE"  // 插入晶面高光着色器中名为 "BASE" 的通道
Name "MyPassName"        // 通道命名为 MyPassName
```

- `GrabPass` 会捕捉物体所在位置的屏幕的内容并写入一个纹理中。
- `GrabPass` 同样可以使用 `Name` 和 `Tags` 命令。

```
GrabPass {}
```

上述写法会捕获当前屏幕的内容到一个纹理中，在后续通道中通过 **`_GrabTexture`** 访问。

```
GrabPass {"纹理名"}
```

上述写法会捕获屏幕内容到一个纹理中，但只会在每帧中处理第一个使用该给定纹理名的纹理对象。
该纹理在后续的通道中可以以通道给定的纹理名访问。
适用于当一个场景中拥有多个使用 `GrabPass` 的对象。

#### Fallback

**降级（Fallback）** 定义在所有子着色器后，表示 "如果没有任何子着色器能被运行到当前硬件上，请尝试使用降级着色器"。

- `Fallback "着色器名"`
	- 退回到给定名称的着色器。
- `Fallback Off`
	- 显示声明没有降级并且不会打印任何警告，甚至没有子着色器会被当前硬件运行。

#### CustomEditor

开发人员可以为着色器定义 **自定义编辑器（CustomEditor）**。
执行此操作时，Unity 会查找以该名称拓展 `MaterialEditor` 的类，如果找到一个，则使用该着色器的所有材质都将使用这个材质检视器。

```
CustomEditor "name"
```

> CustomEditor 会影响使用该着色器程序的所有材质。

#### Category

**分类（Category）** 是渲染命令的逻辑组。
大多数情况下被用于继承渲染状态。

```
Shader "example"{
	Category{
		Fog {Mode Off}       // 关闭雾效果
		Blend One One        // 关闭混合
		SubShader {...}
		SubShader {...}
		...
	}
}
```

### 着色器中涉及的各种空间概念

要绘制出屏幕上绚丽多彩的 3D 场景画面，就需要将每个物体从自己所属的 **物体空间** 依次经 **世界空间**、**摄像机空间**、**剪裁空间**、**标准设备空间** 进行变换，追钟达到 **实际窗口空间**。

#### 物体空间

物体空间就是需要绘制的 3D 物体所在的原始坐标系代表的空间。

- 在 Unity 脚本中，可以通过 **`transform.worldToLocalMatrix` 矩阵的 `MultiplyPoint`、`MultiplyPoint3x4` 和 `MultiplyVector` 方法**，将用世界坐标表达的矢量转换为该物体用物体空间表达的矢量。
- 在着色器编程中，可以通过 **左乘 `_World2Object` 矩阵** 来实现。

> 在进行设计时，一般以物体的 **几何中心** 为坐标系原点，人物模型一般是以 **双脚的中心点** 为物体坐标系原点。

#### 世界空间

世界空间就是物体在最终 3D 场景中的摆放位置对应的坐标所属的坐标系代表的空间。
由于每个物体的模型空间都是处理自身内部的相对关系，无法处理自身以外与其他物体之间的关系，所以就需要一个统一的空间坐标来管理所有物体，用于表达空间中各个模型的相对关系、大小、旋转姿态等。

- 在 Unity 脚本中，可以通过 **`transform.localToWorldMatrix` 矩阵的 `MultiplyPoint`、`MultiplyPoint3x4` 和 `MultiplyVector` 方法**，将用物体空间表达的矢量转换为用世界坐标表达的矢量。
- 在着色器编程中，可以通过 **左乘 `_Object2World` 矩阵** 来实现。

#### 摄像机空间

物体经摄像机观察后，进入摄像机空间。
摄像机空间指的是 *以观察场景的摄像机为原点* 的一个特定坐标系代表的空间。
在这个坐标系中，**摄像机位于原点，视线沿 x 轴负方向，y 轴方向与摄像机的 UP 向量方向一致**。

在着色器编程中，可以通过 **UNITY_MATRIX_MV 矩阵** 将物体从模型空间转换到摄像机空间。

#### 剪裁空间

对于平行投影来说，**视景体** 是一个四边平行于投影方向的四棱柱。
对于透视投影来说，视景体是一个以近平面为上底、远平面为下底的棱台。

并不是摄像机空间中所有的物体都能最终被观察到，只有在摄像机空间中，并且位于视景体内的物体才能被观察到。
将摄像机空间内视景体内的部分独立出来经过处理后，就成为裁剪空间。

在着色器编程中，可以通过 **`UNITY_MATRIX_MVP`** 一次性完成物体从物体空间到摄像机空间再投影到屏幕上的变换。

#### 标准设备空间

标准设备空间就是对裁剪空间执行透视除法后得到的空间。
所谓透视除法，就是将齐次坐标 [x, y, z, w] 的 4 个分量 *都除以 w*，结果为 [x/w, y/w, z/w, 1]，本质上就是对齐次坐标进行了规范化。

#### 实际窗口空间

实际窗口空间一般代表的是设备屏幕上的一块矩形区域，坐标以像素为单位。
转换到该空间的主要工作是将执行透视除法后的 x、y 坐标分量转换为实际窗口的 xy 像素坐标。
主要的思路是将标准设备空间的 xy 平面对应到视口上，将 -1.0 ~ 1.0 内的 x、y 坐标折算为视口上的像素坐标。

## 着色器的 3 种形态

### 固定管线着色器

固定管线是在老一代 GPU 能力比较有限时，对着色器的约束性比较高的一种形态。

> 为了市场占有率，新一代的显卡仍对其有所选择地进行支持，但会在未来被逐步淘汰。

```
Shader "Custom/BaseForm1" {
	Properties{                                            // 定义属性快
		_Color ("Main Color", Color) = (1, 1, 1, 0.5)        // 定义主颜色数值
		_SpecColor ("Sec color", Color) = (1, 1, 1, 1)       // 定义高光颜色数值
		_Emission ("Emission Color", Color) = (0, 0, 0, 0)   // 定义自发光颜色数值
		_Shininess ("Shininess", Range(0.01, 1)) = 0.7       // 定义高光系数数值
		_MainTex ("Base (RGB)", 2D) = "white" {}             // 定义纹理数值
	}
	SubShader{
		Pass{
			Material{                 // 材质快
				Diffuse [_Color]        // 漫反射
				Ambient [_Color]        // 环境光
				Shininess [_Shininess]  // 高光系数
				Specular [_SpecColor]   // 高光
				Emission [_Emission]    // 自发光
			}
		}
		Lighting On                 // 开启光照
		SeparateSpecular On         // 允许高光使用一个不同于主颜色的颜色
		SetTexture [_MainTex]{      // 处理纹理块
			constantColor [_Color]    // 定义颜色值
			Combine texture*primary DOUBLE, texture*constant  // 计算最终颜色
		}
	}
}
```

- SubShader 材质块：
	- 在固定管线着色器中材质块里面把在属性块中定义的数制映射到固定管线光照所有的属性上。
	- 除了使用在定义属性块定义的属性外，材质块中也可以直接使用数值，比如 `Specular(1, 1, 1, 1)`。
- SetTexture 处理纹理块：
	- 首先定义了一个常量颜色值 `constantColor`。
	- 除了使用在定义属性快定义的属性外，也可以直接使用数制，如 `constantColor(1, 1, 1, 0.5)`。
	- `Combine` 语句被逗号分开的两部分，前面是对颜色的计算，后面则是对 Alpha 的计算。
	- `texture` 是对方括号中的纹理贴图的引用。
	- `primary` 是上一步的顶点光照。
	- `constant` 是 `constantColor` 定义的颜色值。

### 顶点片元着色器

顶点片元着色器为可编程着色器，相对于固定管线着色器可以给开发人员更大的发挥空间，但它的缺点是不能直接和光照交互。
着色器程序用 Cg 或 HLSL 语言编写，嵌入在着色器的渲染通道块中。

Cg 程序代码片段被编写在 **`CGPROGRAM` 和 `ENDCG`** 之间。

#### 编译指令

在代码片段编译指令的开头，可以使用 **`#pragma` 指令** 来控制着色器代码的编译。

|编译指令|说明|
|-|-|
|`#pragma vertex <name>`|将名称为 "name" 的函数编译为顶点着色器|
|`#pragma fragment <name>`|将名称为 "name" 的函数编译为片元着色器|
|`#pragma fragmentoption <optime>`|添加 "optime" 到已编译的 OpenGL 片元程序|
|`#pragma target <name>`|要编译成哪个着色器目标|

> 每个代码片段都必须包含一个顶点程序或一个片元程序或两者皆包括。因此，要求必须使用一个 `#pragma vertex` 指令或一个 `#pragma fragment` 指令或两者都使用。

#### 顶点数据结构体

顶点着色器中顶点数据必须以一个 **结构体** 的形式提交给 Cg/HLSL 顶点程序。
几个常用的顶点结构定义在 **`UnityCG.cginc`** 文件中。

- `appdata_base`
	- 由顶点位置、法线和一个纹理坐标构成。
	- `vertex` 为顶点坐标。
	- `normal` 为法线。
	- `texcoord` 为纹理坐标。
- `appdata_tan`
	- 由顶点位置、切线、法线和一个纹理坐标构成。
	- `tangent` 为切线。
- `appdata_full`
	- 由顶点位置、切线、法线、两个纹理坐标以及颜色构成。
	- `texcoord` 为第一个纹理坐标。
	- `texcoord1` 为第二个纹理坐标。
	- `color` 为颜色。

#### 内置变换矩阵

- 顶点着色器处理传入的顶点数据，处理完成后返回通过总变换矩阵变换的顶点位置。
- 片元着色器处理从顶点着色器传出的经过光栅化的片元数据，处理完成后返回片元的最终颜色。

|变换矩阵|说明|
|-|-|
|UNITY_MATRIX_MVP|基本变化矩阵&times;摄像机矩阵&times;投影矩阵|
|UNITY_MATRIX_MV|基本变化矩阵&times;摄像机矩阵|
|UNITY_MATRIX_V|摄像机矩阵|
|UNITY_MATRIX_P|投影矩阵|
|UNITY_MATRIX_VP|摄像机矩阵&times;投影矩阵|
|UNITY_MATRIX_T_MV|（基本变化矩阵&times;摄像机矩阵）的转置矩阵|
|UNITY_MATRIX_IT_MV|（基本变化矩阵&times;摄像机矩阵）的逆转置矩阵|
|UNITY_MATRIX_TEXTURE0|纹理变换矩阵|
|_Object2World|从自身坐标转到世界坐标的矩阵|
|_World2Object|从世界坐标转到自身坐标的矩阵|

```
Shader "Custom/MyWater" {						          //定义了一个着色器，名称为MyWater
	Properties {								                //属性列表,用来指定这段代码将有哪些输入				
		_MainTex ("Base (RGB)", 2D) = "white" {}  //定义一个2D纹理属性，默认白色
		_Aim1("Aim1",Vector) = ( 3, 0, 3, -2.5)   //波源位置
		_Aim2("Aim2",Vector) = ( 5, 0, -5, 2.0)      
		_Aim3("Aim3",Vector) = (-3, 0, -3, 1.0)      
		_Aim4("Aim4",Vector) = (-5, 0, 5,  0.5)
		_High("High",Float) = 1
	}
	SubShader {									    //子着色器
		Pass{									        //通道
			CGPROGRAM							      //开始标记
			#pragma vertex verf					//定义顶点着色器
			#pragma fragment frag				//定义片元着色器
			#include "UnityCG.cginc"		//引用Unity自带的函数库

			sampler2D _MainTex;					//2D纹理属性
			float4 _Aim1;
			float4 _Aim2;
			float4 _Aim3;
			float4 _Aim4;
			float4 _MainTex_ST;
			float _High;

			struct v2f {						    //定义一个结构体
				float4 pos:POSITION;			//声明顶点位置
				float2 uv:TEXCOORD0;		  //声明纹理
			};

			v2f verf(appdata_base v)		//顶点着色器
			{
				v2f o;							      //声明一个结构体对象
				//计算当前顶点与_Aim1、_Aim2、_Aim3、_Aim4的距离
				float dis1 = distance(v.vertex.xyz,_Aim1.xyz);
				float dis2 = distance(v.vertex.xyz,_Aim2.xyz);
				float dis3 = distance(v.vertex.xyz,_Aim3.xyz);
				float dis4 = distance(v.vertex.xyz,_Aim4.xyz);
				//计算当前顶点的高度
				float H = sin(dis1*_Aim1.w+_Time.z *_High)/5;	//计算正弦波的高度
				H += sin(dis2*_Aim2.w + _Time.z*_High)/10;	  //叠加正弦波的高度
				H += sin(dis3*_Aim3.w + _Time.z*_High)/15;	  //叠加正弦波的高度
				H += sin(dis4*_Aim4.w + _Time.z*_High)/10;	  //叠加正弦波的高度
				o.uv = TRANSFORM_TEX(v.texcoord,_MainTex);

				o.pos = mul(unity_ObjectToWorld,v.vertex);		//将顶点转换到世界坐标的矩阵
				o.pos.y = H;									                //顶点的Y值赋为H
				o.pos = mul(unity_WorldToObject,o.pos);				//将顶点转换到自身坐标的矩阵
				o.pos = UnityObjectToClipPos(o.pos);			    //计算顶点位置

				return o;										                  //返回顶点着色器对象
			}

			fixed4 frag(v2f i):COLOR
			{
				float4 texCol = tex2D(_MainTex,i.uv);	        //获取顶点对应UV的染色
				return texCol;						                    //返回顶点染色
			}
			ENDCG									        //着色器结束标志
		}
	}
	FallBack "Diffuse"								//降级着色器（备用的着色器）
}
```

## Cg 数据类型

Cg 支持 7 种基本的数据类型：

- `float`
	- 32 位浮点数据，一个符号位。
	- 浮点数据类型被所有的 profile 支持（但是 DirectX8 pixel profiles 在一些操作中降低了浮点数的精度和范围）。
- `half`
	- 16 为浮点数据。
- `int`
	- 32 位整形数据。
	- 有些 profile 会将 `int` 类型作为 `float` 类型使用。
- `fixed`
	- 12 位定点数。
	- 被所有的 fragment profiles 所支持。
- `bool`
	- 布尔数据。
	- 通常用于 if 和条件操作符（`?:`）。
	- 布尔数据类型被所有的 profiles 支持。
- `sampler`
	- 纹理对象的句柄，分为 6 类：
		- `sampler`，`sampler1D`，`sampler2D`，`sampler3D`，`samplerCUBE` 和 `samplerRECT`。
	- DirectX profiles 不支持 `samplerRECT` 类型，除此之外这些类型被所有的 pixel profiles 和 NV40 vertex program profile 所支持（CgUsersManual 30 页）。

## 表面着色器

### 表面着色器基础知识

#### 编译指令

表面着色器与其他任何着色器一样放置于 `CGPROGRAM ... ENDCG` 块中。

> 区别是必须将其放置于 **子着色器块** 中，而不能放在通道中。

表面着色器自身会编译为多个通道。
使用 **`#pragma surface`** 指令来表明它是个表面着色器

```
#pragma surface <surfaceFunction> <lightModel> [optionalparams]
```

- `<surfaceFunction>` 为 **表面着色器函数名称**。
	- 告诉编译器 Cg 代码中 `surfaceFunction` 函数为表面着色器函数。
- `<lightModel>` 为 **光照模型**。
	- 告诉编译器这个表面着色器使用哪个光照模型。
	- Unity 内置的光照模型为 *`Lambert（漫发射）`、`BlinnPhong（亮光）`*。
	- 也可以自定义光照模型。
- `[optionalparams]` 为可选参数。

|可选参数|说明|
|-|-|
|alpha|Alpha 混合模式，将该参数用于半透明着色器|
|alphatest:VariableName|Alpha 测试模式，将该参数用于透明镂空着色器，镂空值（VariableName）为浮点型变量|
|vertex:VertexFuntion|自定义名为 "VertexFunction" 的顶点函数|
|finalcolor:ColorFunction|自定义名为 "ColorFunction" 的最终颜色修改函数|
|exclude_path:prepass|使用指定的渲染路径|
|exclude_path:forward|使用指定的渲染路径|
|addshadow|添加阴影投射器和集合通道|
|dualforward|将双重光照贴图用于正向渲染路径中|
|fullforwardshadows|在正向渲染路径中支持所有阴影类型|
|decal:add|附加印花着色器|
|decal:blend|附加半透明印花着色器|
|softvegetation|使表面着色器仅在 Soft Vegetation 开启时被渲染|
|noambient|不使用任何环境光照或者球面调和光照|
|novertexlights|在正向渲染中不适用球面调和光照或逐顶点光照|
|nolightmap|在这个着色器上禁用光照贴图|
|nodirlightmap|在这个着色器上禁用方向光照贴图|
|noforwardadd|禁用正向渲染添加通道，这会使这个着色器支持一个完整的方向光和所有逐顶点/SH 计算的光照|
|approxview|对于有需要的着色器，逐顶点而不是逐像素计算规范化视线方向。<sub>1</sub>|
|halfasview|将平方向向量（而非视线方向向量）传递到光照函数中。<sub>2</sub>|

1. 这种方法更快速，但当相机靠近表面时，视线方向不会完全正确
2. 半方向向量将会被逐顶点计算和规范化。这种方法更快速，但不会完全正确

此外，还可以在 `CGPROGRAM` 块中编写 `#pragma debug`，然后表面编译器将产生大量生成代码的注释。
可以在着色器检视器中使用开放的编译着色器进行查看。

#### 输入输出参数结构体

表面着色器函数可以有两个参数：

- 其中一个参数为 **`Input` 结构体**，用于为表面着色器函数输入所需的纹理坐标和其他的数据。
	- `Input` 结构体中的纹理坐标必须在纹理名称前面加上 *`uv` 或 `uv2`*。
	- 带 `uv` 的纹理坐标为物体所带的第一个纹理坐标。
	- 如果物体带有第二个纹理坐标，则带 `uv2` 的纹理坐标为物体所带的第二个纹理坐标。
	- `Input` 结构体可以包含自定义数据，用于从定点函数传递数据给表面着色器函数。
- 另一个参数为 **`SurfaceOutput` 结构体**，需在表面着色器函数中写入相应的值，用于输出数据。
	- 该结构体是内置定义好的，只需在表面着色器函数中为需要的变量赋值即可。
	- 也可以自定义表面着色器的输出结构体。
		- 但自定义的结构体必须包含 `SurfaceOutput` 结构体中的所有变量。
		- 然后可以添加自己需要的变量用于从自定义光照模型函数传递数据给表面着色器函数。

Input 结构体其他可用的数据

|可用的数据|说明|
|-|-|
|float3 viewDir|视图方向。为了计算视差、边缘光照等效果，Input 需要包含视图方向|
|float4 color|每个顶点颜色的插值|
|float4 screenPos|屏幕空间中的位置，为了获得反射效果，需要包含屏幕坐标|
|float3 worldPos|世界坐标空间位置|
|float3 worldRefl|世界空间中的反射向量，但必须表面着色器不写入 `o.Normal` 参数|
|flaot3 worldNormal|世界空间中的法线向量，但必须表面着色器不写入 `o.Normal` 参数|
|float3 worldRefl; INTERNAL_DATA|世界坐标反射向量，但必须表面着色器写入 'o.Normal' 参数。 <sub>1</sub>|
|float3 worldNormal; INTERNAL_DATA|世界坐标法线向量，但必须表面着色器写入 'o.Normal' 参数。<sub>2</sub>|

1. 要基于逐像素法线贴图获得反射向量，请使用 `WorldReflectionVector(IN, o.Normal)`。
2. 要基于逐像素法线贴图获得法线向量，请使用 `WorldNormalVector(IN, o.Normal)`。

```
struct SurfaceOutput {
	half3 Albedo;    // 漫反射的颜色值
	half3 Normal;    // 法线坐标
	half3 Emission;  // 自发光颜色
	half Specular;   // 镜面反射系数
	half Gloss;      // 光泽系数
	half Alpha;      // 透明度系数
}
```

#### 自定义光照模型

编写表面着色器就是描述一个表面的属性（如反射率、颜色、法线等），并由光照模型完成光照交互的计算。
系统内置了 **`Lambert`（漫反射光照）** 和 **`BlinnPhong`（高光光照）** 两个光照模型。
有时也需要开发自定义光照模型。

- 自定义的光照模型是由名称为 **`Lighting` 开头** 的函数实现的。
- 自定义光照模型函数的声明有以下几种形式，用于不同的需求：
	- `half4 Lighting<Name> (SurfaceOutput s, half3 lightDir, half atten)`
		- 其在正向渲染路径中用于非与视线方向相关的光照模型（漫反射等）。
	- `half4 Lighting<Name> (SerfaceOutput s, half3 lightDir, half3 viewDir, half atten)`
		- 其在正向渲染路径中用于与视线方向相关的光照模型。
	- `half4 Lighting<Name>_PrePass (SurfaceOutput s, half4 light)`
		- 其用于延时光照路径中的光照模型。
- 参数解释：
	- `SurfaceOutput` 结构体用于和表面着色器函数传输数据。
	- `lightDir` 参数为点到光源的单位向量。
	- `viewDir` 参数为点到摄像机的单位向量。
	- `atten` 参数为光源的衰减系数。

```
Shader "Custom/BaseForm3" {
  Properties {
    _Color ("Color", Color) = (1,1,1,1)								// 主颜色数值
    _MainTex ("Albedo (RGB)", 2D) = "white" {}				// 2D纹理数值
    _Shininess ("Shininess ", Range(0,10)) = 10				// 镜面反射系数
  }
  SubShader {
    CGPROGRAM
    #pragma surface surf Phong						// 表面着色器编译指令
    sampler2D _MainTex;										// 2D纹理属性
    fixed4 _Color;												// 主颜色属性
    float _Shininess;											// 镜面反射系数属性
    struct Input {
      float2 uv_MainTex;									// uv纹理坐标
    };
    float4 LightingPhong(SurfaceOutput s, float3 lightDir,half3 viewDir, half atten){  //光照模型函数
      float4 c;
      float diffuseF = max(0,dot(s.Normal,lightDir));		// 计算漫反射强度
			// 简单解释就是一个点的反射光强是和该点的法线向量和入射光向量和强度和夹角有关系的，其结果就是这两个向量的点积。
      float specF;
      float3 H = normalize(lightDir+viewDir);						// 计算视线与光线的半向量
      float specBase = max(0,dot(s.Normal,H));					// 计算法线与半向量的点积
      specF = pow(specBase,_Shininess);						      // 计算镜面反射强度
      c.rgb = s.Albedo * _LightColor0 * diffuseF * atten + _LightColor0 * specF;
			// _LightColor0 由 Unity 根据场景中的光源得到的
      // 结合漫反射光与镜面反射光计算最终光照颜色
      c.a = s.Alpha;
      return c;												                  // 返回最终光照颜色
    }
    void surf(Input IN, inout SurfaceOutput o) {			          // 表面着色器函数
      fixed4 c = tex2D (_MainTex, IN.uv_MainTex) * _Color;			// 根据UV坐标从纹理提取颜色
      o.Albedo = c.rgb;										                      // 设置颜色
      o.Alpha = c.a;											                      // 设置透明度
    }
    ENDCG
  }
  FallBack "Diffuse"
}
```

#### 顶点变换函数

顶点变换函数可以修改顶点着色器中的输入顶点数据以及为表面着色器函数传递顶点数据。

- 使用表面着色器编译指令 `vertex:<Name>`，其中 "Name" 为顶点函数的名称。
- 顶点函数的声明有以下几种形式：
	- `void <Name> (inout appdata_full v)`
		- 其用于只修改顶点着色器中的输入顶点数据。
	- `half4 <Name> (inout appdata_full v, out Input o)`
		- 其用于修改顶点着色器中的输入顶点数据以及为表面着色器函数传递数据。
- 参数解释：
	- `inout` 类型的结构体使用了 **顶点数据结构体**，用于给顶点函数输入顶点数据。
	- `out` 类型的结构体为表面着色器中使用的输入结构体，用于顶点变换函数为表面着色器函数传递数据。

```
Shader "Custom/BaseForm4" {
  Properties {
    _MainTex ("Texture", 2D) = "white" {}							  //2D纹理数值
    _Amount ("Extrusion Amount", Range(0,0.1)) = 0.05		//膨胀系数数值
  }
  SubShader {
    CGPROGRAM
    #pragma surface surf Lambert vertex:vert					  //表面着色器编译指令
    struct Input {												              //Input结构体
      float2 uv_MainTex;											          //uv纹理坐标
    };
    float _Amount;												              //定义膨胀系数属性
    sampler2D _MainTex;										              //定义2D纹理
    void vert (inout appdata_base v) {								  //顶点变换函数
      v.vertex.xyz += v.normal * _Amount;					      //通过法线挤压实现充气的效果
    }
    void surf (Input IN, inout SurfaceOutput o) {				//表面着色器函数
      o.Albedo=tex2D (_MainTex, IN.uv_MainTex).rgb;			//从纹理提取颜色为漫反射颜色赋值
    }
    ENDCG
  }
  Fallback "Diffuse"
}
```

#### 最终颜色修改函数

最终颜色修改函数用于修改表面着色器的最终颜色。

- 使用表面着色器指令 `finalcolor:<Name>`，其中 "Name" 为最终颜色修改函数的名称。
- 最终颜色修改函数的声明形式：
	- `void <Name> (Input IN, SurfaceOutput o, inout fixed4 color)`
- 参数解释：
	- `Input` 结构体用了顶点变换函数为最终颜色修改函数传递数据。
	- `SurfaceOutput` 结构体用于为最终颜色修改函数传输数据。
	- `inout` 参数为最终颜色修改函数输出最终颜色。

```
Shader "Custom/BaseForm5" {
  Properties {
    _MainTex ("Texture", 2D) = "white" {}								//2D纹理数值
    _ColorTint ("Tint", Color) = (1.0, 0.6, 0.6, 1.0)		//调色数值
  }
  SubShader {
    Tags { "RenderType" = "Opaque" }
    CGPROGRAM
    #pragma surface surf Lambert finalcolor:mycolor			//表面着色器编译指令
    struct Input {												              //Input结构体
      float2 uv_MainTex;											          //uv纹理坐标
    };
    fixed4 _ColorTint;											            //调色数值属性
    sampler2D _MainTex;										              // 2D纹理属性
    void mycolor(Input IN, SurfaceOutput o, inout fixed4 color){			//最终颜色修改函数
      color *= _ColorTint;									            //通过调色数值修改最终颜色
    }
    void surf (Input IN, inout SurfaceOutput o) {				//表面着色器函数
      o.Albedo = tex2D (_MainTex, IN.uv_MainTex).rgb;		//从纹理提取颜色为漫反射颜色赋值
    }
    ENDCG
  }
  Fallback "Diffuse"
}
```

## 渲染通道的通用指令

渲染通道可以通过一些通用指令来控制。
在固定管线着色器、顶点片元着色器及表面着色器中都可以使用这些通用指令。

### 设置 LOD 数值

着色器中可以给 SubShader 设置一个 LOD 数值，使程序根据脚本中设置的可以使用的最大 LOD 数值来决定是否使用此 SubShader。
如果 SubShader 中设置的 LOD 值小于或等于脚本中设置的最大 LOD 数制就可以使用此 SubShader。

1. 新建场景，创建一个材质资源，并创建一个 3D 球体，将创建的材质资源拖拽到球体对象上。
2. 创建一个着色器，代码如下。
3. 将创建的着色器拖拽到材质资源中，创建 C# 脚本控制最大 LOD 数值，代码如下。
4. 将创建的脚本拖拽到主摄像机上，然后将着色器拖拽到脚本的 `myShader` 属性栏下。
5. 运行并观察效果。

```
Shader "Custom/LODShader" {
	SubShader {
		LOD 600
		CGPROGRAM
		#pragma surface surf Lambert
		struct Input {
			float2 uv_MainTex;
		};

		void surf (Input IN, inout SurfaceOutput o) {
			o.Albedo = float3(1,0,0);
		}
		ENDCG
	}
	SubShader {
		LOD 500
		CGPROGRAM
		#pragma surface surf Lambert
		struct Input {
			float2 uv_MainTex;
		};

		void surf (Input IN, inout SurfaceOutput o) {
			o.Albedo = float3(0,1,0);
		}
		ENDCG
	}
	SubShader {
		LOD 400
		CGPROGRAM
		#pragma surface surf Lambert
		struct Input {
			float2 uv_MainTex;
		};

		void surf (Input IN, inout SurfaceOutput o) {
			o.Albedo = float3(0,0,1);
		}
		ENDCG
	}
}
```

```csharp
using UnityEngine;
using System.Collections;

public class Test : MonoBehaviour {
    public Shader myShader;
    private float val = 6;
    void Update()
    {
        myShader.maximumLOD = (int)val * 100;
    }
    void OnGUI()
    {
        val = (int)GUI.HorizontalSlider(new Rect(250,125,300,30), val, 3, 6);
        GUI.Label(new Rect(333, 100, 170, 30), "Current LOD is: " + val * 100);
    }
}
```

除了针对某一特定着色器设置最大 LOD 数值（`maximumLOD`）外，也可在脚本中设置一个全局最大 LOD 数值（`Shader.globalMaximumLOD`）。
Unity 内置的着色器都有 LOD 分级，

|LOD 分级|对应值|
|-|-|
|VertexLit kind of shaders|100|
|Decal、Reflective VertexLit|150|
|Diffuse|200|
|Diffuse Detail、Reflective Bumped Unlit、Reflective Bumped VertexLit|250|
|Bumped、Specular|300|
|Bumped Specular|400|
|Parallax|500|
|Parallex Specular|600|

### 渲染队列

渲染队列数值决定了 Unity 在渲染场景物体的先后顺序，在制作特定场景特效时需要用到。
Unity 在渲染物体时，在关闭深度检测的情况下，总是后渲染的物体遮挡住先渲染的物体。

1. 新建场景，创建两个球体对象，设置它们的位置，使其中一个球体稍微遮挡住另一个球体、
2. 创建两个材质资源，分别拖拽到连个球体上。
3. 创建一个着色器，代码如下。
4. 创建另一个着色器，将代码中的 `Geometry+100` 修改为 `Geometry+200`。
5. 分别将两个着色器拖拽到球体对象的材质中，运行并观察效果。
6. 将着色器对调拖拽到球体对象的材质中，运行并观察效果、

```
Shader "Custom/NewSurfaceShader" {
	Properties{
		_Color ("Main Color", Color) = (0, 0, 0, 0)
	}
	SubShader {
		Tags { "Queue" = "Geometry+100" }
		ZTest off
		CGPROGRAM
		#pragma surface surf Lambert
		fixed4 _Color;
		struct Input {
			float2 uv_MainTex;
		};
		void surf (Input IN, inout SurfaceOutput o) {
			o.Albedo = _Color;
		}
		ENDCG
	}
	FallBack "Diffuse"
}
```

Unity 中内置了 5 种默认的渲染队列的值：

- **Background**
	- 背景，对应值为 1000，*这个队列在所有队列之前被渲染*。
	- 通常用于渲染真正需要放在背景上的物体，如天空盒。
- **Geometry（default）**
	- 几何体（默认值），对应值为 2000。
	- 不透明的几何体使用这个队列。
- **AlphaTest**
	- Alpha 测试，对应值为 2450。
	- Alpha 测试的几何结构使用这种队列。
- **Transparent**
	- 透明，对应值为 3000。
	- 采用从后到前的次序，任何采用 Alpha 混合的对象在这里渲染。
- **Overlay**
	- 覆盖，对应值为 4000。
	- 这个渲染队列被用于实现叠加效果。

### 混合模式介绍

混合操作用于在所有的计算已经结束，已经决定将当前计算结果输出到帧缓冲中时，如何输出到帧缓存中。

- 混合操作有两个对象：**源** 和 **目标**。
- 因此也有两个对应的因子：**源因子** 和 **目标因子**。

混合模式常用来绘制 **透明和半透明** 的物体。

混合模式常用指令如下：

- `Blend Off`：关闭混合
- `Blend 源因子, 目标因子`：配置并开启混合。
	- 计算产生的颜色和源因子相乘，然后两个颜色相加。
- `Blend 源因子 目标因子, 源因子A 目标因子A`
	- 源因子和目标因子用于混合颜色值，源因子 A 和目标因子 A 用于混合 Alpha 值。
- `BlendOp 操作命令` ：不是讲加入的颜色混合在一起，而是对它们做其他一些操作。
	- 主要操作命令有 `Min`（取最小值）、`Max`（取最大值）、`Sub`（求差）、`RevSub`（求反差）。

常用的混合因子（对源因子和目标因子都有效）：

|混合因子|说明|
|-|-|
|One|值为 1，用它可使源颜色或目标颜色完全显示出来|
|Zero|值为 0，用它可删除源颜色值或者目标颜色值|
|SrcColor|这个阶段的值乘以源颜色值|
|SrcAlpha|这个阶段的值乘以源 Alpha 值|
|DstColor|这个阶段的值乘以帧缓存源颜色值|
|DstAlpha|这个阶段的值乘以帧缓存源 Alpha 值|
|OneMinusSrcColor|这个阶段的值乘以（1 - 源颜色之间的值）|
|OneMinusSrcAlpha|这个阶段的值乘以（1 - 源颜色 Alpha 之间的值）|
|OneMinusDstColor|这个阶段的值乘以（1 - 目标颜色之间的值）|
|OneMinusDstAlpha|这个阶段的值乘以（1 - 目标颜色 Alpha 之间的值）|

### Alpha 测试

Alpha 测试是阻止片元被写到屏幕的最后机会。
在最终渲染出的颜色被计算出来之后，可通过将颜色的透明度值和一个固定值比较：

- 如果 Alpha 值满足要求，则通过测试，绘制此片元。
- 如果 Alpha 值不满足要求，则丢弃此片元，不进行绘制。

Alpha 测试指令如下：

- `AlphaTest 开关状态`
	- 开关状态为 "Off"（缺省值）时关闭 Alpha 测试并绘制所有拼啊远。
	- 开关状态为 "On" 时开启 Alpha 测试。
- `AlphaTest 比较模式 测试值`
	- 设置 Alpha 测试只渲染透明度值在某一确定范围内的片元。
	- 常用的比较模式如下表：

|Alpha 测试模式|说明|Alpha 测试模式|说明|
|-|-|-|-|
|Greater|大于|GEqual|大于等于|
|Less|小于|LEqual|小于等于|
|Equal|等于|NotEqual|不等于|
|Always|渲染所有片元|Never|不渲染任何片元|

### 深度测试

深度测试是为了使距离摄像机近的物体遮挡住距离摄像机远的物体，确保场景看起来是正确的。
当片元写入到帧缓冲前，需要将待写入的片元的深度值 z 与深度缓冲区对应的深度值进行比较测试，只有测试成功才会写入帧缓冲。

深度测试指令如下：

- `ZWrite 深度写开关`
	- 控制是否将来自对象的片元深度值 z 写入深度缓冲（默认开启）。
	- 如果绘制不透明物体，设置为 "On"。
	- 绘制半透明物体时设为 "Off"。
- `ZTest 深度测试模式`
	- 设置深度测试如何执行。
	- 默认模式是 `LEqual`。
		- 使深度值 z 小于或等于深度缓冲区对应的深度值的片元写于帧缓冲，实现距离摄像机近的物体遮挡住距离摄像机远的物体。
	- 其他深度测试模式见下表。
- `Offset Factor, Units`
	- 允许使用两个参数（因子 Factor 和单元 units）指定深度偏移。
	- 这样可以强制地将一个多边形绘制在另一个多边形上，即使它们实际上处于相同位置。

|深度测试模式|说明|深度测试模式|说明|
|-|-|-|-|
|Less|小于|Greate|大于|
|LEqual|小于等于|GEqual|大于等于|
|Equal|等于|NotEqual|不等于|
|Always|总是渲染|&nbsp;|&nbsp;|

### 通道遮罩

通道遮罩可以让开发人员指定渲染结果的输出通道，而不是通常情况下的 RGBA 这四个通道皆会被写入。

- 可选参数是 RGBA 的任意嘴和以及 0。
- 如果参数为 0，这就意味着不会写入到任何通道，但会做一次深度测试并会写入深度缓冲。

### 面的剔除操作

面的剔除操作是一种通过不渲染背对摄像机的几何体面来提高性能的优化措施。

- 所有的集合体都包含正面和反面。
- 面的剔除操作是基于大多数对象是封闭的事实，因此不需要绘制出背面的剔除操作有几种模式。

|面的剔除操作模式|说明|
|-|-|
|Cull Back|不绘制背向摄像机的面（默认值）|
|Cull Front|不绘制面向摄像机的面|
|Cull Off|关闭面的剔除操作|

### 抓屏操作

`GrabPass` 是一种特殊的通道类型，它会捕获物体所在位置的屏幕的内容并写入到一个纹理中。

> `GrabPass` 开销较大，尽量不适用。

- `GrabPass {}`
	- 能捕获当前屏幕的内容到一个纹理中。
	- 纹理能在后续通道中通过 `_GrabTexture` 进行访问。
- `GrabPass { "TextureName" }`
	- 能捕获屏幕内容到一个纹理中，但只会在每帧中处理第一个使用给定纹理名的纹理的对象的渲染过程中产生捕获操作。
	- 纹理在未来的通道中可以通过给定的纹理名访问。

## 着色器的组织和优化

### 着色器的组织和复用

#### cginc 文件

Unity 含有大量用来引入预定义变量和帮助函数的文件，可由开发人员所编写的着色器程序调用。

- 通过 `#include` 指令进行引入。
- 文件的拓展名为 `.cginc`。

常用的内建文件

|文件名称|说明|
|-|-|
|HLSLSupport.cginc|（自动包含）用于声明多个预处理器宏来协助多平台着色器的开发|
|UnityShaderVariables.cginc|（自动包含）常用的全部变量|
|UnityCG.cginc|常用的帮助函数|
|AutoLight.cginc|光照和阴影功能（表面着色器在内部使用此文件）|
|Lighting.cginc|标准表面着色器光照模型（编写表面着色器时自动包含）|
|TerrainEngine.cginc|用于地形（Terrain）和植被（Vegetation）着色器的帮助函数|

上述内建文件中，`UnityCG.cginc` 文件使用得最为频繁。

***UnityCG.cginc 中的数据结构***

- `appdata_base`
	- 具有位置、法线和一个纹理坐标的顶点着色器输入。

```
struct appdata_base {
	float4 vertex : POSITION;    // 位置变量
	float3 normal : NORMAL;      // 法线变量
	float4 texcoord : TEXCOORD;  // 纹理坐标变量
}
```

- `appdata_tan`
	- 具有位置、切线、法线和一个纹理坐标的顶点着色器输入。

```
struct appdata_tan {
	float4 vertex : POSITION;    // 位置变量
	float4 tangent :TANGENT;     // 切线变量
	float3 normal : NORMAL;      // 法线变量
	float4 texcoord : TEXCOORD;  // 纹理坐标变量
}
```

- `appdata_full`
	- 具有位置、切线、法线、顶点颜色和纹理坐标的顶点着色器输入。

```
struct appdata_full {
	float4 vertex : POSITION;       // 位置变量
	float4 tangent : TANGENT;       // 切线变量
	float3 normal : NORMAL;         // 发现变量
	float4 texcoord : TEXCOORD0;    // 纹理坐标位置
	float4 texcoord1 : TEXCOORD1;
	float4 texcoord2 : TEXCOORD2;
	float4 texcoord3 : TEXCOORD3;
#if definded(SHADER_API_XBOX360)
	half4 texcoord4 : TEXCOORD4;
	half4 texcoord5 : TEXCOORD5;
#endif
	float4 color : COLOR;           // 颜色变量
}
```

- `appdata_img`
	- 具有位置和一个纹理坐标的顶点着色器输入。

```
struct appdata_img {
	float4 vertex : POSITION;   // 位置变量
	half2 texcoord : TEXCOORD;  // 纹理坐标变量
}
```

***UnityCG.cginc 常用的函数***


- `float3 WorldSpaceViewDir(float4 v)`
	- 返回从给定对象空间顶点位置朝向相机的世界坐标空间方向（未规范化）。
- `float3 ObjSpaceViewDir(float4 v)`
	- 返回从给定对象空间顶点位置朝向相机的对象空间方向（未规范化）。
- `float2 ParallexOffset(half b, half height, half3 viewDir)`
	- 计算用于视差法线贴图（normal mapping）的 UV 偏移量。
- `fixed Luminance(fixed3 c)`
	- 将颜色转换为亮度（灰度）
- `fixed3 DecodeLightmap(fixed4 color)`
	- 从 Unity 光照贴图（视平台而定为 RGBM 或 dLDR）解码颜色。
- `float4 EncodeFloatRGBA(float v)`
	- 将 [0, 1) 范围内的浮点数编码为 RGBA 颜色，以存储于低精度渲染目标中。
- `float DecodeFloatRGBA(float4 enc)`
	- 将 RGBA 颜色解码为一个浮点数。
- `float2 EncodeFloatRG(float v)`
	- 使用两个颜色通道将 [0, 1) 范围内的浮点数编码为 RGBA 颜色，以存储于低精度渲染目标中。
- `float DecodeFloatRG(float2 enc)`
	- 使用两个颜色通道将 RGBA 颜色解码为一个浮点数。
- `float2 EncodeViewNormalStereo(float3 n)`
	- 将视图空间法线编码为 [0, 1) 范围内的两个数字。
- `float3 DecodeViewNormalStereo(float4 enc4)`
	- 从 `enc4.xy` 解码视图空间法线。
- `float3 WorldSpaceLightDir(float4 v)`
	- 在给定对象空间顶点位置的情况下，计算到光源的世界坐标空间方向（未规范化）。
- `float3 ObjSpaceLightDir(float4 v)`
	- 在给定对象空间顶点位置的情况下，计算到光源的对象空间方向（未规范化）。
- `float3 Shade4PointLights(...)`
	- 在光照数据被紧密打包进向量中的情况下，计算四个点光灯的照明，正向渲染使用这个函数来计算逐顶点光照。
- `float3 ShadeVertexLights(float4 vertex, float3 normal)`
	- 在给定对象空间位置和法线的情况下，计算四个逐顶点光源和环境光的照明。

> 除了使用 Unity 提供的 cginc 文件，开发人员还可以定义自己的 cginc 文件，然后通过 `#include` 指令来调用。

#### UsePass 复用

```
Shader "Custom/MyPass" {
	...
	SubShader {
		...
		Pass{
			Name "ONE"
			...
		}
		Pass {
			Name "TWO"
			...
		}
	}
}
```

```
Shader "Custom/NewShader" {
	SubShader {
		...
		UsePass "Custom/MyPass/ONE"   // 复用已定义的 Pass
	}
}
```

#### 使用 multi_compile 编译着色器的多个版本

Unity 所提供的 `multi_compile` 选项，是用来让 Unity 能够针对不同的定义条件或者关键字来编译多次。
之后在运行时，通过在脚本中开启或关闭相应的关键字，能够使着色器程序在不同条件下执行不同的代码。

```
Shader "Custom/Multi_Compile"{
	SubShader {
		Pass {
			CGPROGRAM
			#pragma vertex vert
			#pragma fragment frag
			// 告诉 Unity 编译两个不同版本的 Shader
			#pragma multi_compile MY_multi_1 MY_multi_2
			#include "UnityCG.cginc"
			struct verOut {
				float4 pos : SV_POSITION;
			};
			vertOut vert(appdata_base v) {
				vertOut o;
				o.pos = mul(UNITY_MATRIX_MVP, v.vertex);
				return o;
			}
			float4 frag(verOut i) : COLOR {
				float4 c = float4(0, 0, 0, 0);
				#ifdef MY_multi_1
				c = float4(1, 0, 0, 0);
				#endif
				#ifdef MY_multi_2
				c = float4(0, 1, 0, 0);
				#endif
				return c;
			}
			ENDCG
		}
	}
	Fallback "Diffuse"
}
```

```csharp
using UnityEngine;
using System.Collections;
public class Multi_Compile : MonoBehaviour {
	public bool multi_1;
	void Start () {
		if(multi_1){
			Shader.EnableKeyword("MY_multi_1");
			Shader.DisableKeyword("MY_multi_2");
		}
		else{
			Shader.EnableKeyword("MY_multi_2");
			Shader.DisableKeyword("MY_multi_1");
		}
	}
}
```

### 移动平台上的优化

相较于 PC 平台而言，移动平台在各个方面的性能上都相差较大。

- **着色计算的代码优化**
	- 编写着色器程序时常常会进行一些计算，使用代数方法简化计算。
	- 开发时直接利用内置的向量操作函数。
	- 计算的内容较为简单时，不要封装成函数。
- **着色计算的位置优化**
	- 与着色计算相关的任务有三个可能的执行位置：*CPU、顶点着色器、片元着色器*。
	- 每当把计算任务安排到片元着色器中时：
		- 考虑将计算任务安排到顶点着色器，画面质量会不会有影响，是否在可接受范围之内。
		- 如果条件允许，就将计算任务安排到 *顶点着色器*，因为 *顶点着色器的执行频率远低于片元着色器*。
	- 每当把计算任务安排到顶点着色器中时：
		- 判断此计算任务是对于每个顶点单帧计算、结果不同的，还是所有顶点共享一个相同的计算结果。
		- 如果是所有顶点共享，则应该将计算任务交由 *CPU* 执行，然后由主程序将计算结果作为一致变量传入顶点着色器供使用。
- **几何复杂度的考量**
	- 顶点数量可以成为一个影响渲染效率的重要阈值。
	- 在 iOS 平台上，当前视口内的顶点总数最好不要超过 100K 个。
- **纹理图的优化**
	- 贴图的大小要尽量是 2 的幂次方。
		- 所有的计算和存储最终都是要以 2 的幂次方为单位进行的。
	- 把小的纹理组合在一起，做成一张大的纹理。
	- 对于大场景贴图而言，进行纹理采样时要尽量使用 *mipmap*。
	- 任何贴图文件的原始尺寸和类型与最终发布时的尺寸和类型完全无关。
	- 推荐 Android 上使用 ETC 的压缩格式，英伟达的硬件 Tegra，DXT5 更合适，iOS 系列或者其他使用 PowerVR 的设备，最好选择 PVRTC 的贴图压缩格式。
- **使用适当的数据类型**
	- 在移动平台上，`half` 类型的运行效率是 `float` 类型的两倍，`fixed` 类型的运行效率是 `half` 类型的两倍。
	- 避免这 3 种数据类型之间的相互转换。（除了 Adreno 的设备）。
- **变量的使用**
	- 因为大多数 GPU 都会尽量减少从 `vertex` 函数传递到 `fragment` 函数的参数数量，所以通常会把变量包装起来。（PowerVR 除外）
	- 在移动平台上，`tex2D` 是一个消耗性能的操作。
- **慎用透明效果**
	- 透明效果意味着 Unity 引擎要进行排序操作，在 GPU 中逐像素地渲染。
	- 如果必须使用，要尽早进行一些可能会导致后续计算被取消的操作。
	- 可以使用 Blend 混合来实现透明效果。
