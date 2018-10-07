[toc]

## 课程概要

1. 讲解 C 程序与 C++ 程序的不同之处。
2. 介绍 C++ 输入输出，字符串以及 algorithm 头文件。

例题：

- [简单的 a+b 程序](http://acm.hdu.edu.cn/showproblem.php?pid=1000)
- [字符串统计](http://acm.hdu.edu.cn/showproblem.php?pid=2017)
- [数列有序](http://acm.hdu.edu.cn/showproblem.php?pid=2019)

## 讲解

### 头文件

[简单的 a+b 程序](http://acm.hdu.edu.cn/showproblem.php?pid=1000)

之前我们写过的 C 语言程序可能会这么写：

```c
#include<stdio.h>

int main(){

  int a, b;
  while(scanf("%d%d", &a, &b) != EOF){
		printf("%d\n", a + b);
	}
  return 0;
}
```

现在我们看看 C++ 会怎么写：

```cpp
#include<cstdio>

int main(){

    int a, b;
    while(scanf("%d%d", &a, &b) != EOF){
    	printf("%d\n", a + b);
	}

    return 0l;
}
```

似乎只有头文件不太一样。。。

- 我们之前写的代码在 C++ 里同样可以运行。
- 虽然我们把头文件 `stdio.h` 换成了 `cstdio`，但原头文件仍然存在。
- C++ 推荐使用以 c 开头的头文件，即 `cstdio`/`cstring`/`cctype`/`cmath`。

### C++ 的输入输出

C++ 有别于 C 的一个特性是：C++ 可以使用 **流** 进行输入输出。

依旧是 A+B 问题。

```cpp
#include<iostream>
using namespace std;

int main(){

    int a, b;
    while(cin >> a >> b){
    	cout << a + b << endl;
	}

    return 0;
}
```

- 这次我们使用流进行输入输出。头文件 `iostream` 中包含了系统已经定义好的 **输入流 `cin`** 和 **输出流 `cout`**。
- `using namespace std;` 是一个没有见过的语句。
	- `namespace` 关键字用于定义一个命名空间，防止在导入多个文件时因标识符重复导致的编译问题。
	- 当我们把这行代码注释掉的时候，编译后会报错，因为流本身存在于 **默认系统空间 `std`** 中。

```cpp
#include<iostream>
//using namespace std;

int main(){

    int a, b;
    while(std::cin >> a >> b){    // 注释掉后将在 cin 前加上 std:: 表示引用 std 命名空间中的 cin
    	std::cout << a + b << std::endl;   // cout 和 endl 同理
	}

    return 0;
}
```

- `using` 关键字表示对于当前 cpp 文件中直接引入 std 命名空间，免去了写一些重复的命名空间。
	- 在实际应用中，不推荐该写法，但算法竞赛为了高效默认了该做法。
- 对于输入流 `cin`，可以使用 `>>` 运算符表示从当前流中读取出后面跟的变量对应存储空间大小的数据。
	- `cin >> a >> b` 表示从流中读取变量 a 大小的数据后，将从剩下的流中读取变量 b 大小的数据。
- 对于输出流 `cout`，可以使用 `<<` 运算符表示将后面的变量通过流输出到控制台。
	- `endl` 等价于 `'\n'`。

输入输出流的优势在于 **不需要任何的占位符**，缺点在于处理速度比 `scanf`/`printf` 慢一些。

> 有的题目要求数据量过大，不允许使用输入输出流。

### 字符串 string

在 C 语言中，不存在 `string` 这种单独的类型，所有的字符串必须存储在 `char[]` 数组中。
在 C++ 中，通过头文件 `string` 引入 `string` 类型。

```cpp
#include<iostream>
#include<string>         // 引入 string 头文件
using namespace std;

int main(){

  char c[] = "Hello";     // C 语言中的字符串
  string str1("Hello");   // 调用参数为 常量字符串 的构造方法创建
	string str2(c);         // 调用参数为 字符数组 的构造方法创建
	string str3(str1);      // 调用参数为 字符串 的构造方法创建
	string str4 = "Hello";  // 直接赋值

	cout << str1 << endl << str2 << endl << str3 << endl << str4 << endl;

  return 0;
}
```

同样，我们可以使用流进行输入输出。

```cpp
#include<iostream>
#include<string>
using namespace std;

int main(){

	string str;

	cin >> str;
	cout << str;

    return 0;
}
```

但是，当我们输入了一个空格，输入回车表示结束时，发现只输出了空格之前的内容。

> 这里类似 `scanf` 输入字符串操作。当然，不可以使用 `%s` 作为 `string` 的占位符。

如果我们确实需要输入一些空格时，可以使用 `getline` 方法。

```cpp
#include<iostream>
#include<string>
using namespace std;

int main(){

	string str;

	getline(cin, str);
	cout << str;

    return 0;
}
```

我们还可以通过 `[]` 运算符索引到字符串中的每个元素。

```cpp
#include<iostream>
#include<string>
using namespace std;

int main(){

	string str = "Hello";

	for(int i = 0; i < str.length(); i ++){
		cout << str[i] << endl;
	}

    return 0;
}
```

注意到我们使用了 `str.length()` 作为判断条件，`length()` 是 `string` 类中的方法，通过成员运算符 `.` 调用。

```cpp
#include<iostream>
#include<string>
using namespace std;

int main(){

	string str = "Hello";

	str.insert(2, "x");             // 在下标为 2 的元素后插入 x
	cout << str.size() << endl;     // size() 等价于 length()
	// 注意到 str 从 5 变为 6，说明 str 的内容已经改变

	str.erase(4);                   // 删除下标为 4 之后的元素
	str += "World";                 // 通过运算符 += 在后面追加字符串
	cout << str << endl;

	str.clear();                    // 清空字符串
	if(str.empty()){                // 判断字符串是否为空
		cout << "Empty!";
	}

    return 0;
}
```

[字符串统计](http://acm.hdu.edu.cn/showproblem.php?pid=2017)

我们很容易写出如下代码：

```cpp
#include<iostream>
#include<string>
#include<cctype>
using namespace std;

int main(){

	int n;
	cin >> n;
	cin.ignore();
	// 由于 cin 碰到回车自动都去结束，导致换行符仍然在流中，使用 ignore 方法忽略掉

	while(n--){
		string str;
		getline(cin, str);

		int count = 0;
		for(int i = 0; i < str.length(); i ++){
			if(isdigit(str[i])){
				count ++;
			}
		}
		cout << count << endl;
	}

    return 0;
}
```

### argorithm 头文件

这个头文件实际上包含了很多常用的函数，比如 `min`/`max`/`sort`/`lower_bound` 等。

[数列有序](http://acm.hdu.edu.cn/showproblem.php?pid=2019)

```cpp
#include<iostream>
#include<algorithm>
using namespace std;
const int maxn = 100 + 5;
int num[maxn];

int main(){

	int n ,m;
	while(cin >> n >> m){
		if(!n && !m){
			break;
		}

		for(int i = 0; i < n; i ++){
			cin >> num[i];
		}
		num[n] = m;                 // 直接将要插入的数放在数组最后

		sort(num, num+n+1);     // sort 默认从小到大排序，需要的参数有数组起始地址和数组末地址

		for(int i = 0; i < n+1; i ++){
			cout << num[i] << (i == n?"\n":" ");
		}
	}

    return 0;
}
```
