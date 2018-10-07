[toc]

## MySQL 数据库管理系统

使用与安装 MySQL 不作为讲课范畴内，略。

## JDBC

**JDBC（Java Database Connectivity）** 提供了访问数据库的 API。

经常使用 JDBC 进行如下的操作：

- 与一个数据库建立连接
- 向已连接的数据库发送 SQL 语句
- 处理 SQL 语句返回的结果

## 连接 MySQL 数据库

应用程序为了能和数据库交互信息，必须首先和数据库建立连接。
目前在开发中常用的连接数据库的方式是 **加载 JDBC 数据库驱动程序**。

用 Java 语言编写的数据库驱动程序称为 JDBC 数据库驱动程序。

使用 JDBC 数据库驱动程序方式和数据库建立连接需要经过两个步骤：

- 加载 JDBC 数据库驱动程序
- 与指定的数据库建立连接

### 加载 JDBC 数据库驱动程序

1. 从网络上下载驱动程序，文件名为 `mysql-connector-java-%版本号%-bin.jar`。
2. 将文件放在 JDK 的扩展目录中（`%JDK 安装目录%\jre\lib\ext`）。
3. 添加如下代码，使应用程序加载 MySQL 的 JDBC 数据库驱动程序。

```java
try{
	Class.forName("com.mysql.jdbc.Driver")；
}
catch(Exception e){}
```

### 建立连接

```java
Connection con = null;
try{
	String url = "jdbc:mysql://192.168.100.1:3306/warehouse";
	String user = "root";
	String password = "99";
	con = DriverManager.getConnection(url, user, password);
}
catch(SQLException e){}
```

```java
Connection con = null;
try{
	String url = "jdbc:mysql://192.168.100.1:3306/warehouse?user=root&password=99";
	con = DriverManager.getConnection(url);
}
catch(SQLException e){}
```

> 如果用户没有设置密码，则把密码设为空字符串。

某些 Web 程序中需要避免操作数据库出现中文乱码，那么要使用如下方法建立连接。

```java
Connection con = null;
try{
	String url = "jdbc:mysql://192.168.100.1:3306/warehouse?user=root&password=99&characterEncoding=UTF-8";
	con = DriverManager.getConnection(url);
}
catch(SQLException e){}
```

## 查询记录

### 结果集与查询

```java
Statement state = null;
ResultSet result = null;
try{
	state = con.createStatement();            // 创建 SQL 语句对象
	result = state.executeQuery("SQL 语句");  // 执行 SQL 语句，并将查询的结果集存储到 result 中
}
catch(SQLException e){}
```

ResultSet 结果集一次只能看到一个数据行，通过 **`next()` 方法** 可走到下一数据行。

> 若已经是最后一行，将返回 `false`。

获得一行数据后，可以使用以下方法获取字段值（列值）。

|方法名称|返回类型|方法名称|返回类型|
|-|-|-|-|
|getByte(int columnIndex)|byte|getByte(String columnName)|byte|
|getDate(int columnIndex)|Date|getDate(String columnName)|Date|
|getDouble(int columnIndex)|double|getDouble(String columnName)|double|
|getFloat(int columnIndex)|float|getFloat(String columnName)|float|
|getInt(int columnIndex)|int|getInt(String columnName)|int|
|getLong(int columnIndex)|long|getLong(String columnName)|long|
|getString(int columnIndex)|String|getString(String columnName)|String|

1. 通过结果集 `ResultSet` 对象调用 `getMetaData()` 方法返回一个 `ResultSetMetaData`对象。
2. 通过 `ResultSetMetaData` 对象，调用 `getColumnCount()` 方法返回结果集中列的数目。
3. 调用 `getColumnName(int i)` 方法返回结果集中第 i 列的名字。

### 随机查询

```java
Statement state = con.createStatement(int type, int concurrency);   // 获取一个滚动的结构及
ResultSet rs = state.executeQuery(SQL 语句);
```

type 的取值有：

- `Result.TYPE_FORWARD_ONLY`：结果集的游标只能向下滚动。
- `Result.TYPE_SCROLL_INSENSITIVE`：结果集的游标可以上下移动，当数据库变化时，当前结果集不变。
- `Result.TYPE_SCROLL_SENSITIVE`：返回可滚动的结果集，当数据库变化时，当前结果集同步改变。

