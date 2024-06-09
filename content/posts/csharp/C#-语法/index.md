+++
title = 'C#-语法'
date = 2024-06-09T23:33:01+08:00
draft = false
+++
# syntax

## 一、输出
```cs
Console.Write("Hello World!"); // 不换行
Console.WriteLine("Hello World!"); // 换行
```

## 二、变量
`type 变量 = 值;`

```cs
int a = 10; \\ 初始化
int b = 10, c; \\ 一次可以定义多个变量
```

### 类型(常用)
- bool(布尔型)
- byte(0~255)/sbyte(-128~127)
- short/int/long
- float/double
- char
- var(隐式声明)

#### 引用类型
引用类型是一个内存位置(多个变量可以指向一个内存位置)
- object(对象类型): 可分配任何类型(分配前进行类型转换)
- dynamic(动态类型): 可存储任何类型的值(和object相似,但运行时类型检查)
- string(字符串): (注: string为String的别名) (`@""`转义字符\\作普通字符对待,可任意换行)

#### sizeof方法
用于获得类型的大小

#### 指针类型
同C指针

`type* 标识符`

例:
```cs
char* cptr;
```

## 三、类型转化
### 隐式类型转换
```cs
int a = 10;
long b = a; // 不需要显式转换
```
### 显式类型转换
```cs
long i = 10;
int j = (int)i; // 需要使用强制类型转换

int intValue = 3;
string strValue = intValue.ToString(); // int -> string
```

### 转换方法
- Convert.(ToDouble/ToInt16/ToInt32/ToInt64)
- ToBoolean/ToString
- ToByte/ToChar/ToDateTime/ToDecimal/ToSbyte/ToSingle/ToType
- ToUInt16/ToUInt32/ToUInt64

## 四、变量作用域
作用域通常由花括号`{}`定义的代码块来确定(类似rust)

## Tips
`typeof()` 返回类型, `&` 返回地址, `*` 变量的指针, `is` 判断是否为某一类型, `as` 强制转换(失则也不抛出错误)
