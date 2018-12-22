[toc]

## 图形窗口与坐标轴

### 图形对象的句柄

句柄概念：在 Matlab 中，用句柄来表示对象，通过句柄来访问相应对象的属性。

例：绘制多个图形，并保存图形句柄。

```matlab
t = 0: pi/10: 2*pi;
h1 = plot3(t + pi, t - 2*pi, sin(t), 'r');
hold on;
[x, y] = meshgrid(t);
z = sin(x);
h2 = mesh(t - 2*pi, t + pi, z);
[x3, y3, z3] = cylinder(t);
h3 = surf(x3, y3, z3);
```

- 访问图形对象：`对象句柄.属性名`
- 获取特定图形对象句柄的函数：
    - `gcf`：获取当前图形窗口的句柄。
    - `gca`：获取当前坐标轴的句柄。
    - `gco`：获取最近被选中的图形对象的句柄。
    - `findobj`：按照指定的属性来获取图形对象的句柄。

### 图形对象的属性

- 常用公共属性：
    - `Children`：该对象的所有子对象的句柄组成的一个向量。
    - `Parent`：该对象的父对象的句柄。
    - `Type`：对象的类型（只读）。
    - `Tag`：给对象定义一个标识符。

例：

```matlab
subplot(1, 2, 1)
h1 = fplot(@(t) t.*sin(t), @(t) t.*cos(t), [0, 6*pi]);
axis equal
subplot(1, 2, 2)
[x, y, z] = peaks(20);
h2 = mesh(x, y, z);
h10 = h1.Parent;           % 曲线的父对象是坐标轴
h10.Color = 'y';
h1.Color = 'r';
h2.Parent.Color = 'cyan';
```

- 常用动态属性：
    - `KeyPressFcn`：定义按下键盘按键事件的响应。
    - `CreateFcn`：定义创建图形对象时做出的响应。
    - `DeleteFcn`：定义取消图形对象时做出的响应。
    - `WindowButtonDownFcn` 或 `ButtonDownFcn`：定义单击鼠标左键事件的响应。

### 图形窗口的操作

- 建立窗口对象：
    - `句柄变量 = figure(属性1, 属性值1, 属性2, 属性值2, ...)`
    - `句柄变量 = figure`
    - `figure(窗口句柄)`
- 图形窗口属性：
    - `MenuBar`：控制图形窗口是否有菜单条，取值为 `none` 或 `figure`。
    - `Name`：指定指定图形窗口的标题。
    - `NumberTitle`：决定图形窗口的标题中是否以 "Figure n:" 为标题前缀。
    - `Color`：设定图形窗口背景的颜色。
    - `Position`：定义图形窗口对象在屏幕上的位置和大小，值为 `[x, y, w, h]`。
    - `Units`：定义图形窗口使用的长度单位，默认值为 `pixels`。
        - `pixels`/`inches`/`centimeters`/`points`/`normalized`

### 坐标轴对象的操作

- 建立坐标轴对象：
    - `句柄变量 = axes(属性1, 属性值1, 属性2, 属性值2, ...)`
    - `句柄变量 = axes`
    - `axes(坐标轴句柄)`
- 坐标轴对象的属性：
    - `Position`：定义坐标轴在图形窗口中的位置和大小。
    - `Units`：定义坐标轴使用的度量单位，默认值为 `normalized`。
    - `Box`：决定坐标收是否带有边框，取值为 `on` 或 `off`。
    - `GridLineStyle`：用于定义网格线的类型，取值为 `:`/`-`/`-.`/`--`/`none`。
    - `Title`：用于对坐标轴标题对象进行操作，取值是通过 `title` 函数建立的标题对象的句柄。
    - `XLabel`/`YLabel`/`ZLabel`：取值分别是通过 `xlabel`/`ylabel`/`zlabel` 函数建立的坐标轴标签对象的句柄。
    - `XLim`/`YLim`/`ZLim`：用于定义各坐标轴的下限和上限，取值为 `[Lmin, Lmax]`，默认值为 `[0, 1]`。
    - `XScale`/`YScale`/`ZScale`：用于定义各坐标轴的刻度类型，取值为 `linear`/`log`。
    - `View`：用于定义视点，取值为 `[az, el]`，`az` 定义视点的方位角，`el` 定义视点的仰角。
    - `ColorOrder`：用于设置多条曲线的颜色顺序，是一个 n\*3 矩阵，默认 n 为 7。

例：利用坐标轴对象实现图形窗口的分割。

```matlab
ha1 = axes('Position', [0.1, 0.1, 0.7, 0.7]);
contour(peaks(20));
ha1.Title = title('等高线');
ha1.YLabel = ylabel('南北向');
ha1.XLabel = xlabel('东西向');
ha2 = axes('Position', [0.65, 0.7, 0.28, 0.28]);
surf(peaks(20));
ha2.View = [-30, 45];
```

