[toc]

## 课前准备

1. Dev-cpp
2. [C语言网](www.dotcpp.com)

> 推荐课外学习教材：《算法竞赛入门经典（第2版）》 刘汝佳 编著 清华大学出版社

## C语言

### 编程规范

- 缩进
	- 代码 `{}` 内的所有代码加上一个 **缩进（Tab）**。

```c
#include<stdio.h>
int main(){                      // 这是 main 函数的代码块
	int radius;
	scanf("%d", &radius);
	if(radius > 10){               // 这是 if 语句的代码块
		printf("输入的半径大于 10");
	}                              // if 语句结束
	else{                          // 这是 else 语句的代码块
		printf("输入的半径小于 10");
	}                              // else 语句结束
	return 0;
}                                // main 函数结束
```

- 标识符
	- 除规定好的标识符规范之外，要求标识符尽量 **有意义**。
	- 常用的标识符：
		- ans：表示答案。
		- flag：表示标志。
		- sum：表示求和。

```c
int radius;            // 表示半径
double PI = 3.1415;    // 表示圆周率
double ans;            // 表示答案
```

## 基本数据类型

|关键字|类型名称|说明|
|-|-|-|
|`int`|整型|取值范围在 - 2<sup>31</sup> ~ 2<sup>31</sup> - 1（大约 21 亿）|
|`short int`|短整型|不常用|
|`long int`|长整型|取值范围在 - 2<sup>31</sup> ~ 2<sup>31</sup> - 1（与 int 范围等同）|
|`long long int`| |取值范围在 - 2<sup>63</sup> ~ 2<sup>63</sup> - 1|
|`float`|单精度浮点数|不常用|
|`double`|双精度浮点数| |
|`char`|字符型|&nbsp;|

```c
#include<limits.h>
#include<stdio.h>
int main(){

	// 测试下 int、long int、long long int 的最大值

	printf("int %d\n",INT_MAX);
	printf("long int %ld\n",LONG_MAX);
	printf("long long int %lld\n", LLONG_MAX);
	// 注意 long long int 所用的占位符

	return 0;
}
```

几个常用的字符型常量

|字符常量|ASCII 码|
|-|-|
|`'A'`|65|
|`'a'`|97|
|`'0'`|48|

## 运算符、输入与输出

### 运算符

|算术运算符|作用|
|-|-|
|`+`|两侧操作数做加法运算|
|`-`|两侧操作数做减法运算|
|`*`|两侧操作数做乘法运算|
|`/`|两侧操作数做除法运算|
|`%`|两侧操作数做除法运算，将余数作为结果|

题目 1：输入一个半径，输出圆的面积。

```c
#include<stdio.h>
int main(){

	double radius;         // 输入需要一个变量进行存储
	double PI = 3.1415926;
	scanf("%lf", &radius);  // 输入

	printf("%lf\n", PI * radius * radius);   // 直接将表达式作为结果输出

	return 0;
}
```

> 如果对精度有要求：`%.mlf   // m 表示精度`

```c
#include<stdio.h>
int main(){
	int a = 10;

	// 自增前缀运算符
	printf("a = %d\n", a++);
	printf("a = %d\n", a);

	// 自增后缀运算符
	a = 10;
	printf("a = %d\n", ++a);
	printf("a = %d\n", a);

	return 0;
}
```

|关系运算符|作用|
|-|-|
|`>`|大于|
|`<`|小于|
|`>=`|大于等于|
|`<=`|小于等于|
|`==`|等于|
|`!=`|不等于|

<table border= "1">
    <tr>
        <th>逻辑运算符</th>
        <th>作用</th>
    </tr>
    <tr>
        <td>&&</td>
        <td>逻辑与</td>
    </tr>
    <tr>
        <td>||</td>
        <td>逻辑或</td>
    </tr>
    <tr>
        <td>!</td>
        <td>逻辑非</td>
    </tr>
</table>

> 在 C 语言中，非 0 即真。

