[toc]

## Unity 脚本概述

Unity 中的脚本程序需要附加在特定的游戏对象上，脚本中不同的方法在特定的情况下会被 **回调**，实现特定的功能。

- Start 方法
	- 这个方法在游戏场景加载时被调用。
	- 在方法内可以写一些游戏场景初始化之类的代码。
- Update 方法
	- 这个方法会在每一帧渲染之前被调用。
	- 大部分游戏代码在这里执行，除了物理部分的地方。
- FixedUpdate 方法
	- 这个方法会在固定的物理时间步调调用一次。
	- 这里是基本物理行为代码执行的地方。

除了上面几个常用的回调方法，Unity 还提供了其他很多回调方法。
开发人员在有需要的情况下，还可以重写一些处理特定事件的回调方法，这类方法一般以 On 前缀开头。

> 所有的回调方法都是位于 `MonoBehaviour` 类的子类中。

## Unity 中 C# 脚本的注意事项

Unity 中 C# 脚本的运行环境使用了 Mono 技术（Mono 是指由 Novell 公司领导的，一个致力于 .NET 开源的工程），可以在 Unity 脚本中使用 .NET 所有的相关类。
但 Unity 中 C# 的使用和传统的 C# 有一些不同。

### 继承自 `MonoBehaviour` 类

Unity 中所有挂载到游戏对象上的脚本中的类必须继承 `MonoBehaviour` 类（直接的或间接的）。

```csharp
public class NewBehaviourScript : MonoBehaviour {...;}
```

### 类名必须匹配文件名

C# 脚本中类名需要手动编写，而且类名必须和文件名相同。
否则当前脚本挂载到游戏对象时，在控制台会报错。

### 使用 `Awake` 或 `Start` 方法初始化

用于初始化脚本的代码必须置于 `Awake` 或 `Start` 方法中。

- `Awake` 方法是在加载场景时运行。
- `Start` 方法是在第一次调用 `Update` 或 `FixedUpdate` 方法之前被调用。
- `Awake` 方法总是运行在所有 `Start` 方法之前。

### Unity 脚本中协同程序有不同的语法规则

Unity 脚本中协同程序（Coroutines）必须是 `IEnumerator` 返回类型。
`yield` 被 `yield return` 替代。

### 只有满足特定情况变量才能显示在属性查看器中

只有序列化的成员变量才能显示在属性查看器中。
`private` 和 `protected` 类型的成员变量只能在专家模式中显示，其属性不被序列化或显示在属性查看器中。
如果属性想在属性查看器中显示，其必须是 `public` 类型的。

### 尽量避免使用构造函数

不要在构造函数中初始化任何变量，要用 `Awake` 或 `Start` 方法来实现。
因为 Unity 会自动调用构造函数，无法预计何时会调用构造函数。

### 调试

Unity 自带了完善的调试功能，在 Unity 的控制台（Console）中包含了当前的全部错误，每一个错误信息都明确指明了代码出错的位置和原因。
若这个错误是脚本错误，当双击这个错误时，可以自动跳转到默认的脚本编辑器中。

在 Unity 中，可以使用 `print()` 和 `Debug.Log()` 打印调试信息。
但是 `print()` 只能在 Mono 的类中使用，所以一般情况下最好使用 `Debug.Log()`。
同时可以使用 `Debug.LogWarning()` 和 `Debug.LogError()` 收集警告和错误信息。
Unity 通过 `Debug.Break()` 设置断点。

## Unity 脚本的基本语法

### 常用操作

Unity 中很多对游戏对象的操作都是通过在脚本中修改对象的 Transform（变换属性） 和 Rigidbody（刚体属性） 参数来实现的。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	void Update () {
		// 让物体绕 x 轴顺时针旋转 20°
		this.transform.Rotate (20, 0, 0);
	}
}
```

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	void Update () {
		// 物体每帧向前移动 1 个单位长度
		this.transform.Translate (0, 0, 1);
	}
}
```

> 一般情况下，x 轴为红色轴表示左右，y 轴为绿色轴表示上下，z 轴为蓝色轴表示前后。

