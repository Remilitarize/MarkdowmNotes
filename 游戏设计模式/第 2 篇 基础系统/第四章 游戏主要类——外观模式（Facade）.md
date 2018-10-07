[toc]

## 游戏子功能的整合

一款游戏要能顺利运行，必须同时由内部数个不同的子系统一起合作完成。
可能会包含：

- 事件系统
- 角色系统
- 关卡系统
- 成就系统
- ...

这些系统在游戏运行时会彼此使用对方的功能，并且通知相关信息或传送玩家的指令。
另外，有些子系统必须在游戏开始运行前，按照一定的步骤将它们初始化并设置参数，或在游戏在完成一个关卡时，也要按照一定的流程替它们释放资源。

那么，上面这些子系统的沟通及初始化过程都是发生在 **游戏内部** 的。
因为对于外界或客户端来说，大可不必去了解它们之间的相关运行过程。
（就比如使用手机软件，只需要戳戳戳就可以了。）

如果客户端了解太多系统内部的沟通方式及流程，就必须与每一个游戏系统绑定，并且调用每一个游戏系统的功能。
这样的做法对客户端来说不是一件好事。
专业点来讲，让客户端与每个子系统产生依赖性，增加了游戏系统与客户端的 **耦合度**。

```csharp
public class BattleState : ISceneState
{
    // 游戏系统
    private GameEventSystem m_GameEventSystem = null;     // 游戏事件系统
    private StageSystem m_StageSystem = null;             // 关卡系统
    private CharacterSystem m_CharacterSystem = null;     // 角色系统
    private AchievementSystem m_AchievementSystem = null; // 成就系统

    public BattleState(SceneStateController controller) : base(controller)
    {
        // 初始化游戏系统
        InitGameSystem();
    }

    private void InitGameSystem()
    {
        m_GameEventSystem = new GameEventSystem();
        m_StateSystem = new StateSystem();
        m_CharacterSystem = new CharacterSystem();
        m_AchievementSystem = new AchievementSystem();
    }

    // 更新游戏子系统
    private void UpdateGameSystem(){
        m_GameEventSystem.Update();
        m_StateSystem.Update();
        m_CharacterSystem.Update();
        m_AchievementSystem.Update();
    }

}
```

虽然这样的实现方式很简单，但是让战斗状态类（BattleState）这个客户端去负责带哦用所有与游戏玩法相关的系统功能，是不好的实现方式。

- 单一职责原则：`BattleState` 类负责的是游戏在 "战斗状态" 下的功能执行及状态切换，所以不应该负责游戏子系统的初始化、执行操作及相关的整合工作。
- 可重用性：这种设计方式会使得 `BattleState` 类不容易转换给其他项目使用，因为与太多特定子系统产生关联。

## 外观模式（Facade）

定义：**为了系统定义一组统一的接口，这个高级的接口会让子系统更加容易被使用**。

> 通俗化理解就是：我们只需要关注我们自己的操作，而不需要关注内部具体的过程。

![外观模式](http://oxnec2zdn.bkt.clouddn.com/DesignPattern/Facade.PNG)

## 使用外观模式（Facade）实现游戏主程序

![外观模式1](http://oxnec2zdn.bkt.clouddn.com/DesignPattern/Facade1.PNG)

参与者说明：

- GameEventSystem、StageSystem...：分别为游戏的子系统，每个系统负责各自应该实现的功能并提供接口。
- Game：包含了和游戏相关的子系统对象，并提供了界面让客户端使用。
- BattleState：战斗状态类，客户端之一。

具体代码如下；

`Game` 类

```csharp
public class Game
{
    private GameEventSystem m_GameEventSystem = null;     // 游戏事件系统
    private StageSystem m_StageSystem = null;             // 关卡系统
    private CharacterSystem m_CharacterSystem = null;     // 角色系统
    private AchievementSystem m_AchievementSystem = null; // 成就系统

    private bool m_bGameOver;

    public void Initial()
    {
        // 场景状态控制
        m_bGameOver = false;
        m_GameEventSystem = new GameEventSystem(this);
        m_StateSystem = new StateSystem(this);
        m_CharacterSystem = new CharacterSystem(this);
        m_AchievementSystem = new AchievementSystem(this);    
    }

    public void Update()
    {
        m_GameEventSystem.Update();
        m_StateSystem.Update();
        m_CharacterSystem.Update();
        m_AchievementSystem.Update();       
    }

    // 游戏状态
    public bool ThisGameIsOver()
    {
        return m_bGameOver;
    }

    // 当前敌人数量
    public int GetEnemyCount()
    {
        if(m_CharacterSystem != null)
        {
            // 调取角色系统中的 GetEnemyCount 方法
            // 避免客户端直接与角色系统相关联
            return m_CharacterSystem.GetEnemyCount();
        }
    }

    public void Release()
    {
        // 释放相关资源
    }
}
```

`BattleState` 类

```csharp
public class BattleState : ISceneState
{
    // 开始
    public override void StateBegin()
    {
        Game.Instance.Initial();
    }

    public override void StateEnd()
    {
        Game.Instance.Release();
    }

    public override StateUpdate()
    {
        Game.Instance.Update();
        if(Game.Instance.ThisGameIsOver())
        {
            // 如果游戏结束，则返回主菜单界面
            m_controller.SetState(new MainMenuState(m_controller));
        }
    }
}
```

优点：

- 将战斗状态类（BattleState）单一化，让该类只负责游戏在 "战斗状态" 下的功能执行及状态切换。
- 使得战斗状态类（BattleState）减少了不必要的类引用及功能整合，增加了重用性。
- 节省时间：减少系统之间的耦合度，有助于减少系统构建的时间。
- 易于分工开发：只需要了解对方负责系统的 `Facade` 接口类，不必深入了解其中的运行方式。
- 增加系统安全性：系统执行时出错的情况下，使用 `Facade` 接口类可以按照步骤进行整合，直接调用即可，否则客户端将依次执行各个子系统中的错误处理方法，若顺序错误则会导致系统崩溃。

当 `Facade` 接口类过于庞大时：

- 重构 `Facade` 接口类，将功能相近的子系统进行整合，以减少内部系统的依赖性。
- 整合其他设计模式来减少 `Facade` 接口类过度膨胀。

## 外观模式（Facade）面对变化时

任何游戏子系统的修改及更换，都被限制在 `Game` 这个 `Facade` 接口类中。
当有新的系统需要增加时，也只会影响 `Game` 类的定义及增加对外开放的方法，使项目的变动范围减到最小。

## 结论

外观模式（Facade）主要优点就是 *将复杂的子系统沟通交给单一的一个类负责，并提供单一界面给客户端使用，使客户端减少对系统的耦合度*。

> 除此之外，外观模式还可以应用在网络引擎或数据库引擎上。
