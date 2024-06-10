+++
title = 'C#-字符串'
date = 2024-06-10T15:17:27+08:00
draft = false
+++
# 一、属性
`string`: 用`+`连接
```cs
string a = "你好";
Console.WriteLine(a[0]); \\ 输出: 你
Console.WriteLine(a.Length); \\ 输出: 2
```
# 二、方法
- `public static int Compare(string strA, string strB, [bool ignoreCase = false])`

    比较两个字符串,返回相对位置的整数

- `public static string Concat(string strA, string strB, [string strC, ...])`

    返回连接后的字符

- `public string Concats(string value)` 

    返回表示指定string对象是否出现在字符串中的值

- `public static string Copy(string str)`

    创建一个与指定字符串具有相同值的新字符串

- `public static string CopyTo(int sourceIndex, char[] destination, int destinationIndex, int count)` 

    从字符串指定位置开始复制指定数量的字符到字符数组中的指定位置

- `public string EndsWith(string value)`
    
    判断结尾是否匹配指定字符串

- `public string Equals(string value)`

    判断当前的字符串是否与指定的字符串相同

- `public static string Equals(string a, string b)`

    判断两个字符串相同

- `public static string Format(string format, Object arg0)`

    返回字符串中格式替换为指定字符串

- `public int IndexOf(char value, [int startIndex = 0])`/`public string IndexOf(string value, [int startIndex = 0])`
    
    返回字符串首次出现的索引(索引从0开始)

- `public string IndexOfAny(char[] anyOf, int startIndex = 0)`

    返回指定字符数组中任意字符在该实例中第一次出现的索引(索引从 0 开始)

- `public string Insert(int startIndex, string value)`
    
    返回指定的字符串被插入在当前字符串的指定索引位置的字符

- `public static bool IsNullOrEmpty( string value )`
    
    指示指定的字符串是否为null或者是否为一个空的字符串

- `public static string Join(string separator, string[] value [, int startIndex = 0, int count])`

    连接一个字符串数组中的所有元素,使用指定的分隔符分隔每个元素

- `public int LastIndexOf( char value )`/`public int LastIndexOf( string value )`

    返回索引值(指定字符/字符串在当前字符串中最后一次出现的索引位置(索引从0开始))

- `public string Remove(int startIndex [, int count])`
    返回字符串(当前字符串的指定位置开始移除指定数量的字符)

- `public string Replace(char oldChar, char newChar)`/`public string Replace(string oldValue, string newValue)`
    
    返回字符串(所有指定字符/字符串替换为另一个指定字符/字符串)

- `public string[] Split(params char[] separator)`

    返回一个字符串数组(包含当前的字符串中的子字符串,子字符串是使用指定的字符数组中的元素进行分隔的)

- `public string[] Split(char[] separator, int count)`

    返回一个字符串数组(包含当前的字符串中的子字符串,子字符串是使用指定的字符数组中的元素进行分隔的(int 参数指定要返回的子字符串的最大数目)

- `public bool StartsWith(string value)`

    判断字符串实例的开头是否匹配指定的字符串

- `public char[] ToCharArray([ int startIndex, int length ])`

    返回一个带有字符串中所有字符的字符数组(从指定的索引开始,直到指定的长度为止)

- `public string ToLower()`

    返回字符串(转换为小写)

- `public string ToUpper()`

    返回字符串(转换为大写)

- `public string Trim()`

    移除字符串中的所有前后空白字符
