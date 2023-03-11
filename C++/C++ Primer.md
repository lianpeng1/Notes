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
- 对象的生命周期：
  - 全局对象在程序启动时分配，结束时销毁。
  - 局部对象在进入程序块时创建，离开块时销毁。
  - 局部`static`对象在第一次使用前分配，在程序结束时销毁。
  - 动态分配对象：只能显式地被释放。

- 对象的内存位置：
  - **静态内存**用来保存局部`static`对象、类`static`对象、定义在任何函数之外的变量。
  - **栈内存**用来保存定义在函数内的非`static`对象。
  - **堆内存**，又称自由空间，用来存储**动态分配**的对象。

### 动态内存和智能指针
`new`  and  `delete`

**`shared_ptr` and `unique_ptr` 都支持的操作**:

| 操作 | 解释 |
|-----|-----|
| `shared_ptr<T> sp`<br> `unique_ptr<T> up` | 空智能指针，可以指向类型是`T`的对象 |
| `p` | 将`p`用作一个条件判断，若`p`指向一个对象，则为`true` |
| `*p` | 解引用`p`，获得它指向的对象。 |
| `p->mem` | 等价于`(*p).mem` |
| `p.get()` | 返回`p`中保存的指针，要小心使用，若智能指针释放了对象，返回的指针所指向的对象也就消失了。 |
| `swap(p, q)`<br>`p.swap(q)` | 交换`p`和`q`中的指针 |

**`shared_ptr`独有的操作**：

| 操作 | 解释 |
|-----|-----|
| `make_shared<T>(args)` | 返回一个`shared_ptr`，指向一个动态分配的类型为`T`的对象。使用`args`初始化此对象。 |
| `shared_ptr<T>p(q)` | `p`是`shared_ptr q`的拷贝；此操作会**递增**`q`中的计数器。`q`中的指针必须能转换为`T*` |
| `p = q` | `p`和`q`都是`shared_ptr`，所保存的指针必须能互相转换。此操作会**递减**`p`的引用计数，**递增**`q`的引用计数；若`p`的引用计数变为0，则将其管理的原内存释放。 |
| `p.unique()` | 若`p.use_count()`是1，返回`true`；否则返回`false` |
| `p.use_count()` | 返回与`p`共享对象的智能指针数量；可能很慢，主要用于调试。 |