<table border= "1">
    <tr>
        <th>位运算符</th>
        <th>作用</th>
    </tr>
    <tr>
        <td>&</td>
        <td>按位与</td>
    </tr>
    <tr>
        <td>|</td>
        <td>按位或</td>
    </tr>
    <tr>
        <td>^</td>
        <td>按位异或</td>
    </tr>
    <tr>
        <td>~</td>
        <td>按位非</td>
    </tr>
    <tr>
        <td>&lt;&lt;</td>
        <td>左移</td>
    </tr>
    <tr>
        <td>&gt;&gt;</td>
        <td>右移</td>
    </tr>
</table>

- 赋值运算符 `=` 可以与其他运算符（除逻辑运算符）进行合并。
- 类型转换
	- 表达式的结果的类型为操作数中精度最高的类型。
	- 高精度向低精度转换需要 **强制转换**。

### 输入、输出

- 格式输入输出函数

```c
scanf("格式符", &变量1, &变量2, ...);
printf("要输出的字符串、格式符以及转义字符", 变量1, 变量2, ...);
```

|格式字符|作用|
|-|-|
|`%d`|整型变量|
|`%o`|以八进制整型变量|
|`%x`|以十六进制整型变量|
|`%ld`|长整型变量|
|`%lld`| `long long` 型变量|
|`%c`|字符变量|
|`%f`|单精度浮点数|
|`%lf`|多精度浮点数|
|`%s`|字符串|


- 单字符输入输出函数

```c
char c;
getchar(c);  // 输入一个字符
putchar(c);  // 输出一个字符
```

- 多字符输入输出函数

```c
char c[10];
gets(c);      // 输入一个字符串
puts(c);      // 输出一个字符串
```

> gets 函数可以读取字符串中的空格，scanf 函数不能。

## 选择 | 循环

### 选择

```c
if(条件){
	// 条件成立则执行
	语句;
}
else if(条件){
	// 前面的条件不成立且当前条件成立则执行
	语句;
}
...
else{
	// 前面所有套件都不成立
	语句;
}
```