用于旋转的 `Rotate` 方法和用于移动的 `Translate` 方法都有 4 个参数的重载形式。
第四个参数为 `Space` 枚举类型。

- 如果设置为 `Space.Self`，变换被应用相对于自身轴。
- 如果设置为 `Space.World`，变换被用用相对于世界坐标系统。
- 如果不设置第四个参数，则默认设置为 `Space.Self`。

### 记录时间

在 Unity 中记录时间需要使用到 `Time` 类。
其中比较重要的变量为 `deltaTime`（只读），它指的是从最近一次调用 `Update` 方法到现在的时间。

由于系统在绘制每一帧时，都会回调一次 `Update` 方法，所有如果想实现以秒为时间间隔的效果，需要乘上 `deltaTime`。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	void Update () {
		// 绕 x 轴每秒旋转 10°
		this.transform.Rotate (10 * Time.deltaTime, 0, 0);
	}
}
```

### 访问游戏对象组件

常用的组件可以通过简单的成员变量获得。

|组件名称|变量名称|组件名称|变量名称|
|-|-|-|-|
|Transform|transform|Rigidbody|rigidbody|
|Renderer|renderer|Camera|camera（只有摄像机对象有效）|
|Light|light（只在光源对象有效）|Animation|animation|
|Collider|collider|&nbsp;|&nbsp;|

> 这里的组件体现在属性查看器上，而变量是体现在脚本中。

如果游戏对象中没有想要获取的值，那么对应的变量将为 `null`。

在 Unity 中，附加在游戏对象上的组件可以通过 `GetComponent` 方法获得。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	void Update () {
		// 下面两个方法是等价的
		transform.Translate (1, 0, 0);
		GetComponent<Transform> ().Translate (1, 0, 0);
	}
}
```

也可以通过 `GetComponent` 方法获取其他的脚本。

Hello.cs

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Hello : MonoBehaviour {
	void sayHello(){}
}
```

Test.cs

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	void Update () {
		Hello hello = GetComponent<Hello> ();
		hello.sayHello ();
	}
}
```

### 访问其他游戏对象

#### 通过属性查看器指定参数

代码中声明 `public` 类型的游戏对象引用，在属性查看器中就会显示这个游戏对象参数，然后就可以将需要获取的游戏对象拖拽到属性查看器的相关参数位置。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	public GameObject otherObject;

	void Update () {
		otherObject.transform.Rotate (10 * Time.deltaTime, 0, 0);
	}
}
```

#### 确定游戏对象的层次关系

游戏对象在游戏组成对象列表中存在父子关系，在代码中就可以通过获取 `Transform` 组件来找到子对象或者父对象。
一旦成功获取到子对象或父对象，就可以通过 `GetComponent` 方法获取其其他组件。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	void Update () {
		// 获取子对象
		transform.Find ("Cube1").Translate (1 * Time.deltaTime, 0, 0);
		transform.Find ("Cube1").GetComponent<Transform> ()
			.Translate (1 * Time.deltaTime, 0, 0);
		// 获取父对象
		transform.parent.Translate (1 * Time.deltaTime, 0, 0);
	}
}
```

也可以使用循环获取到所有子对象。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	void Update () {
		foreach (Transform child in transform) {
			child.Translate (0, 5, 0);
		}
	}
}
```

#### 通过名字或标签获取游戏对象

Unity 脚本中可以使用 `FindWithTag` 方法和 `Find` 方法来获取游戏对象。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	private GameObject name;
	private GameObject tag;

	void Start(){
		tag = GameObject.FindWithTag ("Player");
		name = GameObject.Find ("Cube1");
	}

	void Update () {
		tag.transform.Translate (1 * Time.deltaTime, 0, 0);
		name.transform.Rotate (10 * Time.deltaTime, 0, 0);
	}
}
```

#### 通过传递参数来获取游戏对象

