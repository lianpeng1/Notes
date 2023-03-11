---
html:
  toc: true
export_on_save:
  html: true
---

## Chapter 2. Variables and Basic Types
### 基本内置类型
**基本算数类型**：

| 类型 | 含义 | 最小尺寸|
|---|---|---|
| `bool` | 布尔类型  | 8bits |
| `char`| 字符 | 8bits |
| `wchar_t` | 宽字符 | 16bits |
| `char16_t` | Unicode字符 | 16bits |
| `char32_t` | Unicode字符 | 32bits |
| `short` | 短整型 | 16bits |
| `int` | 整型 | 16bits (在32位机器中是32bits) |
| `long` | 长整型 | 32bits |
| `long long` | 长整型 | 64bits （是在C++11中新定义的） |
| `float` | 单精度浮点数 | 6位有效数字 |
| `double` | 双精度浮点数 | 10位有效数字 |
| `long double` | 扩展精度浮点数 | 10位有效数字 |

### 如何选择类型
- 当数值不可能为负数时，选择无符号类型
- 使用`int`执行整数运算。一般`long`的大小和`int`一样，而`short`太小。如果超过了`int`的范围，则选择`long long`
- 算术表达式中不要使用`char`或`bool`
- 浮点运算使用`double`。`float`精度不够

### 类型转换
- 非布尔型赋给布尔型，初始值为0则结果为false，否则为true。
- 布尔型赋给非布尔型，初始值为false结果为0，初始值为true结果为1。


## Chapter 7. Classes
### 抽象数据类型
- 类背后的基本思想：**data abstraction** and **encapsulation**

#### 类成员
#### 类成员函数
#### 非成员函数
#### 构造函数
- 与类同名的成员函数。
- 构造函数放在类的`public`部分。

## Chapter 8. IO Library
- **cin**：一个`istream`对象，从标准输入读取数据。
- **cout**：一个`ostream`对象，向标准输出写入数据。
- **cerr**：一个`ostream`对象，向标准错误写入消息。
### IO 类
|头文件 | |
| ----------- | ----------- |
| `iostream` | 


## Chapter 12. Dynamic Memory
