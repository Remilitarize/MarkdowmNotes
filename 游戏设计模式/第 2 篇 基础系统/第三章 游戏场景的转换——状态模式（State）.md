[toc]

## 游戏场景

### 场景的转换

- 登陆场景：负责游戏片头、加载游戏数据、出现游戏主画面、等待玩家登陆游戏。
- 主画面场景：负责进入游戏画面、玩家在主城 / 主画面中的操作、在地图上打怪打宝……
- 战斗场景：负责与玩家组队之后进入副本关卡、挑战王怪……

- 切分场景的好处
	- 将游戏功能执行时需要的环境明确分类
	- “重复使用”

### 游戏场景可能的实现方式

```csharp
public class SceneManager
{
	private string m_state = "开始";
	// 改换场景
	public void ChangeScene(string StateName)
	{
		m_state = StateName;

		switch(m_state)
		{
			case "菜单":
				Application.LoadLevel("MainMenuScene");
				break;
			case "主场景":
				Application.LoadLevel("GameScene");
				break;
		}
	}

	// 更新
	public void Update(){
		switch(m_state)
		{
			case "开始":
				// ...
				break;
			case "菜单":
				// ...
				break;
			case "主场景":
				// ...
				break;
		}
	}
}
```

- 缺点
	- 只要**增加一个状态**，则所有 **`switch(m_state)`** 的程序代码都需要增加对应的程序代码。
	- 与每一个状态有关的对象，都**必须在 `SceneManager` 类中被保留**，当作这些对象被多个状态共享时，可能会产生混淆，不太容易识别是哪个状态设置的，造成游戏程序调试上的困难。
	- 每一个状态可能使用不同的类对象，容易造成 `SceneManager` 类 **过度依赖** 其他类，让 `SceneManager` 类不容易移植到其他项目上。

- 期望一个 "场景类" 的功能
	- 场景初始化
	- 场景结束后，负责清除资源
	- 定时更新游戏逻辑单元
	- 转换到其他场景
	- 其他与该场景有关的游戏实现

## 状态模式（State）

### 状态模式的定义

GoF 的解释：让一个对象的行为 **随着内部状态的改变而变化**，而该对象也像是换了类一样。

当某个对象状态改变是，虽然它 "表现的行为" 会有所变化，但是对于客户端来说，并不会因为这样的变化，而改变对他的 "操作方法" 或 "信息沟通" 的方式。

### 状态模式的说明

该例子是一个角色的状态变化。

- Context（状态拥有着）
	- 具有 "状态" 属性的类，让外界能够得知状态的改变或通过操作让状态改变。
- State（状态接口类）
	- 制定状态的 **接口**。
- ConcreteState（具体状态类）
	- 继承自 State
	- 实现 Context 在特定状态下该有的行为。

![状态模式](http://oxnec2zdn.bkt.clouddn.com/DesignPattern/State.PNG)

### 状态模式的实现范例

- Context 类

```csharp
public class Context
{
	State m_state;
	public void Request(int Value){
		m_state.Handle(Value);
	}
	public void SetState(State theState){
		Debug.log("Context.SetState:" + theState);
		m_state = theState;
	}
}
```

- State 类

```csharp
public abstract class State
{
	protected Context m_context = null;  
	// 因为需要在具体类中修改，所以将 Context 对象作为属性存储进来
	public State(Context theContext){
		m_context = theContext;
	}
	public abstract void Handle(int Value);
}
```

- 定义 3 个状态

```csharp
public class ConcreteStateA : State
{
	public ConcreteStateA(Context theContext) : base(theContext) {}
	public override void Handle(int Value){
		Debug.log("ConcreteStateA.Handle");
		if(Value > 10){
			m_context.SetState(new ConcreteStateB(m_context));
		}
	}
}

public class ConcreteStateB : State
{
	public ConcreteStateB(Context theContext) : base(theContext) {}
	public override void Handle(int Value){
		Debug.log("ConcreteStateB.Handle");
		if(Value > 20){
			m_context.SetState(new ConcreteStateC(m_context));
		}
	}
}

public class ConcreteStateC : State
{
	public ConcreteStateC(Context theContext) : base(theContext) {}
	public override void Handle(int Value){
		Debug.log("ConcreteStateC.Handle");
		if(Value > 30){
			m_context.SetState(new ConcreteStateA(m_context));
		}
	}
}
```

状态的转换可以有下列两种方式：

- 交由 Context 类本身，按条件在各状态之间转换。
- 产生 Context 类对象时，马上指定 **初始状态** 给 Context 对象，而在后续执行过程中的状态转换则交由 State 对象负责，Context 对象不再介入。

测试代码：

```csharp
Context theContext = new Context();
theContext.SetState(new ConcreteState1(theContext));  // 初始状态为 ConcreteState1

theContext.Request(5);  // 当值为 5 时请求改变状态
theContext.Request(15);
theContext.Request(25);
theContext.Request(35);
```

> 会发现当值增大时，状态也会随之改变。但是对于跳过某个状态仍需要继续完善。

## 状态模式（State）面对变化时

- 加入一个新的状态状态类对应到新的状态，并在其中实现相关的功能。
- 决定要从哪个现有状态转换到新的状态。
- 决定新的状态结束后要转换到哪个状态。

就程序代码的修改而言，只会新增一个程序文件（.cs）实现，并修改一个现有的游戏状态即可。
除此之外，不需要修改其他任何的程序代码。

## 结论

利用状态模式（State）实现了状态的切换，虽然并非全是优点，但比起传统的 `switch(state_code)` 相比，已经算是更好的设计。

优点：

- 可以清楚了解某个场景状态执行时所需要配合使用的类对象。
- 减少因新增状态而需要大量修改现有程序代码的维护成本。

缺点：

- 当状态类过多时，会伴随着 *类爆炸* 的问题。

> 状态模式除了可以进行角色状态的切换，还可以实现场景、关卡等其他状态的切换。