一些事件回调方法的参数中包含了特殊的游戏对象或组件信息。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	void OnTriggerStay(Collider other){
		if(other.GetComponent<Rigidbody>()){
			other.GetComponent<Rigidbody> ().AddForce (0, 0, 2);
		}
	}
}
```

#### 通过组件名称获取游戏对象

Unity 脚本中可以通过 `FindObjectsOfType` 方法和 `FindObjectOfType` 方法来找到挂载特定类型组件的游戏对象。

- `FindObjectsOfType` 方法可以获取所有挂载指定类型组件的游戏对象。
- `FindObjectOfType` 方法获取挂载指定类型组件的第一个游戏对象。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	void Start () {
		Transform tran = FindObjectOfType<Transform> ();
		Debug.LogWarning (tran.gameObject.name);

		Transform[] trans = FindObjectsOfType<Transform> ();
		foreach (Transform tr in trans) {
			Debug.LogError (tr.gameObject.name);
		}
	}
}
```

### 向量

Unity 中提供了完整的向量以及向量操纵方法，分别为表示二维向量的 `Vector2` 类和表示三维向量的 `Vector3` 类。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	public Vector3 position1 = new Vector3 ();
	public Vector3 position2 = new Vector3 (1, 2, 2);

	void Start () {
		position1.x = 1;
		position1.y = 1;
		position1.z = 1;
	}
}
```

`Vector3` 类中也定义了一些常量。

|常量|值|常量|值|
|-|-|-|-|
|`Vector3.zero`|(0, 0, 0)|`Vector3.one`|(1, 1, 1)|
|`Vector3.forward`|(0, 0, 1)|`Vector3.up`|(0, 1, 0)|
|`Vector3.right`|(1, 0, 0)|&nbsp;|&nbsp;|

`Vector3` 类中有很多对向量进行操纵的方法。

|方法|作用|
|-|-|
|`Lerp`|两个向量之间的线性插值。|
|`Slerp`|在两个向量之间进行球形插值。|
|`OrthoNormalize`|使向量规范化并且彼此相互垂直。|
|`MoveTowards`|从当前的位置移向目标。|
|`RotateTowards`|当前的向量转向目标。|
|`SmoothDamp`|随着时间的推移，逐渐改变一个向量朝向预期的目标。|
|`Scale`|两个矢量组件对应相乘。|
|`Cross`|两个向量的交叉相乘。|
|`Reflect`|沿着法线反射向量。|
|`Dot`|两个向量的点乘积。|
|`Project`|投影一个向量到另一个向量。|
|`Angle`|返回两个向量的夹角。|
|`Distance`|返回两点之间的距离。|
|`ClampMagnitude`|返回向量的长度，最大不超过 maxLength 所指示的长度。|
|`Min`|返回两个向量中长度较小的向量。|
|`Max`|返回两个向量中长度较大的向量。|
|`operator +`|两个向量相加。|
|`operator -`|两个向量相减。|
|`operator *`|两个向量相乘。|
|`operator /`|两个向量相除。|
|`operator ==`|两个向量是否相等。|
|`operator !=`|两个向量是否不想等。|

### 成员变量和静态成员变量

一般情况下，定义在方法体外的变量是成员变量。

- 如果这个变量是 `public` 类型的，就可以在属性查看器看到。
- 如果在属性查看器对它的值进行修改，它的值就会随着项目一起自动保存。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	public Transform ren;

	void Update () {
		if(Vector3.Distance (ren.position, transform.position) < 10){
			Debug.Log (ren.position);
		}
	}
}
```

- 可以通过 `private` 关键字创建私有变量，此时在属性查看器中就不会显示该变量。
- 可以通过 `static` 关键字来创建全局变量，这样就可以在不同脚本间调用这个变量。

### 实例化游戏对象