题目2：[输入三个数，输出最大值。](http://www.dotcpp.com/oj/problem1002.html)

```c
#include<stdio.h>
int main(){

	int a, b, c;
	scanf("%d%d%d", &a, &b, &c);
	// 注意占位符之间不需要空格，但输入时两个数字用空格或回车隔开

	if(a > b){
		if(b > c){
			printf("%d\n",a);
		}
		else if(a > c){
			printf("%d\n",a);
		}
		else{
			printf("%d\n",c);
		}
	}
	else{
		if(a > c){
			printf("%d\n",b);
		}
		else if(b > c){
			printf("%d\n",b);
		}
		else{
			printf("%d\n",c);
		}
	}
	return 0;
}
```

**太麻烦了！**

```c
#include<stdio.h>
int main(){

	int a, b, c;
	scanf("%d%d%d", &a, &b, &c);

	int max = a;      // 使用辅助的变量存储最大值
	if(max < b){
		max = b;
	}
	if(max < c){
		max = c;
	}

	printf("%d\n", max);
	return 0;
}
```

> 还可以用条件运算符或函数进行简化。

题目3：鸡兔同笼
一个笼子中同时装有一些鸡和一些兔，输入头和脚的个数，输出鸡和兔的数目，否则输出无法计算。

```c
#include<stdio.h>
int main(){

	int head, feet;
	scanf("%d%d", &head, &feet);

	if((feet % 2) || (feet < head * 2) || （feet > head * 4){    // 需要注意特殊情况
		printf("无法计算\n");
	}
	else{
		int rabbit = (4 * head - feet) / 2;   // 直接使用推导的公式
		int chicken = head - rabbit;

		printf("chicken = %d\nrabbit = %d\n", chicken, rabbit);
	}

	return 0;
}
```

### 开关语句

```c
switch(变量值){  // 变量值只能为 整型、字符型、浮点型
	case 值1:      // 变量值为值 1 时
		语句;        // 执行该语句
		break;       // 跳出 switch 语句，若省略则继续执行下面的 case
	case 值2:
		语句;
		break;
	...
	default:       // 上面的 case 全部不成立时执行
		语句;
		break;
}
```

题目4：彩票中奖
若彩票号码为 123, 456, 789 中一等奖，为 147, 258, 369 中二等奖，为 159, 357, 555 中三等奖，其余号码均未中奖。

```c
#include<stdio.h>
int main(){

	int num;
	scanf("%d",&num);

	switch(num){
		case 123:
		case 456:
		case 789:
			printf("中一等奖\n");
			break;
		case 147:
		case 258:
		case 369:
			printf("中二等奖\n");
			break;
		case 159:
		case 357:
		case 555:
			printf("中三等奖");
			break;
		default:
			printf("未中奖");
			break;
	}
	return 0;
}
```

### 循环

```c
// while 循环
while(条件){
	循环语句;
}

// do-while 循环
do{
	循环语句;
}while(条件)

// for 循环
for(初始化; 条件; 循环自增){
	循环语句;
}
```

题目5：[转换密码](http://www.dotcpp.com/oj/problem1003.html)
按照转换规则，将一串密码转换成对应的密码。
规则：'A' 转换成 'E'，'B' 转换成 'F'，...，'Z' 转换成 'D'（仅输入大写字符）。

```c
#include<stdio.h>
int main(){

	char c;
	while((c = getchar()) != EOF){
	// 注意这道题没有提示输入结束的标志
		if(c >= 'A' && c <= 'Z'){
			putchar((c - 'A' + 4) % 26 + 'A');
		}
		else if(c >= 'a' && c <= 'z'){
			putchar((c - 'a' + 4) % 26 + 'a');
		}
	}
	putchar('\n');

	return 0;
}
```

> scanf() 函数具有返回值，为输入正确输入的个数或 `EOF`。
  getchar() 函数同样具有返回值，为输入正确的字符或 `EOF`。

> 当输入结束时，可以输入 Ctrl + Z 结束输入。

题目6：打印九九乘法表

```c
#include<stdio.h>
int main(){
	// 循环变量默认使用 i, j, k
	for(int i = 1; i <= 9; i ++){         // 可以在循环初始化条件中声明循环变量
		for(int j = 1; j <= i; j ++){
			printf("%d*%d=%d ", i, j, i * j);
		}
		printf("\n");
	}

	return 0;
}
```

## 数组

```c
类型 数组名[数组大小];  // 数组的声明

int a[10];   // 声明一个大小为 10，数组名为 a 的整型数组
char s[10];  // 声明一个大小为 10，数组名为 s 的字符串
```

- 数组的元素下标从 0 起始，若大小为 10，则最后一个元素的下标为 9。
- 字符串总是以 `'\0'` 结尾。

题目5：

```c
#include<stdio.h>
#include<string.h>       // 需要使用 strlen() 函数
int main(){

	char s[100];
	scanf("%s", s);      // 输入字符串使用 %s

	int m = strlen(s);   // strlen() 的作用是返回字符串的长度
	for(int i = 0; i < m; i ++){   // 数组下标从 0 起始，到 长度 - 1 结束
		if(s[i] >= 'A' && s[i] <= 'Z'){
			printf("%c", (s[i] - 'A' + 4) % 26 + 'A');
		}
		else if(s[i] >= 'a' && s[i] <= 'z'){
			printf("%c", (s[i] - 'a' + 4) % 26 + 'a');
		}
	}
	printf("\n");

	return 0;
}
```

题目7：[数组插入数字](http://www.dotcpp.com/oj/problem1025.html)
已有一个已排好的9个元素的数组，今输入一个数要求按原来排序的规律将它插入数组中。

```c
#include<stdio.h>
int main(){

	int num[9];

	for(int i = 0; i < 9; i ++){
		scanf("%d", &num[i]);
	}

	int x;
	scanf("%d", &x);

	for(int i = 0, flag = 1; i < 9; i ++){
		if(flag && num[i] >= x){      // 当输出过 x 值时 flag 置为 0
			printf("%d\n", x);
			flag = 0;
		}
		printf("%d\n", num[i]);
	}

	return 0;
}
```

## 结构体

```c
struct 结构体名{
	结构体内的数据;
};

// 定义一个点
struct point{
	int x;
	int y;
};
```

- 结构体通常定义在函数外。
- 结构体实质上将多个变量整合在一起，使分离的变量之间具有一定的意义。

```c
struct point p1, p2;     // 定义两个结构体变量
p1.x = 0;         // 使用成员运算符 `.`
p1.y = 2;
scanf("%d%d", &p2.x, &p2.y);
printf("%d %d", p2.x, p2.y);
```

题目8：[两点之间距离](http://www.dotcpp.com/oj/problem1172.html)
输入两点坐标(x<sub>x</sub>, y<sub>1</sub>), (x<sub>2</sub>, y<sub>2</sub>)，计算并输出两点间的距离。

```c
#include<stdio.h>
#include<math.h>       // 使用 sqrt() 函数
struct point{
	int x;
	int y;
};
int main(){

	struct point p1, p2;

	while(scanf("%d%d%d%d", &p1.x, &p1.y, &p2.x, &p2.y) != EOF){  // 注意是多组输入数据
		int x = (p1.x - p2.x) * (p1.x - p2.x);
		int y = (p1.y - p2.y) * (p1.y - p2.y);
		printf("%.2lf\n", sqrt(x + y));     // 用 sqrt() 计算平方根
	}
	return 0;
}
```

## 函数与递归

### 函数的定义

```c
返回值类型 函数名(参数列表){
	// 函数体
	语句;
}
```

- 返回值类型即 `return` 后跟着的变量或值的类型，若没有返回值或省略则填写 `void`。
	- 通过 `return` 语句可以 **提前结束** 函数并返回调用处。
	- 若省略返回值则 **执行到大括号** 并返回调用处。
- 参数列表中为函数需要的各个参数，在调用时需要 **提供对应的参数**。

### 递归

```c
#include<stdio.h>
int f(int x){
	if(x < 5){
		f(x + 1);   // 递归的入口
	}
	else{
		return x;   // 必要的出口
	}
}
int main(){

	printf("%d",f(1));
	return 0;
}
```

- 递归是在函数内调用函数本身的一种方式。
- 函数必须有一个入口以及一个出口。
- 通过递归可以不断重复同一个过程，在必要的条件下结束并得到结果。

题目9：[最大公约数和最小公倍数](http://www.dotcpp.com/oj/problem1027.html)
写两个函数，分别求两个整数的最大公约数和最小公倍数，用主函数调用这两个函数，并输出结果两个整数由键盘输入。

```c
#include<stdio.h>

// 可以将公用的变量放在函数外作为全局变量
// 全局变量可以被从声明位置起以后的所有语句使用
int num1, num2;
int GCD;

// 利用 辗转相除法 求得两个数的最小公约数
int gcd(int a, int b){  // 函数参数以在函数内有效
	if(a < b){
		int temp = a, a = b, b = temp;  // 这个局部变量只在该代码块间有效
	}
	if(!(a % b)){
		return b;
	}
	gcd(b, a % b);
}

// 最大公约数 * 最小公倍数 = 两数乘积
int lcm(){
	return num1 * num2 / GCD;
}
int main(){

	scanf("%d%d", &num1, &num2);
	GCD = gcd(num1, num2);
	printf("%d %d\n",GCD, lcm());
	return 0;
}
```

## 预处理

- include 预处理
	- 用来加载头文件。
- define 预处理
	- 用来将指定字符序列替换成对应的字符序列

```c
#define PI 3.1415926  // 常用于定义一个常量
```

## 思考题

1. [进制转换](http://www.dotcpp.com/oj/problem1055.html)
2. 阶乘之和
		- 输入 n，计算 S = 1! + 2! + ... + n! 的末 6 位（不含前导 0）。
		- 样例输入：10
		- 样例输出：37913
3. 汽水瓶
		- “某商店规定：三个空汽水瓶可以换一瓶汽水。小张手上有十个空汽水瓶，她最多可以换多少瓶汽水喝？”答案是5瓶。
		- 样例输入：10
		- 样例输出：5
4. WERTYU
		- 输入往右一个错位后敲出的字符串（所有字母均大写），输出打字员本来想打出的句子，且输入保证合法。
		- 样例输入：O S, GOMR YPFSU/
		- 样例输出：I AM FINE TODAY.
5. 生成元
		- 如果 x 加上 x 的各个数字之和得到 y，就说 x 是 y 的生成元。给出 n 求出最小生成元，无解输出 0。
		- 样例输入1：216
		- 样例输出1：198
		- 样例输入2：121
		- 样例输出2：0
		- 样例输入3：2005
		- 样例输出3：1979