## 曲线与曲面对象

### 曲线对象

- 建立曲线对象
    - `句柄变量 = line(x, y, z, 属性1, 属性值1, 属性2, 属性值2, ...)`
- 曲线对象常用属性：
    - `Color`：定义曲线颜色，默认值为 `[0, 0, 0]`。
    - `LineStyle`：定义线型，默认值为 `-`。
    - `LineWidth`：定义线宽，默认值为 0.5 磅。
    - `Marker`：定义数据点标记符号，默认值为 `none`。
    - `MarkerSize`：定义数据点标记符号的大小，默认值为 6 磅。
    - `XData`/`YData`/`ZData`：设置 3 个坐标轴的数据源。

### 曲面对象

- 建立曲面对象
    - `句柄变量 = surface(x, y, z, c, 属性1, 属性值1, 属性2, 属性值2, ...)`
        - `c` 指定不同高度下的颜色。
- 曲面对象有关属性：
    - `FaceColor`：定义曲面网格片的颜色。
        - `flat`：每一个网格片用单一颜色填充。
        - `interp`：用渐变方式填充网格片。
        - `none`：网格片无颜色。
        - `texturemap`：用 `Cdata` 属性定义的颜色填充网格片。
        - RGB 向量或代表颜色的字符。
    - `EdgeColor`：定义曲面网格线的颜色。

### 光照处理

- 光照处理
    - `对象句柄 = light(属性1, 属性值1, 属性2, 属性值2, ...)`
- 光源对象的属性：
    - `Color`：设置光的颜色。
    - `Style`：设置光源类型，取值为 `infinite` 或 `local`。
    - `Position`：指定光源位置。
- 光照模式
    - `lighting 选项`
    - 选项取值为：`flat`/`gouraud`/`phong`/`none`

例：

```matlab
r = linspace(0.2*pi, 60);
[u, v] = neshgrid(r);
x = (8 + 3*cos(v)).*cos(u);
y = (8 + 3*cos(v)).*sin(u);
z = 3 * sin(v);

axes('Position', [0.05, 0.675, 1.0, 0.3], 'View', [-37.5, 30]);
hs1 = surface(x, y, z);
axis equal;
hs1.EdgeColor = 'none';
hs1.FaceColor = 'interp';

axes('Position', [0.05, 0.35, 1.0, 0.3], 'View', [-37.5, 30]);
hs2 = surface(x, y, z);
axis equal;
hs2.EdgeColor = 'none';
hs2.FaceColor = 'interp';
light('Position', [0, 0, 8]);
lighting flag

axes('Position', [0.05, 0.025, 1.0, 0.3], 'View', [-37.5, 30]
hs3 = surface(x, y, y);
axis equal;
hs3.EdgeColor = 'none';
hs3.FaceColor = 'interp';
light('Position', [0, 0, 8]);
lighting phong
```

### 图形对象的反射特性

- `SpecularStrength`：控制对象表面镜面反射的强度。
- `DiffuseStrenghth`：控制对象表面漫反射的强度。
- `AmbientStrength`：确定环境光的强度。
- `SpecularExponent`：控制镜面反射指数。
- `BackFaceLighting`：控制对象内表面和外表面的区别。
    - `unlit`/`lit`/`reverselit`

## 图形界面设计方法

### 图形用户界面的组成

图形用户界面：用户与计算机进行信息信息交流的窗口。

设计图形用户界面的方法：

- 调用建立用户界面控件的函数。
- 使用 Matlab 提供的 `GUIDE` 工具进行可视化操作。

### 控件对象及其操作

- 常用控件
    - 输入和输出控件：编辑框、静态文本、列表框、滑动条等。
    - 实施确认、选择操作类控件：按钮、双位按钮、单选按钮、复选框等。
- 建立控件对象
    - `句柄对象 = uicontrol(图形窗口句柄, 属性1, 属性值1, 属性2, 属性值2, ...)`
- 控件对象的基本控制属性
    - `Style`：定义控件对象的类型。
        - `pushbutton`：表示按钮对象。
        - `edit`：表示编辑框。
    - `String`：定义控件对象的说明文字。
    - `Tag`：标识控件对象。
    - `Enable`：控制控件对象是否可用。
    - `Position`：定义控件对象的位置和大小，其取值形式为 `[x, y, w, h]`。
    - `Callback`：属性值是描述命令的字符串或函数句柄。
        - 当选中控件时，系统将自动执行字符串描述的命令或调用句柄所代表的函数。
- 回调函数

```matlab
function 函数名(source, eventdata)
    % source 是发生事件的源控件句柄。
    % eventdata 存储事件数据
end
```

```matlab
function plot_sin(source, callbackdata)
    t = -pi: pi/20: pi;
    plot(t, sin(t));
end
```