Unity 中如果想创建游戏对象，可以通过创建游戏对象菜单在场景中创建游戏对象，也可以在脚本中动态地创建游戏对象。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {

	public GameObject otherObject;

	void OnCollisionEnter(){
		Destroy(gameOjbect, 1);   // 撞击发生 1s 后销毁对象
		GameObject theNewObject = Instantiate(otherObject, transform.position, transform.rotation) as GameObject;
	}
}
```

> `Destroy(gameObject, n)` 方法是在 ns 后销毁物体，`DestroyImmediate(gameObject, boolean)` 当参数的布尔值为 `true` 时就会立即销毁。

### 协同程序和中断

协同程序，即在主程序运行时同时开启另一段逻辑处理，来协同当前程序的执行。
与线程程序不同，所有的协同程序都是在主线程中运行的，还是一个单线程程序。
通过 `StartCoroutine` 方法来开启一个协同程序。

- `StartCoroutine` 方法为 `MonoBehaviour` 类中的一个方法，即必须在继承于 `MonoBehaviour` 的类中调用。
- `StartCoroutine` 方法可以使用返回值作为 `IEnumrator` 类型方法的参数。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {
	void Start(){
		StartCoroutine(doThing());
	}

	IEnumrator doThing(){
		Debug.Log("dothing");
		yield return null;
	}
}
```

可以使用 `yield` 关键字来中断协同程序，也可以使用 `WaitForSeconds` 类的实例化对象让协同程序休眠。

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour {
	void Start(){
		StartCoroutine(doThing());
	}

	IEnumrator doThing(){
		// 协同程序休眠 2 秒
		yield return new WaitForSeconds(2);
		Debug.Log("dothing");
	}
}
```

### 一些重要的类

#### MonoBehaviour 类

MonoBehaviour 类中常用的可重写的方法

|方法|说明|
|-|-|
|Update|当脚本启用后，该方法在每一帧被调用。|
|FixedUpdate|当脚本启用后，该方法会在固定的屋里时间步调调用一次。|
|Awake|当一个脚本实例被载入时该方法被调用。|
|Start|该方法仅在 Update 方法第一次被调用前调用。|
|OnEnable|当对象变为可用或激活状态时该方法被调用。|
|OnDisable|当对象变为不可用或非激活状态时该方法被调用。|
|OnDestroy|当对象被销毁时该方法被调用。|
|OnGUI|渲染和处理 GUI 事件时调用。|
|LateUpdate|该方法在 Update 方法之后调用。|

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Test : MonoBehaviour{

	// 每当脚本被加载时调用
	// public 成员变量在这里初始化
	void Awake(){
		print("Awake");
	}

	// 在每次激活脚本时调用
	// 重置
	void OnEnable(){
		print("OnEnable");
	}

	// 第一次调用 Update 之前调用
	// private 成员变量在这里初始化
	void Start(){
		print("Start");
	}

	// 每帧调用一次 Update
	// 主循环每循环一次就是一帧
	// 接近每秒 60 帧
	// 画面逻辑
	void Update(){
		print("Update");
	}

	// Update 之后调用
	// 其余逻辑
	void LateUpdate(){
		print("LateUpdate");
	}

	// 取消激活后调用
	void OnDisable(){
		print("OnDisable");
	}

	// 脚本被销毁时调用
	void OnDestroy(){
		print("OnDestroy");
	}

	// 激活时持续调用
	void OnGUI(){
		print("OnGUI")；
	}

	// 激活时持续调用
	// 以固定频率调用
	// 不会受到图像刷新速率的影响
	// 处理物理逻辑
	void FixedUpdate(){
		print("FixedUpdate");
	}
}
```

MonoBehaviour 类中常用的可继承的成员变量

|成员变量|说明|
|-|-|
|enabled|启用行为被更新，禁用行为不更新。|
|transform|附加到游戏物体的 Transform 组件。|
|rigidbody|附加到游戏物体的 Rigidbody 组件。|
|camera|附加到游戏物体的 Camera 组件。|
|light|附加到游戏物体的 Light 组件。|
|animation|附加到游戏物体的 Animation 组件。|
|constantForce|附加到游戏物体的 ConstantForce 组件。|
|renderer|附加到游戏物体的 Renderer 组件。|
|audioSource|附加到游戏物体的 AudioSource 组件。|
|guiText|附加到游戏物体的 GUIText 组件。|
|collider|附加到游戏物体的 Collider 组件。|
|particleEmitter|附加到游戏物体的 ParticleEmitter 组件。|
|gameObject|组件附加的游戏物体。|
|tag|游戏物体的标签。|

MonoBehaviour 类中常用的课继承的成员方法

