[toc]

## 开始在 Visual Studiio 2015 环境中编程

### 创建一个控制台应用程序

1. 打开 Visual Studio 2015。
2. 在 "文件" 菜单中选择 "新建" | "项目"。
3. 在左侧窗格中 "已安装" 节点，展开 "模板"，单击 "Visual C#"。在中间窗格，验证顶部组合框显示的是 ".NET Framework 4.6"，单击 "控制台应用程序"。
4. 在 "位置" 文本框中输入 **工作目录**。
5. 在 "名称" 文本框中输入 **程序名**（默认为ConsoleApplication1）。
6. 确定以勾选 "为解决方案创建目录" 复选框，单击 "确定" 按钮。

### 解决方案资源管理器

"解决方案资源管理器" 显示了项目相关文件的名称以及其他内容。
双击文件名即可在 "代码和文本编辑器" 中显示该文件的内容。

> 这里用默认的 ConsoleApplication1 进行解释。

- 解决方案 "ConsoleApplication1"
	- 位于最顶级，每个应用程序都包含 **单个解决方案文件**。
	- 解决方案可包含 **一个或多个项目**，Visual Studio 2015 利用该解决方案文件对项目进行组织。
	- 文件目录在 **工作目录的 ConsoleAppliaction1** 下，文件名为 **程序名.sln**（ConsoleApplication1.sln)。
- ConsoleApplication1
	- C# 项目文件，每个项目文件都引用一个或多个包含项目 **源代码** 以及其他内容（比如图片）的文件。
	- 一个项目的所有源代码都必须使用相同的编程语言。
	- 实际名称为 **ConsoleApplication1.csproj**，保存在 **工作目录的 ConsoleApplication1\ConsoleApplication1 子文件下**。
- Properties
	- 项目中的一个文件夹，展开会发现 AssemblyInfo.cs 文件。
	- AssemblyInfo.cs 是用于为程序添加 "特性"（Attribute） 的特殊文件。
	- 具体如何使用这些特性已超出范围。
- 引用
	- 包含对已编译好的代码库的引用。
	- C# 代码编译时会转换成 **库**，并获得 **唯一名称**。Microsoft .NET Framework 将这种库称为 **程序集**。
- App.config
	- 应用程序配置文件。
- Program.cs
	- **C# 源代码文件**。

## 写第一个程序

初始代码：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
}
```

Program.cs 文件定义了 Program 类，其中包含 **Main 方法**，所有可执行代码都必须在 Main 方法中定义。

> 方法必须从属于类或结构。

- **Main 方法指定程序入口**，且必须定义成 **静态方法**。
- 否则应用程序运行时，.NET Framework 可能不把它视为起点（入口）。

> 利用 "智能感知" 写代码可以提高速率，这里不做详解。

### 注释

注释可以填写一些方便开发人员理解的文字信息，但会被 **编译器忽略**。

- 行内注释：`//`
- 行间注释：

```csharp
/*
*
*/
```

### 执行程序

在 Main 方法中添加一行代码：

```csharp
Console.WriteLine("Hello World!");
```

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
						Console.WriteLine("Hello World!");
        }
    }
}
```

1. 在 "生成" 菜单中，选择 **"生成解决方案"**。
	- 这样会编译 C# 代码并声称可运行的程序。
	- 在 "代码和文本编辑器" 下方会显示 "输出" 窗口。
	- 如果 "输出" 窗口没有出现，请在 "视图" 菜单中选择 "输出"。
2. 如果有错误，则会显示在 "错误列表" 窗口中。
	- 双击错误，光标会移动到导致错误的代码行。
	- 当输入一行不能编译的代码时，Visual Studio 会在其下方显示一条 **红色波浪线**。
3. 在 "调试" 菜单中，选择 **"开始执行（不调试）"**。
4. 在 "解决方案资源管理器" 中单击项目，然后单击 "解决方案资源管理器" 工具栏中的 "显示所有文件" 按钮。
	- 在 Program.cs 文件上方会显示 bin 和 obj，这两项直接对应于项目文件夹中的 bin 和 obj 文件夹，包含应用程序的可执行版本，以及用于生成和调试应用程序的其他文件。
5. 展开 bin 文件，再展开其中的 Debug 文件夹，随后看到编译好的程序 `.exe`。

## 使用命名空间

命名空间用于解决当引用了多个开发人员的程序集时使用了大量相同名称的问题。

```csharp
namespace TestHello{
// 使用 namespace 关键字在 TestHello 命名空间中创建 Greeting 类
	class Greeting{
		// ...;
	}
}

