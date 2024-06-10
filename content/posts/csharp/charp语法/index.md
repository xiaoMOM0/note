+++
title = 'C#-语法'
date = 2024-06-09T23:33:01+08:00
draft = false
+++

# 一、输出
```cs
Console.Write("Hello World!"); // 不换行
Console.WriteLine("Hello World!"); // 换行
```

# 二、变量
`type 变量 = 值;`

```cs
int a = 10; \\ 初始化
int b = 10, c; \\ 一次可以定义多个变量
```

## 类型(常用)
- bool(布尔型)
- byte(0~255)/sbyte(-128~127)
- short/int/long
- float/double
- char
- var(隐式声明)

### 数组
`type[] arrayName`
```cs
int[] a = new int[3]; //初始化
int[] b = {1, 2, 3}; //初始化
int[] c = new int[3] {1, 2, 3}; //初始化

/* 多维数组 */
int [,] d = new int[2,3] {
    {0, 1},
    {2, 3},
    {4, 5},
}

int val = d[0, 1]; // 访问
```
### 引用类型
引用类型是一个内存位置(多个变量可以指向一个内存位置)
- object(对象类型): 可分配任何类型(分配前进行类型转换)
- dynamic(动态类型): 可存储任何类型的值(和object相似,但运行时类型检查)
- [string](/posts/csharp/csharp字符串/) (字符串): (注: string为String的别名) (`@""`转义字符\\作普通字符对待,可任意换行)




### 可空类型
`?`使类型可赋值为`null`, `??`判断类型是否为`null`
```cs
int i; // 默认值0
int? j; // 默认值null

a = b ?? c; // 如果b为空,返回c
```

### sizeof方法
用于获得类型的大小

### 指针类型
同C指针

`type* 标识符`

例:
```cs
char* cptr;
```

# 三、类型转化
## 隐式类型转换
```cs
int a = 10;
long b = a; // 不需要显式转换
```
## 显式类型转换
```cs
long i = 10;
int j = (int)i; // 需要使用强制类型转换

int intValue = 3;
string strValue = intValue.ToString(); // int -> string
```

## 转换方法
- Convert.(ToDouble/ToInt16/ToInt32/ToInt64)
- ToBoolean/ToString
- ToByte/ToChar/ToDateTime/ToDecimal/ToSbyte/ToSingle/ToType
- ToUInt16/ToUInt32/ToUInt64

# 四、作用域
作用域通常由花括号`{}`定义的代码块来确定(类似rust)

# Tips
`typeof()` 返回类型, `&` 返回地址, `*` 变量的指针, `is` 判断是否为某一类型, `as` 强制转换(失则也不抛出错误)

# 五、判断
## if
```cs
if(boolean_expression_1)
{
    ...
} else if (boolean_expression_2)
{
    ...
} else
{
    ...
}
```

# 六、循环
## while 
```cs
while (condition)
{
    ...
}
```
## for
```cs
for (init; condition; increment) {
    ...
}

foreach (var item in collection) {
    ...
}
```
## 控制语句
- break: 终止循环
- continue: 跳过本轮循环

# 七、封装
封装可以方止对细节的访问
## 修饰符
- public: 所有对象都能访问
- internal: 同一个程序集对象能访问
- protected: 该对象及其子类才能访问
- private: 该对象本身才能访问
```cs
class Rect
{
    private double length;
    private double width;
    
    public void InitValue()
    {
        Console.WriteLine("请输入长度:");
        length = Convert.ToDouble(Console.ReadLine());
        Console.WriteLine("请输入宽度:");
        width = Convert.ToDouble(Console.ReadLine());
    }
}
```

# 八、方法
## 定义
```cs
<访问修饰符> <返回类型> <方法名称>(参数列表)
{
    ...
}
```

# 九、结构
```cs
struct name
{
    <访问修饰符> <返回类型> <字段名>;
    ...
};
```

# 十、类
```cs
<访问修饰符> class class_name
{
    // 成员变量
    <访问修饰符> <type> var1;
    <访问修饰符> <type> var2;
    ...
    // 成员方法
    <访问修饰符> <return type> method1(参数列表){
        ...
    }
}
```
- 访问修饰符: 类(默认 internal), 成员(默认 private)

```cs
class Box
{
    private int var;
    public Box()
    {
        Console.WriteLine("对象已创建");
    }

    ~Box // 析构函数
    {
        Console.WriteLine("对象已删除");
    }
}

```

## 静态成员
定义静态变量后,多个对象到只有同一个静态变量(静态函数在对象被创建之前就已经存在)

## 继承
```cs
<访问修饰符> class <基类>
{
    ...
}

class <派生类> : <基类>
{
    ...
}

```
派生类会继承基类(变量,方法), 通过`base`来调用基类的构造函数和方法
```cs

class <派生类> : <基类>
{
    pulic <派生类>(参数): base(传参)
    { }
    base.Method();
}

```
## 继承接口
```cs
using System;

// 定义一个基接口
interface BaseI
{
    void Method1();
}

// 定义一个派生接口, 继承自基接口
interface I : BaseI
{
    void Method2();
}

// 实现派生接口的类
class MyClass : I
{
    public void Method1()
    {
        Console.WriteLine("Method1 implementation");
    }

    public void Method2()
    {
        Console.WriteLine("Method2 implementation");
    }
}

...
MyClass obj = new MyClass();
obj.Method1(); // 调用继承自基接口的方法
obj.Method2(); // 调用派生接口新增的方法
```
> C#不支持多重继承, 只能用接口实现

## 多态
例1
```cs
public int Add(int a, int b, int c)
{

}

public int Add(int a, int b)
{

}

Console.WriteLine("add1:" + Add(1, 2));
Console.WriteLine("add2:" + Add(1, 2, 3));
```

例2
```cs

public int ToInt(int a)
{
    Console.WriteLine("已经是int");
    return a;
}

public int ToInt(float a)
{
    return (int)a;
}

```

## 类与结构
- 类: 适合复杂的对象和行为
    1. 支持继承和多态性
    2. 可以有无参数构造
    3. 可空
- 结构: 适合表示轻量级数据和值类型
    1. 提高性能和避免引用的管理开销
    2. 不可以无参数构造
    3. 不可空


# 十一、枚举
```cs
enum <enum_name>
{
    enumeration list
}
```