|成员方法|说明|
|GetComponent|返回游戏物体上指定名称的组件。|
|GetComponentChildren|返回游戏对象及其子对象上指定类型的第一个找到的组件。|
|GetComponents|返回游戏物体上指定名称的全部组件。|
|SendMessage|在游戏物体每一个脚本上调用指定名称的方法。|
|Instantiate|实例化游戏对象。|
|Destroy|删除一个游戏物体、组件或资源。|
|DestroyImmediate|立即销毁物体。|
|FindObjectOfType|返回指定类型第一个激活的加载的物体。|
|FindObjectsOfType|返回指定类型所有激活的加载的物体列表。|

#### Transform 类

Transform 类中常用的成员变量

|成员变量|说明|
|-|-|
|position|在世界空间坐标中游戏对象的位置。|
|localPosition|相对于父级的变换的位置。|
|eulerAngles|物体旋转的欧拉角。|
|localEulerAngles|相对于父级旋转的欧拉角。|
|right|在世界空间坐标变换的红色轴，即 x 轴。|
|up|在世界空间坐标变换的绿色轴，即 y 轴。|
|forward|在世界空间坐标变换的蓝色轴，即 z 轴。|
|rotation|在世界空间坐标物体变换的旋转角度。|
|localRotation|物体变换的旋转角度相对于父级的物体变换的旋转角度。|
|localScale|相对于父级物体变换的缩放。|
|parent|物体变换的父级。|
|worldToLocalMatrix|从世界坐标转为自身坐标的矩阵变换。（只读）|
|localToWorldMatrix|从自身坐标转为世界坐标的矩阵变换。（只读）|
|childCount|变换的子物体数量。|
|lossyScale|物体的全局缩放。（只读）|

Transform 类中常用的成员方法

|成员方法|说明|
|-|-|
|Translate|移动游戏对象的方向和距离。|
|Rotate|应用一个欧拉角的旋转角度。|
|RotateAround|按照指定角度通过在世界坐标轴旋转物体。|
|LookAt|旋转物体，指向目标的当前位置。|
|TransformDirection|变换方向从自身坐标到世界坐标。|
|InverseTransformDirection|变换方向从世界坐标到自身坐标。|
|TransformPoint|变换位置从自身坐标到世界坐标。|
|InverseTransformPoint|变换位置从世界坐标到自身坐标。|
|DetachChildren|所有子物体解除父子关系。|
|IsChildOf|这个变换是否是父级的子物体。|

#### Rigidbody 类

`Rigidbody` 组件可以模拟物体在物理效果下的状态，可以让物体接受力和扭矩，让物体相对真实地移动。

Rigidbody 类中常用的成员变量

|成员变量|说明|
|-|-|
|velocity|刚体的速度向量。|
|angularVelocity|刚体的角速度向量。|
|drag|物体的阻力。|
|angularDrag|物体的角阻力。|
|mass|刚体的质量。|
|useGravity|控制重力是否影响整个刚体。|
|isKinematic|控制物理是否影响这个刚体。|
|freezeRotation|控制物理是否改变物体的旋转。|
|collisionDetectionMode|刚体的碰撞检测模式。|
|centerOfMass|相对于变换原点的重心。|
|worldCenterOfMass|在世界坐标空间的刚体的中心。（只读）|
|inertiaTensorRotation|惯性张量的旋转。|
|inertiaTensor|相对于中心的质量的惯性张量对角线。|
|detectCollisions|碰撞检测是否启用。（默认总是启用的）|
|useConeFriction|用于该刚体的锥形摩擦力。|
|position|该刚体的位置。|
|rotation|该刚体的旋转。|
|interpolation|插值允许你以固定的帧率平滑物理运动效果。|
|solverIterationCount|允许覆盖每个刚体的求解迭代次数。|
|sleepVelocity|线性速度，低于该值的物体将开始休眠。|
|sleepAngularVelocity|角速度，低于该值的物体将开始休眠。|
|maxAngularVelocity|刚体的最大角速度。|

Rigidbody 类中常用的成员方法