namespace NewNameSpace{
// 使用 namespace 关键字在 NewNameSpace 命名空间中创建 Greeting 类
	class Greeting{
		// ...;
	}
}
```

TestHello 命名空间中的 Greeting 类可以用 `TestHello.Greeting` 引用。
NewNameSpace 命名空间中的 Greeting 类可以用 `NewNameSpace.Greeting` 引用。

> Visual Studio 2015 环境默认使用 **项目名称** 作为顶级命名空间。

使用 `using` 指令可以将某个命名空间引入作用域（即当前源代码中）。
当注释掉（或删除）程序上方的 `using System;` 时，`Console.WriteLine();` 这一行会报错。

> 注意到文件顶部会有几个 using 指令，这些命名空间包含的类很常用。

## 创建图形应用程序

Visual Studio 2015 允许用两个视图查看图形应用程序：**设计视图** 和 **代码视图**。
可在"代码和文本编辑器"窗口中修改和维护图形应用程序的代码和逻辑。
"设计视图"窗口则用与不知图形用户界面。

### 在 Visual Studio 2015 中创建图形应用程序

1. 选择 "文件"|"新建"|"项目"。
2. 在左侧窗格展开 "已安装"|"模板"|"Visual C#"|"Windows"|"通用"。
 	- 如果没有安装，就选择 "UAF"，并在中间窗格选择 "安装通用 Windows 工具"。
3. 在中间窗格单击 "空白应用（通用 Windows）" 图标。
4. 确定 "位置" 文本框内填写的是你的工程目录。
5. 在 "名称" 文本框中输入项目名。
6. 确定已勾选 "为解决方案创建目录"，单击 "确认"。
7. 创建好应用之后，看一下解决方案资源管理器。
	- 展开 MainPage.xaml 文件夹，会发现 `MainPage.xaml.cs` 文件，所有的代码都将添加到该文件夹中。
	- 加载 `MainPage.xaml` 文件所定义的 UI 后，就会运行这些代码。
8. 双击 MainPage.xaml，该文件包含 UI 布局。

### 创建用户界面

1. 单击设计视图左侧的 "工具箱" 标签。
	- "工具箱" 中显示了可放到窗体上的各种组件和空间。
2. 展开 "常用 XAML 控件" 区域。
	- 该区域显示了大多数图形应用程序都要使用的控件。
3. 在 "常用 XAML 空间" 区域单击 TextBlock，将 TextBlock 控件拖放到设计视图显示的窗体。
	- TextBlock 是一个仅显示文字的标签。
	- 如果希望工具箱是中可见，同时不想它遮住窗体的任何部分，可以单击工具箱标题栏右侧的 "自动隐藏" 按钮。
4. 窗体上的 TextBlock 空间可能不在理想的地方，可以单击并拖动来重新定位。
	- 在底部窗格中，窗体的 XAML 描述了现在包含的 TextBlock 空间及其属性。
	- `Margin` 属性指定位置。
	- `Text` 属性指定控件上显示的默认文本。
	- `HorizontalAlignment` 和 `VerticalAlignment` 属性指定这些文本的对齐方式。
	- `TextWrapping` 属性指定这些文本是否自动换行。
	- 可以在 XAML 窗格中编辑值，更改会在设计视图中反映。
5. 在 "视图" 菜单中选择 "属性窗口"。
	- 可以利用设计视图下方的 XAML 窗格来编辑控件属性，但属性窗口提供了一种更简便的方式来修改窗体上的各个项以及程序项目中的其他项的属性。
	- 单击窗体任意位置（TextBlock 控件除外），属性窗口将显示 Grid 元素的属性。
	- **所有窗体都包含一个 Grid 属性**，它控制要显示的各个项的布局。
6. 在属性窗口任意修改各个属性的值，直至达到你想要的效果。
7. 从工具箱将一个 TextBox 空间拖放到窗体上。
	- TextBox 是一个文本输入框。
8. 将一个 Button 空间拖放到窗体。
	- Button 是一个按钮。
9. 将 Button 的 Content 属性修改为 OK，按钮上显示的文字也将变为 "OK"。
	- `Content` 属性指定 `Button` 控件显示的文字。
10. 在 "生成" 菜单中选择 "生成解决方案"。
11. 确认 "调试目标" 下拉列表选定的是 "本地计算机"，然后在 "调试" 菜单中选择 "开始调试"。

> 由于各个控件之间还没有添加代码使之做出响应，所以运行后只能够在 TextBlock 输入一些文字，但不会发生任何事情。
