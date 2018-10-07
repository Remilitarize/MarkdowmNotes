[toc]

## Overview

- vector
	- [词组缩写](http://acm.hdu.edu.cn/showproblem.php?pid=2564)
- stack
	- [Bitset](http://acm.hdu.edu.cn/showproblem.php?pid=2051)
- queue
	- 讲 BFS 时使用。
- priority_queue
	- [Fence Repair](http://poj.org/problem?id=3253)
- set
	- [Andy's First Dictionary](https://vjudge.net/problem/UVA-10815)
- map
	- [水果](http://acm.hdu.edu.cn/showproblem.php?pid=1263)

## STL 模板

### vector 向量

vector 是不定长数组。
相比数组，vector 能够根据需要自动调整大小以便容下更多元素。

```cpp
#include<iostream>
#include<vector>               // 使用 vector 需要加载该头文件
using namespace std;

int main(){

	vector<int> v1;            // 定义一个容纳 int 的 vector
	vector<string> v2;         // 定义一个容纳 string 的 vector

	vector<int>::iterator it;  // 定义一个指向 vector<int> 的迭代器

	for(int i = 1; i <= 10; i ++){
		v1.push_back(i);         // 使用 push_back 函数在最后添加一个数据
	}

	cout << "下标为 3 的元素是" << v1[3] << endl;   // 使用索引

	cout << "弹出最后的元素" << v1.back() << endl;  // 使用 back() 函数获取最后的元素
	v1.pop_back();             // 使用 pop_back 函数去除最后的元素

	cout << "在下标为 5 的位置上插入 10" << endl;
	v1.insert(v1.begin() + 5, 10);

	cout << "删除下标为 3 的元素" << endl;
	v1.erase(v1.begin() + 3);

	cout << "当前 vector 大小为：" << v1.size() << endl;
	                           // 使用迭代器遍历 vector
	for(it = v1.begin(); it != v1.end(); it ++){
		cout << *it << " ";
	}
	cout << endl;

	v1.clear();                // 清空数组

	if(v1.empty()){
		cout << "vector 已空" << endl;
	}

	return 0;
}
```

[词组缩写](http://acm.hdu.edu.cn/showproblem.php?pid=2564)

```cpp
#include<iostream>
#include<vector>
#include<string>
#include<sstream>
#include<cctype>
using namespace std;

int main(){

	vector<string> v;
	vector<string>::iterator it;

	int n;
	cin >> n;
	cin.ignore();

	while(n --){
		string s, str;
		getline(cin, s);
		stringstream ss(s);
		while(ss >> str){
			v.push_back(str);
		}

		for(it = v.begin(); it != v.end(); it ++){
			cout << (char)toupper((*it)[0]);
		}

		cout << endl;
		v.clear();
	}

	return 0;
}
```

### stack 栈

stack 是一种 **后进先出** 的线性数据结构。
可以想象成生活中的收纳箱，把衣物一件一件放入，取出底下的衣物之前需要先把上面的取出。

```cpp
#include<iostream>
#include<stack>               // 使用 stack 需要加载该头文件
using namespace std;

int main(){

	stack<int> s;             // 定义可以容纳 int 的栈

	for(int i = 1; i <= 10; i ++){
		s.push(i);            // 使用 push 函数
	}

	cout << "当前栈中元素个数：" << s.size() << endl;  

	while(!s.empty()){
		cout << s.top() << endl;  // 获取栈顶元素
		s.pop();                 // 栈顶元素弹出
	}

	return 0;
}
```

[Bitset](http://acm.hdu.edu.cn/showproblem.php?pid=2051)

```cpp
#include<iostream>
#include<stack>
using namespace std;

int main(){

	stack<int> s;

	int n;
	while(cin >> n){
		while(n){
			s.push(n % 2);
			n /= 2;
		}
		while(!s.empty()){
			cout << s.top();
			s.pop();
		}
		cout << endl;
	}

	return 0;
}
```

### queue 队列

queue（队列）是一种 **先进先出** 的线性数据结构。
类似于排队等候的例子，元素总是从队尾入队，从队头出队。

```cpp
#include<iostream>
#include<queue>               // 使用 queue 需要加载该头文件
using namespace std;

int main(){

	queue<int> q;             // 定义可以容纳 int 的队列

	for(int i = 1; i <= 10; i ++){
		q.push(i);
	}

	cout << "当前队列元素个数：" << q.size() << endl;  

	while(!q.empty()){
		cout << q.front() << endl;  // 获取队头元素
		q.pop();                    // 队头元素弹出
	}

	return 0;
}
```

由于 quwuw 不经常单独使用，将与后面具体的算法实现一同食用。

### priority_queue 优先队列

priority_queue（优先队列）是一种带有优先级的队列。
每次有新元素入队时，总会按照优先级进行重新排队。

```cpp
#include<iostream>
#include<queue>               // 使用 priority_queue 需要加载该头文件
using namespace std;

int main(){

	priority_queue<int> q;             // 定义可以容纳 int 的优先队列
	// 默认的优先级是元素越大优先级越高
	priority_queue<int, vector<int>, less<int> > q0;   // 等价

	for(int i = 1; i <= 10; i ++){
		q.push(i);
	}

	cout << "当前队列元素个数：" << q.size() << endl;  

	while(!q.empty()){
		cout << q.top() << endl;  // 获取队头元素
		q.pop();                    // 队头元素弹出
	}

	cout << "--------------" << endl;

	priority_queue<int, vector<int>, greater<int> > qq;

	for(int i = 10; i >= 1; i --){
		qq.push(i);
	}

	while(!qq.empty()){
		cout << qq.top() << endl;
		qq.pop();
	}

	return 0;
}
```

[Fence Repair](http://poj.org/problem?id=3253)

```cpp
#include<iostream>
#include<queue>               // 使用 priority_queue 需要加载该头文件
using namespace std;

int main(){

	priority_queue<int, vector<int>, greater<int> > q;

	int n;
	while(cin >> n){
		while(n --){
			int m;
			cin >> m;
			q.push(m);
		}

		long long ans = 0;

		while(q.size() > 1){
			int a = q.top();
			q.pop();
			int b = q.top();
			q.pop();
			q.push(a + b);
			ans += a + b;
		}

		cout << ans << endl;
	}

	return 0;
}
```

### set 集合

set（集合）重要的性质就是 **不包含任何重复元素**。
对于 STL 模板，set 还会自动进行排序，但不可进行修改其值。

> set 实际上实现了红黑树的平衡二叉检索树的数据结构。

```cpp
#include<iostream>
#include<set>               // 使用 set 需要加载该头文件
using namespace std;

struct cmp{
	bool operator()(const int &a, const int &b){
		return a > b;
	}
};

int main(){

	set<int> s;             // 定义容纳 int 键值的集合
	// 默认排序方式为从小到大

	s.insert(2);            // 使用 insert 函数插入一个键值
	s.insert(4);
	s.insert(1);
	s.insert(7);
	s.insert(6);

	set<int>::iterator it;  // 使用迭代器进行遍历

	for(it = s.begin(); it != s.end(); it ++){
		cout << *it << endl;
	}

	s.erase(6);             // 删除键值为 3 的元素

	cout << "删除了键值为 6 的元素" << endl;

	for(it = s.begin(); it != s.end(); it ++){
		cout << *it << endl;
	}

	it = s.find(4);
	if(it != s.end()){
		cout << "找到键值为 4 的元素" << endl;
	}
	else{
		cout << "未找到键值为 4 的元素" << endl;
	}

	set<int, cmp> ss;

	ss.insert(6);
	ss.insert(7);
	ss.insert(1);
	ss.insert(5);

	for(it = ss.begin(); it != ss.end(); it++){
		cout << *it << endl;
	}

	return 0;
}
```

[Andy's First Dictionary](https://vjudge.net/problem/UVA-10815)

```cpp
#include<iostream>
#include<set>
#include<cctype>
#include<string>
#include<sstream>
using namespace std;

int main(){

	string s;
	set<string> dict;
	set<string>::iterator it;

	while(cin >> s){
		stringstream ss;
		for(int i = 0; i < s.length(); i ++){
			if(isalpha(s[i])){
				s[i] = tolower(s[i]);
			}
			else{
				s[i] = ' ';
			}
		}

		ss << s;

		string temp;
		while(ss >> temp){
			dict.insert(temp);
		}
	}

	for(it = dict.begin(); it != dict.end(); it++){
		cout << *it << endl;
	}

	return 0;
}
```

### map 图

map（图） 可以进行 **键-值** 的存储。

```cpp
#include<iostream>
#include<map>              // 使用 map 则必须包含该头文件
#include<string>
using namespace std;

int main(){

	map<int, int> m;       // 创建 int - int 的图
	map<int, string> m0;   // 创建 int - string 的图

	m[7] = 2;              // 使用 [] 进行插入
	// 该插入方式会先判断是否存在键为 7 的键值对，若没发现，则创建该键，再赋对应的值
	// 如果找到了该键，则覆盖原来的值

	// 下面两种当已存在一个键，将不会覆盖值
	m.insert(pair<int,int>(2, 3));  // 使用 insert 函数传递 pair

	m.insert(map<int, int>::value_type(4, 5));  // 使用 insert 函数传递 value_type

	cout << "当前 m 的大小" << m.size() << endl;

	map<int, int>::iterator it;            // 使用迭代器进行遍历

	for(it = m.begin(); it != m.end(); it++){
		cout << it->first << ' ' << it->second << endl;
		// 通过迭代器指针获取键 first 和值 second
	}

	m.erase(4);           // 删除键为 4 的键值对

	if(m.empty()){
		cout << "m 空了" << endl;
	}
	else{
		cout << "当前 m 的大小" << m.size() << endl;
	}

	return 0;
}
```

[水果](http://acm.hdu.edu.cn/showproblem.php?pid=1263)

```cpp
#include<iostream>
#include<map>              // 使用 map 则必须包含该头文件
#include<string>
using namespace std;

int main(){

	int n;

	map<string, map<string, int> >  fruit;
	map<string, map<string, int> >::iterator it1;
	map<string, int>::iterator it2;
	cin >> n;
	while(n--){
		int m;
		cin >> m;
		while(m--){
			string name, place;
			int x;
			cin >> name >> place >> x;

			fruit[place][name] += x;
		}
		for(it1 = fruit.begin(); it1 != fruit.end(); it1++){
			cout << it1->first << endl;
			for(it2 = it1->second.begin(); it2 != it1->second.end(); it2++){
				cout << "   |----" << it2->first << "(" << it2->second << ")" << endl;			
			}
		}

		fruit.clear();
		if(n != 0){
			cout << endl;
		}
	}

	return 0;
}
```