|成员方法|说明|
|-|-|
|SetDensity|基于附加的碰撞器假设一个固定的密度设置质量。|
|AddForce|施加一个力到刚体。|
|AddRelativeForce|施加一个力到刚体，相对于自身的系统坐标。|
|AddTorque|施加一个力矩到刚体。|
|AddRelativeTorque|施加一个力矩到刚体，相对于自身的系统坐标。|
|AddForceAtPosition|在指定位置施加一个力。|
|AddExplosionForce|施加一个力到刚体来模拟爆炸效果。爆炸力将随着到刚体的距离线性衰减。|
|ClosestPointOnBounds|到附加的碰撞器包围盒上的最近点。|
|GetRelativePointVelocity|相对于刚体在指定点的速度。|
|GetPointVelocity|刚体在世界坐标空间中指定点的速度。|
|MovePosition|移动刚体到指定位置。|
|MoveRotation|旋转刚体到指定位置。|
|Sleep|强制一个刚体休眠至少一帧。|
|IsSleeping|判断刚体是否在休眠。|
|WakeUp|强制唤醒在休眠状态中的刚体。|

#### CharacterController 类

角色控制器是 `CharacterController` 类的实例化对象，用于第三人称或第一人称游戏角色控制。
可以根据碰撞检测判断是否能够移动，而不必添加刚体和碰撞起。
而且角色控制器不会受到力的影响。

CharacterController 类中常用的成员变量

|成员变量|说明|
|-|-|
|isGrounded|角色控制器是否触碰地面。|
|velocity|角色控制器当前的相对速度。|
|collisionFlags|在最近一次角色控制器移动方法调用时，角色控制器的哪个部分与周围环境相碰撞。|
|radius|角色控制器的半径。|
|height|角色控制器的高度。|
|center|角色控制器的中心位置。|
|slopeLimit|角色控制器的坡度度数限制。|
|stepOffset|角色控制器的台阶偏移量（台阶高度）。|
|detectCollisions|其他的刚体和角色控制器是否能够与本角色控制器相碰撞。|

CharacterController 类中常用的成员方法

|成员方法|说明|
|-|-|
|SimpleMove|以一定的速度移动角色。|
|Move|一个更加复杂的移动函数，每次都绝对移动。|

### 性能优化

#### 缓存组件查询

当通过 `GetComponent` 获取一个组件时，Unity 必须从游戏物体里查找目标组件。
如果是在 Update 方法中进行查找，就会影响运行速度。
可以设置一个私有变量去存储这个组件。

```csharp
public class Test : MonoBehaviour{
	private Transform m_transform;

	void Start(){
		m_transform = this.transform;
	}

	void Update(){
		m_transform.Translate(new Vector3(0,0,1));
	}
}
```

#### 使用内建数组

虽然 `ArrayList` 和 `Array` 使用起来容易并且方便，但是相比较内建数组而言，前者和后者的速度还是有很大的差别。
内建数组直接潜入 struct 数据类型存入第一缓冲区里，不需要其他类型信息或其他资源，因此更加快捷。

```csharp
public class Test : MonoBehaviour{
	private Vector3[] positions;

	void Start(){
		positions = new Vector3[100];
		for(int i = 0; i < positions.Length; i++){
			positions[i] = Vector3.zero;
		}
	}
}
```

#### 尽量少调用函数

Unity 中 Update 函数每一帧都在运行，所以减少 Update 方法里面的工作量，可以大幅度提高运行速率。
可以通过协调程序或者加入标志位就能实现。

### 脚本编译

根据官方的解释，脚本的具体编译需要以下 4 步：

1. 所以在 Standard Assets、Pro Standard Assets 和 Plugins 中的脚本将被首先编译。
	- 在这些文件夹之内的脚本不能直接访问这些文件夹以外的脚本。
	- 不能直接引用类或它的变量。
	- 可以用 `GameObject.SendMessage` 与它们通信。
2. 所有在 Standard Assets/Editor、Pro Standard Assets/Editor 和 Plugins/Editor 中的脚本接着被编译。
	- 如果想要使用 `UnityEditor` 命名空间，必须将脚本放置到这些文件夹中。
3. 然后所有在 Assets/Editor 外的，并且不在上面文件夹中的脚本文件被编译。
4. 所有在 Assets/Editor 中的脚本，最后被编译。