```matlab
ha = axes('Units', 'pixels', 'Position', [40, 40, 360, 360]);
ptgrid = uicontrol('Style', 'pushbutton', 'String', '网格', ...
                    'Position', [450, 120, 48, 20], 'Callback', 'grid');
btncla = uicontrol('Style', 'pushbutton', 'String', '清除', ...
                    'Position', [450, 80, 48, 20], 'Callback', 'cla');
btnplot = uicontrol('Style', 'pushbutton', 'String', '绘图', ...
                    'Position', [450, 160, 48, 20]);
btnplot.Callback = @plot_sin;
```

### 菜单对象

- 建立菜单对象
    - `一级菜单项句柄 = uimenu(图形窗口句柄, 属性1, 属性值1, 属性2, 属性值2, ...)`
    - `子菜单项句柄 = uimenu(上级菜单项句柄, 属性1, 属性值1, 属性2, 属性值2, ...)`
- 菜单属性
    - `Label`：定义菜单项的名字。
    - `Accelerator`：定义菜单项的快捷键。
    - `Checked`：指示菜单项是否已选中。
    - `Enable`：控制菜单项的可选择性。
    - `Separator`：用于在菜单中添加分隔线。

```matlab
function MLine_Type(source, callbackdata)
    hline = findobj('Type', line);
    if strcmp(source.Tag, 'Solid') == 1
        hline.LineStyle = '-';
    elseif strcmp(source.Tag, 'Dotted') == 1
        hline.LineStyle = ':';
    elseif strcmp(source.Tag, 'Dashed') == 1
        hline.LineStyle = '--';
    end
end
```

```matlab
hopt = uimenu(gcf, 'Label', '图形选项', 'Accelerator', 'L');
hLStyle = uimenu(Hopt, 'Label', '线型', 'Tag', 'LStyle', 'Enable', 'off');
hL_Solid = uimenu(hLStyle, 'Label', '实线', 'Tag', 'Solid', 'Callback', @MLine_Type);
hL_Dotted = uimenu(hLStyle, 'Label', '虚线', 'Tag', 'Dotted', 'Callback', @MLine_Type);
hL_Dashed = uimenu(hLStyle, 'Label', '双划线', 'Tag', 'Dashed', 'Callback', @MLine_Type);
```

```matlab
function plot_sin(source, callbackdata)
    t = -pi: pi/20: pi;
    plot(t, sin(t));
    h1 = findobj('Tag', 'LStyle');
    h1.Enable = 'On';       % 仅当绘制完曲线后可用
end
```

## 图形界面设计工具

### 图形用户界面设计窗口

- 打开 GUIDE
    - 输入 `guide` 命令
    - 选择“主页”选项卡，单机工具栏的“新建”命令按钮，再选择“应用程序”下的 GUIDE 命令。
- 图形用户界面设计模板
    - Blank GUI(Default)
    - GUI with Uicontrols
    - GUI with Axes and Menu
    - Modal Question Dialog

> 具体设计窗口介绍略

### 回调属性与回调函数

- 回调属性：处理消息并响应事件。
    - `Callback`：按钮类控件和菜单项的单击事件的默认回调属性。
    - `ButtonDownFcn`：定义单机鼠标键按下的响应。
    - `KeyPressFcn`：定义键盘键按下的响应。
    - `SelectionChangeFcn`：定义改变选项的响应。
- 回调函数：

```matlab
function 对象标识_Callback(hObject, eventdata, handles)
    % hObject 为发生事件的源控件
    % eventdata 为事件数据
    % handles 保存图形界面中所有对象的句柄
end
```

## APP 设计工具

> 后缀名为 `.mlapp`

### App Designer 的使用

- 打开 App Designer
    - 输入 `appdesigner` 命令
    - 选择“主页”选项卡，单击工具栏“新建”命令按钮，再选择“应用程序”下的“App Designer”命令。

> 具体设计窗口介绍略

### App 组件

- 常用组件
- 容器组件
    - 面板
    - 选项卡
- 仪器组件
    - 仪表
    - 旋钮

### App 程序

***类的基本结构***

```matlab
classdef 类名 < matlab.apps.AppBase
    properties (Access = public)
        ...
    end

    methods (Access = public)
        function 函数1 (app)
            ...
        end
        function 函数2 (app)
            ...
        end
    end
end
```

***访问权限***

- `private`：私有
    - 只允许在类中访问。
- `public`：公共
    - 可用于与 App 的其他类共享。

> 属性的声明、`startupFcn` 函数、`createComponents` 函数、回调函数的默认权限是 `private`。

***运行 App***

- 在 App 设计器窗口中按“F5”键或单击工具栏上的“运行”命令按钮。
- 在 Matlab 主窗口的当前文件夹双击 mlapp 文件。
- 在命令行窗口输入 mlapp 文件的住文件名。

***打包 App 应用***

选中 App Designer 窗口的“设计器”选项卡，单击工具栏中的“App 应用打包”按钮，弹出“应用程序打包”对话框。