concurrency 取值决定是否可以用结果集更新数据库：

- `Result.CONCUR_READ_ONLY`：不能用结果集更新数据库中的表。
- `Result.CONCUR_UPDATABLE`：能用结果集更新数据库中的表。

常用方法有：

- `public boolean previous()`：将游标向上移动。
	- 当移动到结果集第一行前面时返回 `false`。
- `public void beforeFirst()`：将游标移动到结果集的初始位置，即第一行之前。
- `public void afterLast()`：将游标移动到结果集的最后一行之后。
- `public void first()`：将游标移到结果集的第一行。
- `public void last()`：将游标移到及国际的最后一行。
- `public boolean isAfterLast()`：判断游标是否在最后一行之后。
- `public boolean isBeforeFirst()`：判断游标是否在第一行之前。
- `public boolean isFirst()`：判断游标是否指向结果集的第一行。
- `public boolean isLast()`：判断游标是否指向结果集的最后一行。
- `public int getRow()`：得到当前游标所指行的行号。
	- 行号从 1 开始，如果结果集没有行，返回0。
- `public boolean absolute(int row)`：将游标移到指定行号。
	- 行号允许取负值，即倒数的行数。

## 更新、添加与删除记录

通过 `public int executeUpdate(String sqlStatement)` 方法以及 SQL 语句进行更新、添加或删除。

## 用结果集操作数据库中的表

### 更新记录

```java
// 创建一个滚动的可更新的状态
Statement state = con.createStatement(Result.TYPE_SCROLL_SENSITIVE, Result.CONCUR_UPDATABLE);
// 得到执行 SQL 语句后的结果集
ResultSet rs = state.executeQuery(SQL 语句);
// 将游标移动到指定的行
rs.absolute(n);
// 调用下面方法更新数据
rs.updateInt(String columnName, int x); rs.updateInt(int columnIndex, int x);
rs.updateLong(String columnName, long x); rs.updateLong(int columnIndex, long x);
rs.updateDouble(String columnName, double x); rs.updateDouble(int columnIndex, double x);
rs.updateString(String columnName, String x); rs.updateString(int columnIndex, String x);
rs.updateBoolean(String columnName, boolean x); rs.updateBoolean(int columnIndex, boolean x);
rs.updateDate(String columnName, Date x); rs.updateDate(int columnIndex, Date x);
// 调用 updateRow() 更新到数据库
rs.updateRow();
```

### 插入记录

```java
// 将结果集的游标移动到插入行
rs.moveToInsertRow();
// 调用更新方法
rs.updateXxx();   // 上面提到的所有方法都适用
// 调用 insertRow() 插入到数据库
rs.insertRow();
```

## 预处理语句

```java
PreparedStatement pre = con.prepareStatement(String sql);
// 调用以下方法均可以使数据库执行
pre.executeQuery();
pre.execute();
pre.executeUpdate();
```

在对 SQL 进行预处理时可以使用通配符 `?` 来代替字段的值。

```java
PreparedStatement pre = con.prepareStatement("select * from pruduct where price < ? and price > ?");
pre.setDouble(1, 6565);    // 对第一个通配符设置字段
pre.setDouble(2, 1212);    // 对第二个通配符设置字段
```

常用方法有：

- `void setDate(int parameterIndex, Date x)`
- `void setDouble(int parameterIndex, double x)`
- `void setFloat(int parameterIndex, float x)`
- `void setInt(int parameterIndex, int x)`
- `void setLong(int parameterIndex, long x)`
- `void setString(int parameterIndex, string x)`

## 事务

1. 使用 `setAutoCommit(boolean autoCommit)` 方法关闭自动提交。
	- `con.setAutoCommit(false);`
2. Statement 对象对数据库提交的任何 SQL 语句操作都不会立即生效。
	- 直到连接对象调用 `commit()` 方法。
	- `con.commit();`
3. 在处理 `SQLException` 时必须让连接对象调用 `rollback()` 方法，撤销事务中执行过的 SQL 语句。
	- `con.rollback();`

## 分页显示记录

- 如果 m 除以 n 的余数大于 0，总页数等于 m 除以 n 的商加 1。
- 如果 m 除以 n 的余数等于 0，总页数等于 m 除以 n 的商。

`总页数 = (m%n) == 0 ? (m/n) : (m/n + 1)`
