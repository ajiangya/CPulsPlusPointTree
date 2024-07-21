[TOC]

# 总论

## 思维导图

思维导图见此链接 [https://s.shutu.cn/w/1ptl7l](https://s.shutu.cn/w/1ptl7l)

后续会做成图片或文件的形式放在这里。



# 1 基础

## 1.1 bit/B/KB

|      | 二进制说明                                                   |
| ---- | ------------------------------------------------------------ |
| b    | bit , 位, 比特, 比特位.                                      |
| B    | Byte字节, 1B=8bit, **sizeof返回值**                          |
| KB   | 千字节, kilobyte, 1KB = 1024B = 2^10B                        |
| MB   | 兆字节, 1MB = 1024KB = 2^10KB                                |
| GB   | 吉字节, 1GB = 1024MB = 2^10MB                                |
| TB   | 万亿字节, 太字节, 1TB = 1024GB = 2^10GB                      |
|      | 1 TB = 2^10 GB = 2^20 MB = 2^30 KB = 2^40 B                  |
|      | **b(bit) 常用于表示网络传输速率， B(Byte)常用于表示存储容量**。 |
| bit  | b, 数据传输速率: 单位时间内传输的比特数, bps, 比特每秒       |
| Byte | B, 存储容量: 计算机数据存储和处理的最小可寻址单元.           |

# 2 语法

## 2.1 杂项

### C++标准

| 发布时间 | 通称  | 说明          |
| -------- | ----- | ------------- |
| 2017     | C++17 | 第五个C++标准 |
| 2014     | C++14 | 第四个C++标准 |
| 2011     | C++11 | 第三个C++标准 |
| 2003     | C++03 | 第二个C++标准 |
| 1998     | C++98 | 第一个C++标准 |

### 命名空间

|      | 说明                                              |
| ---- | ------------------------------------------------- |
| 用途 | 命名空间(namespace)，防止同名冲突                 |
| 用法 | using namespace【命名空间】; 不推荐，可能发生冲突 |
|      | using【命名空间】::【变量名】                     |

### 面向对象与面向过程

编程范式中有:  面向过程编程和面向对象编程.

| 面向过程     | 面向过程编程说明                                             |
| ------------ | ------------------------------------------------------------ |
| **概念**     | 通过函数和过程组织代码.                                      |
| **优点**     | 简单/高效/模块化/线性的.                                     |
| **缺点**     | 扩展性差/数据安全性差/代码重复.                              |
| **应用场景** | 系统程序、嵌入式开发、小型脚本                               |
|              |                                                              |
| **面向对象** | **面向对象编程说明**                                         |
| **概念**     | 通过类和对象来组织代码                                       |
| **优点**     | 封装好/可扩展/易维护/抽象                                    |
| **缺点**     | 性能开销/复杂/过度设计                                       |
| **应用场景** | 大型软件系统、GUI应用、游戏开发、企业级应用系统              |
|              |                                                              |
| **抽象**     | 只展示必要信息, 隐藏不必要的细节                             |
| **封装**     | 指将数据(属性)和操作数据的方法(函数)封装在一个类中，保护私有数据 |
| **继承**     | 一个类(子类)继承另一个类(父类)的属性和方法，也称基类和派生类 |
| **多态**     | 通过基类指针或引用，来调用派生类的方法                       |


### 并行和并发

|                      | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| **并行**             | 同时进行, 多核, 独占CPU                                      |
| **并发**             | 交替执行, 共享CPU,                                           |
| **决定因素**         |                                                              |
| **硬件资源**         | 并行需要 多核处理器/多线程处理器等.                          |
| **操作系统调度策略** | 操作系统负责进程和线程的调度, 通过调度算法决定其执行顺序.    |
| **程序设计和编程**   | 通过合理的并行技术和并发技术来控制并行和并发. 如多线程编程/并行算法/并发数据结构的设计. |

### 进程和线程

|               | 说明                                                         |
| ------------- | ------------------------------------------------------------ |
| **进程**      | 一个程序实例, 具有独立的内存空间/代码/数据,                  |
| **线程**      | 进程内部的一条执行路径, 共享进程的代码和数据. 有独立的线程栈和寄存器上下文. |
|               |                                                              |
| **相同点**    | 用于执行任务的单元                                           |
|               | 具有**执行上下文**(寄存器+执行栈)和**资源**(文件+网络连接+内存等) |
|               | 可以被称作系统调度和管理                                     |
|               |                                                              |
| **差异点**    | 说明                                                         |
| **独立/共享** | 进程是独立实体, 具有独立的地址空间, 不同进程间不能直接访问数据. |
|               | 线程是进程的一部分, 共享地址空间, 同进程的不同线程可以直接访问数据. |
| **切换开销**  | 进程切换开销大, 线程开销小.                                  |
| **创建/销毁** | 进程的创建和销毁比线程慢, 需要**分配和释放资源**;            |
|               | 线程的创建和销毁相对较快, 因为共享进程的资源;                |
| **崩溃**      | 进程间相互独立, 崩溃互不影响;                                |
|               | 线程间共享相同资源, 某线程的错误可能导致整个进程的崩溃       |

### C++关键字

| asm              | else         | new                  | this         |
| ---------------- | ------------ | -------------------- | ------------ |
| auto             | enum         | operator             | throw        |
| bool             | **explicit** | private              | true         |
| break            | **export**   | protected            | try          |
| case             | extern       | public               | typedef      |
| catch            | false        | **register**         | **typeid**   |
| char             | float        | **reinterpret_cast** | **typename** |
| class            | for          | return               | union        |
| const            | friend       | short                | unsigned     |
| **const_cast**   | goto         | signed               | using        |
| continue         | if           | sizeof               | virtual      |
| default          | inline       | static               | void         |
| delete           | int          | **static_cast**      | **volatile** |
| do               | long         | struct               | wchar_t      |
| double           | **mutable**  | switch               | while        |
| **dynamic_cast** | namespace    | **template**         |              |

### 预处理

| 预处理指令         |                                                              |
| ------------------ | ------------------------------------------------------------ |
| #include           | 包含头文件                                                   |
| #define            | 定义宏                                                       |
| #undef             | 取消宏                                                       |
| #if                | 条件编译, **#ifdef #ifndef #else #elif #endif**              |
| #line              | 用于改变编译器报告的行号和文件名(不常用)                     |
| #error             | 用于在预处理阶段生成一个错误消息                             |
| #pragma            | 防止头文件重复包含                                           |
|                    |                                                              |
| **预处理运算符**   |                                                              |
| #                  | **字符串化运算符**,将宏参数转换为用双引号括起来的字符串字面量 |
| ##                 | **连接运算符**，连接两个标记以形成一个标记                   |
| ...                | 可变参数宏, 用的不多.                                        |
|                    |                                                              |
| **预处理变量**     |                                                              |
| **`__DATE__`**     | 程序被编译的日期, 格式为 "Mmm dd yyyy"                       |
| **`__TIME__`**     | 程序被编译的时间,格式为 "hh:mm:ss"                           |
| **`__FILE__`**     | 当前源代码文件的名称,字符串                                  |
| **`__LINE__`**     | 源代码文件中的当前行号,整型                                  |
| **`__func__`**     | 预定义的标识符, (C++11 引入), 当前函数的名称                 |
| **`__FUNCTION__`** | 函数名称                                                     |
| **`__cplusplus`**  | c++始终定义的宏, 表示编译的是c++代码                         |
| **`__VA_ARGS__`**  | 不是预定义, 在定义可变参数宏 时使用的一个特殊的标记符，用于表示可变参数列表 |

### 编译过程

| 阶段   | 说明                                 | linux         | win            |
| ------ | ------------------------------------ | ------------- | -------------- |
| 预处理 | **预处理指令处理**                   | .i, .cpp      | .i,.cpp        |
| 编译   | 将预处理后的代码**转化为汇编代码**   | .o            | .obj           |
| 汇编   | 将汇编代码**转化为机器码**           |               |                |
| 链接   | 将所有目标模块组合**生成可执行文件** | .so,.a,无后缀 | .dll,.lib,.exe |

以下是linux平台上参考的makefile

```
# 指定编译器
CC = g++

# 编译选项
CFLAGS = -Wall -Wextra

# 目标文件夹
BUILD_DIR = build

# 目标可执行文件名
TARGET = myprogram

# 源文件目录
SRC_DIR = src

# 头文件目录
INCLUDE_DIR = include

# 源文件列表
SRCS = $(wildcard $(SRC_DIR)/*.cpp)
# 源文件列表 如果存在多级子目录的情况, 可以使用如下find命令来获取
#SRCS := $(shell find $(SRC_DIR) -name '*.cpp')

# 将源文件列表转换成对应的目标文件列表
OBJS = $(patsubst $(SRC_DIR)/%.cpp,$(BUILD_DIR)/%.o,$(SRCS))

# 动态库文件列表
LDFLAGS_DYNAMIC = -L/path/to/dynamic_lib1 -ldynamic_lib1 -L/path/to/dynamic_lib2 -ldynamic_lib2

# 静态库文件列表
LDFLAGS_STATIC = -L/path/to/static_lib1 -lstatic_lib1 -L/path/to/static_lib2 -lstatic_lib2 -L/path/to/static_lib3 -lstatic_lib3

# 默认目标，编译可执行文件
all: $(BUILD_DIR) $(TARGET)

# 创建目标文件夹
$(BUILD_DIR):
	mkdir -p $(BUILD_DIR)

# 编译目标可执行文件
$(TARGET): $(OBJS)
	$(CC) $(CFLAGS) $(OBJS) $(LDFLAGS_DYNAMIC) $(LDFLAGS_STATIC) -o $(TARGET)

# 编译源文件为目标文件
$(BUILD_DIR)/%.o: $(SRC_DIR)/%.cpp
	$(CC) $(CFLAGS) -I$(INCLUDE_DIR) -c $< -o $@

# 清理生成的目标文件和可执行文件
clean:
	rm -rf $(BUILD_DIR) $(TARGET)
```

以下是linux平台生成动态库和静态库的makefile示例

```
# 指定编译器
CC = g++

# 编译选项
CFLAGS = -Wall -Wextra -fPIC

# 目标文件夹
BUILD_DIR = build

# 目标文件名
TARGET = libmylibrary

# 头文件目录
INCLUDE_DIR = include

# 源文件目录
SRC_DIR = src

# 源文件列表
SRCS := $(wildcard $(SRC_DIR)/*.cpp)
# 源文件列表 如果存在多级子目录的情况, 可以使用如下find命令来获取
#SRCS := $(shell find $(SRC_DIR) -name '*.cpp')

# 将源文件列表转换成对应的目标文件列表
OBJS := $(patsubst $(SRC_DIR)/%.cpp,$(BUILD_DIR)/%.o,$(SRCS))

# 动态库文件
LIB_DYNAMIC = $(TARGET).so

# 静态库文件
LIB_STATIC = $(TARGET).a

# 默认目标，编译动态库和静态库
all: $(BUILD_DIR) $(LIB_DYNAMIC) $(LIB_STATIC)

# 创建目标文件夹
$(BUILD_DIR):
	mkdir -p $(BUILD_DIR)

# 编译动态库
$(LIB_DYNAMIC): $(OBJS)
	$(CC) $(CFLAGS) -shared $(OBJS) -o $@

# 编译静态库
$(LIB_STATIC): $(OBJS)
	ar rcs $@ $(OBJS)

# 编译源文件为目标文件
$(BUILD_DIR)/%.o: $(SRC_DIR)/%.cpp
	$(CC) $(CFLAGS) -I$(INCLUDE_DIR) -c $< -o $@

# 清理生成的目标文件和库文件
clean:
	rm -rf $(BUILD_DIR) $(LIB_DYNAMIC) $(LIB_STATIC)
```



## 2.2 数据类型

### 声明与定义

|      | 含义                                |
| ---- | ----------------------------------- |
| 声明 | 声明类型和名字, extern声明，        |
| 定义 | 声明类型和名字, 并**分配存储空间**. |

### 变量命名规则

|      | c++变量命名规则如下                                          |
| ---- | ------------------------------------------------------------ |
| 1    | **字母、数字和下划线**：变量名只能包含字母(a-z, A-Z)、数字(0-9)和下划线(_)。 |
| 2    | **不能以数字开头**：变量名不能以数字开头，但可以以字母或下划线开头。 |
| 3    | **区分大小写**：C++是区分大小写的语言，因此`variable`、`Variable`和`VARIABLE`是三个不同的变量名。 |
| 4    | **不能是关键字**：变量名不能是C++的保留关键字，如`int`、`for`、`while`等。 |
| 5    | **无特殊字符**：除了下划线(_)外，不能使用其他特殊字符(如`@`、`#`、`$`等)来命名变量。 |
| 6    | **无空格**：变量名中不能包含空格。                           |


### 基础类型

| 基础类型        | linux32(Byte) | linux64 | win32 | win64 |
| --------------- | ------------- | ------- | ----- | ----- |
| bool            | 1             | 1       | 1     |       |
| char            | 1             | 1       | 1     |       |
| short           | 2             | 2       | 2     |       |
| int             | 4             | 4       | 4     |       |
| **long**        | **4**         | **8**   | 4     |       |
| long long       | 8             | 8       | 4     |       |
| float           | 4             | 4       | 4     |       |
| double          | 8             | 8       | 8     |       |
| **long double** | **12**        | **16**  |       |       |
| **pointer ***   | **4**         | **8**   | 4     |       |

### 固定类型+修饰符+字面值+转移字符

| 固定大小类型               | 头文件 cstdint                           |
| -------------------------- | ---------------------------------------- |
| int8_t/uint8_t             |                                          |
| int16_t/uint16_t           |                                          |
| int32_t/uint32_t           |                                          |
| int64_t/uint64_t           |                                          |
| **intptr_t**/**uintptr_t** | **大小取决于平台, 在特定平台上是固定的** |
|                            |                                          |
| **修饰符**                 | **说明**                                 |
| signed                     | 有符号                                   |
| unsigned                   | 无符号                                   |
| void                       | 空类型                                   |
|                            |                                          |
| **整型字面值常量**         |                                          |
| 20                         | 十进制                                   |
| 024                        | 八进制                                   |
| 0x14                       | 十六进制                                 |
|                            |                                          |
| **浮点型字面值常量**       |                                          |
| 3.14159                    |                                          |
| 3.14159E0                  | e/E:科学计数法                           |
| 'a'                        | 字符常量                                 |
| "hello world"              | 字符串常量                               |
|                            |                                          |
| **类型转换**               |                                          |
| 非布尔>>bool               | 0->false, 其他->true                     |
| bool>>非bool               | false->0, true->1                        |
| 浮点型->整型               | 近似处理, 只保留整型                     |
| 整型->浮点型               | 小数部分记作0,可能存在精度损失           |
| 无符号类型赋**超限值**     | 取模后的余数                             |
| 有符号类型赋**超限值**     | 结果未定义                               |
|                            |                                          |
| **指定字面值的类型**       |                                          |
| **前缀**                   | **字符/字符串**                          |
| u                          | char16_t, unicode16字符                  |
| U                          | char32_t, unicode32字符                  |
| L                          | wchar_t, 宽字符                          |
| u8                         | char, UTF-8                              |
| **后缀**                   | **整型字面值**                           |
| u/U                        | unsigned                                 |
| l/L                        | long                                     |
| ll/LL                      | long long                                |
| **后缀**                   | **浮点型字面值**                         |
| f/F                        | float                                    |
| l/L                        | long double                              |
|                            |                                          |


| 转义字符  |              |              |           |               |        |
| --------- | ------------ | ------------ | --------- | ------------- | ------ |
| 换行符\n  | 横向制表符\t | 纵向制表符\v | 反斜线\\\ | 回车符\r      | 问号\? |
| 单引号\\' | 双引号\\"    | 退格符\b     | 进纸符\f  | 报警/响铃符\a |        |

## 2.3  派生类型

### 数组

```
整型数组的静态初始化、部分初始化、省略大小
int arr1[5] = {1, 2, 3, 4, 5}; // 声明并初始化一个包含5个元素的数组
int arr2[5] = {1, 2}; // 剩余元素自动初始化为0
int arr3[] = {1, 2, 3, 4, 5}; // 编译器自动确定数组大小

字符数组的静态初始化、字符串初始化
char charArray1[6] = {'H', 'e', 'l', 'l', 'o', '\0'}; // 包含空字符
char charArray2[] = "Hello"; // 自动添加空字符

字符串数组的静态初始化、部分初始化、省略大小
char strArray1[3][10] = {"Hello", "World", "C++"};
char strArray2[3][10] = {"Hello", "World"} // 第三个字符串自动初始化为空字符串
char strArray3[][10] = {"Hello", "World", "C++"};// 自动确定第一维大小

const类型的字符串数组初始化
const char* strArray1[3] = {"Hello", "World", "C++"};

使用 std::string 数组表示的二维字符串时, 期静态初始化/部分初始化/省略大小
std::string strArray1[3] = {"Hello", "World", "C++"};
std::string strArray2[3] = {"Hello", "World"} // 第三个字符串自动初始化为空字符串
std::string strArray3[] = {"Hello", "World", "C++"};// 自动确定数组大小


数组的长度
int length = sizeof(arr) / sizeof(arr[0]); // 计算数组长度

多维数组
int matrix[3][4] = {{1, 2, 3, 4}, {5, 6, 7, 8}, {9, 10, 11, 12}}; // 二维整型数组
```

### 指针

```
//空指针
NULL //传统的 C 风格空指针常量, <cstddef> 不推荐使用, 可能引起类型安全问题
nullptr //c++11引入, 类型安全
0 //不推荐

//普通指针：
int var = 10; // 声明一个整型变量  
int *ptr; // 声明一个整型指针变量
ptr = &var; // 将var的地址赋给ptr指针
int value = *ptr; // 通过指针访问变量的值

//指向指针的指针：
int x = 10; // 声明一个整型变量  
int *p = &x; // 声明一个整型指针变量，并将x的地址赋给它  
int **pp = &p; // 声明一个整型指向指针的指针变量，并将p的地址赋给它 
```

### struct

```
声明
struct Person {  
    std::string name;  
    int age;
    Person()
    {
    	name="";
    	age=0;
    }
};  

定义:
struct Student
{
    int Code;
    char Name[20];
    char Sex;
    int Age;
}Stu,StuArray[10],*pStu;

初始化: 列表初始化/构造初始化/直接成员初始化
Person p = {"Alice", 25};//c++11, 列表初始化
Person p1; // 默认构造函数
Person p2;p2.name = "LiSi";p2.age = 8;//直接成员初始化
```

### enum

|      | enum的枚举值的特点         |
| ---- | -------------------------- |
| 1    | 指定值时可以按照顺序       |
| 2    | 可以为负数                 |
| 3    | 自动递增, 从0开始/显式指定 |
| 4    | 指定和不指定可混合使用     |
| 5    | 枚举值可重复**不推荐**     |


```
// 默认从0开始 依次递增1
enum Color {  
    RED,  
    GREEN,  
    BLUE  
};  

// 直接指定值
enum error{
	error_1 = 0,
	error_2 = -1,
	error_3 =-3,
}

强类型枚举的作用域和类型安全
enum class Animal {
    Dog = 1,
    Cat = -1,
    Bird = 2
};
使用
Animal myPet = Animal::Dog;
```

### union

可以在**同一块内存位置**存储**不同**的数据类型, 任意一时间**只能存储一种**，类型长度以**最长**的为准

```
//声明
union MyUnion {
    int i;
    float f;
    char c;
};

使用初始化列表(C++11 引入)
MyUnion u = {42}; // 初始化 `i` 成员

使用匿名联合体初始化
union {
    int i;
    float f;
    char c;
} u = {42}; // 初始化 `i` 成员

初始化特定成员(使用 C++17 引入的聚合初始化)
MyUnion u = {.f = 3.14f}; // 初始化 `f` 成员
```

```
#include <iostream>  
  
union DataType {  
    int integer;  
    float floatValue;  
    char character;  
};  
  
int main() {  
    DataType data;  
  
    // 存储整数  
    data.integer = 10;  
    std::cout << "Integer: " << data.integer << std::endl;  
  
    // 存储浮点数  
    data.floatValue = 3.14f;  
    std::cout << "Float: " << data.floatValue << std::endl;  
  
    // 存储字符  
    data.character = 'A';  
    std::cout << "Character: " << data.character << std::endl;  
  
    return 0;  
}
```

### 位域

```
struct BitField {  
    unsigned int field1 : 5;  // 使用5位存储数据  
    unsigned int field2 : 3;  // 使用3位存储数据  
    unsigned int field3 : 2;  // 使用2位存储数据  
};  
```

### typedef 

为现有数据类型创建别名, 使代码简洁便于理解.

1.**基本数据类型**：

```cpp
typedef int Integer;  
typedef double Float;
```

2.**指针**：

```cpp
typedef int* IntPtr;  
typedef double* PtrToDouble;
```

3.**结构体**：

```cpp
typedef struct Point {  
    int x, y;  
}Point;  

typedef struct Point Point;// 定义Point为Point结构的别名
```

4.**数组**：

```cpp
typedef int Array[5];// 定义Array为包含5个整数的数组类型别名
```

5.**函数指针**：

```cpp
typedef int (*func_ptr)(int);// 定义func_ptr为指向接受一个整数参数并返回整数的函数的指针类型别名
```

6.**联合体**：

```cpp
typedef union MyUnion{  
    int a;  
    float b;  
} MyUnion;  // 定义MyUnion为union类型的别名
```

7.**枚举**

```
typedef enum Color {  
    RED, GREEN, BLUE  
}Color;  
  
typedef enum Color Color;  // 定义Color为enum Color的别名  
```

## 2.4 类型关联

### 指针和函数

|              | 说明：                                                   |
| ------------ | -------------------------------------------------------- |
| 函数**指针** | 本质是**指针**, 指向函数的指针, 可通过它调用函数, ()强调 |
| 指针**函数** | 本质是**函数**, 返回类型是指针,                          |

函数指针用法

```
返回类型 (*函数指针名称)(参数列表);
int (*funcPtr)(int, int);
int result = (*funcPtr)(2, 3);  // 调用 add 函数，并将结果存储在 result 中
```

指针函数用法

```
返回类型 *函数名称(参数列表);
int *getIntPtr(int x);
int *ptr = getIntPtr(5);  // 获取指向整数的指针  
int value = *ptr;  // 通过指针访问整数值
```

函数指针代码示例：

```
#include <iostream>

// 声明一个函数指针类型
typedef void (*FunctionPointer)(int);

// 定义函数 foo，参数为 int，无返回值
void foo(int x) {
    std::cout << "foo: " << x << std::endl;
}

// 定义函数 bar，参数为 int，无返回值
void bar(int x) {
    std::cout << "bar: " << x << std::endl;
}

int main() {
    // 声明函数指针变量并初始化为指向 foo 函数
    FunctionPointer ptr = foo;

    // 使用函数指针调用 foo 函数
    ptr(10); // 输出：foo: 10

    // 将函数指针指向 bar 函数
    ptr = bar;

    // 使用函数指针调用 bar 函数
    ptr(20); // 输出：bar: 20

    return 0;
}
```

指针函数代码示例：

```
#include <iostream>

// 定义一个指针函数，返回一个函数指针
void (*getFunctionPointer(int choice))(int) {
    if (choice == 1) {
        return foo;
    } else {
        return bar;
    }
}

// 定义函数 foo，参数为 int，无返回值
void foo(int x) {
    std::cout << "foo: " << x << std::endl;
}

// 定义函数 bar，参数为 int，无返回值
void bar(int x) {
    std::cout << "bar: " << x << std::endl;
}

int main() {
    // 声明一个函数指针变量
    void (*ptr)(int);

    // 调用指针函数，获取函数指针并赋值给 ptr
    ptr = getFunctionPointer(1);

    // 使用函数指针调用 foo 函数
    ptr(10); // 输出：foo: 10

    // 调用指针函数，获取另一个函数指针并赋值给 ptr
    ptr = getFunctionPointer(2);

    // 使用函数指针调用 bar 函数
    ptr(20); // 输出：bar: 20

    return 0;
}
```

### 指针和数组

|                      | 说明：                                     |
| -------------------- | ------------------------------------------ |
| 指针**数组**         | 本质上是**数组**, 元素是指针.              |
| 数组**指针(行指针)** | 本质上是**指针**, 指向数组，常用于多维数组 |

指针**数组**的用法

```
int *arr[5];  // 定义一个包含5个整型指针的指针数组
int a = 10, b = 20;  
//赋值
arr[0] = &a;  // 将变量a的地址存储在arr[0]中  
arr[1] = &b;  // 将变量b的地址存储在arr[1]中
//修改值
*arr[0] = 30;  // 修改a的值为30  
*arr[1] = 40;  // 修改b的值为40
```

数组**指针**的用法

```
int arr[5] = {1, 2, 3, 4, 5};  
int (*ptr)[5] = &arr;  // 定义一个指向包含5个整数的数组的指针

(*ptr)[0] = 10;  // 修改数组arr的第1个元素为10  
(*ptr)[4] = 50;  // 修改数组arr的第5个元素为50

ptr->[0] = 10;  // 修改数组arr的第1个元素为10  
ptr->[4] = 50;  // 修改数组arr的第5个元素为50
```

指针数组代码示例：

```
#include <iostream>

int main() {
    // 定义一个指针数组，每个元素是指向 int 的指针
    int* arr[3];

    // 定义一些 int 变量
    int a = 10, b = 20, c = 30;

    // 将指针数组的元素指向不同的 int 变量
    arr[0] = &a;
    arr[1] = &b;
    arr[2] = &c;

    // 使用指针数组访问和修改变量
    std::cout << "*arr[0] = " << *arr[0] << std::endl; // 输出：10
    std::cout << "*arr[1] = " << *arr[1] << std::endl; // 输出：20
    std::cout << "*arr[2] = " << *arr[2] << std::endl; // 输出：30

    // 可以通过循环遍历指针数组
    for (int i = 0; i < 3; ++i) {
        std::cout << "arr[" << i << "] = " << *arr[i] << std::endl;
    }

    return 0;
}
```

数组指针代码示例：

```
#include <iostream>

int main() {
    // 定义一个数组
    int arr[3] = {10, 20, 30};

    // 定义一个指向数组的指针
    int (*ptr)[3] = &arr;

    // 使用数组指针访问数组的元素
    std::cout << "(*ptr)[0] = " << (*ptr)[0] << std::endl; // 输出：10
    std::cout << "(*ptr)[1] = " << (*ptr)[1] << std::endl; // 输出：20
    std::cout << "(*ptr)[2] = " << (*ptr)[2] << std::endl; // 输出：30

    // 也可以直接使用指针语法访问数组元素
    std::cout << "ptr[0][0] = " << ptr[0][0] << std::endl; // 输出：10
    std::cout << "ptr[0][1] = " << ptr[0][1] << std::endl; // 输出：20
    std::cout << "ptr[0][2] = " << ptr[0][2] << std::endl; // 输出：30

    return 0;
}
```

### 指针和const

|                  | 说明：                                                       |
| ---------------- | ------------------------------------------------------------ |
| 指针**常量**     | 本质是**常量**, 指针类型的常量, 指向不可修改, 指向的值可以修改. |
| 常量**指针**     | 本质是**指针**, 指向常量; 指向可修改, 指向的值不可修改.      |
| 指向常量的常指针 | 指针和指向都是常量                                           |
| **写法根本**     | **const靠右修饰原则**                                        |

```
//**指针常量的用法**
int x = 10;  
int * const ptr = &x;  
// *ptr = 20;  // 这是合法的，会改变x的值为20  
// ptr++;      // 这是非法的，因为ptr是一个常指针

//**常量指针的用法**
int x = 10;  
const int * ptr = &x;  
int const * ptr = &x;
// *ptr = 20;  // 这是非法的，因为ptr指向一个常量  
// ptr++;      // 这是合法的，因为ptr本身不是常量


//**指向常量的常指针**
int x = 10;  
const int * const ptr = &x;  
// *ptr = 20;  // 这是非法的，因为ptr指向一个常量  
// ptr++;      // 这也是非法的，因为ptr本身是一个常量指针
```

### 指针和引用

|      | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| 指针 | 类型, 可定义变量/初始化/赋值/解引用/算术运算, 有空值/类型检查 |
| 引用 | 类型别名, 声明时必须初始化, 不可改变指向. 避免拷贝           |

### define,typedef,函数,inline,const

|          | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| #define  | 预处理指令,只替换,不求解,无作用域,无优先级,无安全检查,内存开销大, 不便于调试, |
| typedef  | 类型别名, 有类型安全, 便于阅读和维护                         |
| 函数     | 有作用域, 类型安全, 好调试追踪, 好传参                       |
| inline   | 有作用域, 编译时处理, 类型安全, 便于调试,                    |
| const    | 有作用域, 编译时处理, 类型安全, 便于调试                     |
| **建议** | 使用typedef,函数,inline,const                                |

### struct 和 class

| 说明         | struct   | class    |
| ------------ | -------- | -------- |
| 默认访问权限 | public   | private  |
| 继承方式     | public   | private  |
| 通常用法     | 表示数据 | 表示行为 |

## 2.5 限定符

### 限定符


| 限定符类型    | 引入标准 | 用途                                                      |
| ------------- | -------- | --------------------------------------------------------- |
| **类型**      |          |                                                           |
| const         | C++98    | 表示变量的值不可修改                                      |
| volatile      | C++98    | 提示编译器变量可能会被外部因素修改，避免优化              |
| mutable       | C++98    | 允许**常量成员函数修改类成员变量**                        |
| restrict      | C++20    | 用于指针，提示编译器该指针是访问对象的唯一方式            |
| **存储类**    |          |                                                           |
| static        | C++98    | 表示变量在文件作用域或函数作用域内静态存储                |
| extern        | C++98    | 声明变量或函数在其他文件中定义                            |
| thread_local  | C++11    | 声明每个线程都有自己实例的变量                            |
| register      | C++98    | **C++17弃用**, 提示编译器将变量存储在寄存器中而不是内存中 |
| **函数**      |          |                                                           |
| inline        | C++98    | 提示编译器将函数扩展内联，减少函数调用开销                |
| **constexpr** | C++11    | 表明表达式/函数/构造函数为常量表达式,指示在编译时求值,    |
| **noexcept**  | C++11    | 指定函数不抛出异常                                        |
| virtual       | C++98    | 声明虚函数，允许在派生类中重写                            |
| **explicit**  | C++98    | **防止隐式转换或复制构造函数的自动调用**                  |
| friend        | C++98    | 声明函数或类可以访问类的私有和受保护成员                  |
| **default**   | C++11    | **显式声明默认的构造/析构/拷贝/移动操作 函数**            |
| **delete**    | C++11    | 显式**禁止某些函数的自动生成**                            |
| **final**     | C++11    | 表示类或虚函数**不能被继承或重写**                        |
| **override**  | C++11    | 表示**覆盖**基类中的虚函数                                |
| **访问控制**  |          |                                                           |
| public        | C++98    | 成员可以被任何代码访问                                    |
| protected     | C++98    | 成员只能被该类和其派生类访问                              |
| private       | C++98    | 成员只能被该类访问                                        |
| **其他**      |          |                                                           |
| alignas       | C++11    | 指定变量或类型的对齐要求                                  |
| alignof       | C++11    | 查询类型或变量的对齐要求                                  |
| decltype      | C++11    | 获取表达式的类型                                          |


### static

|                | 说明                                                       |
| -------------- | ---------------------------------------------------------- |
| static局部变量 | 代码块可见                                                 |
| static全局变量 | 本文件可见                                                 |
| static全局函数 | 本文件可见                                                 |
| static成员变量 | 类内定义, 类外初始化, 可类名::直接访问, 所有类对象共享一份 |
| static成员函数 | 可类名::直接访问, 只能访问静态成员变量和静态成员函数,      |

```
void foo() {  
    static int count = 0; // 静态局部变量，只初始化一次，程序结束时销毁  
    count++;  
}  

static int global_var = 42; // 静态全局变量，只在定义它的文件中可见  

static void bar() { /* ... */ } // 静态全局函数，同样只在定义它的文件中可见
```

### extern

```
// file1.cpp  
int global_var = 42; // 定义全局变量  

// file2.cpp  
extern int global_var; // 声明全局变量，表示它在其他地方定义  

void use_global() {  
    int local = global_var;  
    // ...  
}
```

### thread_local

```
#include <iostream>
#include <thread>

thread_local int myVar;  // 声明一个具有线程局部存储的变量

void foo() {
    myVar = 5;  // 在每个线程中设置不同的值
    std::cout << "Thread ID: " << std::this_thread::get_id() << ", myVar: " << myVar << std::endl;
}

int main() {
    std::thread t1(foo);
    std::thread t2(foo);
    t1.join();
    t2.join();
    return 0;
}
```

### alignas

```
#include <iostream>
#include <cstdint>

struct alignas(16) MyStruct {
    char a;
    int32_t b;
};

int main() {
    std::cout << alignof(MyStruct) << std::endl; // 输出MyStruct类型的对齐要求
    return 0;
}
```

### alignof

```
#include <iostream>
#include <cstdlib>

int main() {
    std::cout << alignof(int) << std::endl; // 输出int类型的对齐要求
    return 0;
}
```

### decltype

```
#include <iostream>
#include <typeinfo>

int main() {
    int x = 5;
    decltype(x) y; // 推断y的类型和x相同
    std::cout << typeid(y).name() << std::endl; // 输出y的类型名称
    return 0;
}
```

### noexcept

```
#include <iostream>

void func() noexcept {
    // 函数体
}

int main() {
    std::cout << noexcept(func()) << std::endl; // 输出函数是否会抛出异常
    return 0;
}
```

### constexpr

```
constexpr int square(int x) {
    return x * x;
}

int main() {
    constexpr int value = square(5);
    return 0;
}
```



## 2.6 运算符

以下是C++中所有运算符的分类和符号，以表格格式列出：

| 类型             | 符号                                                         |
| ---------------- | ------------------------------------------------------------ |
| 算术             | + (加), - (减), * (乘), / (除), % (取模)                     |
| 关系             | == (等于), != (不等于), > (大于), < (小于), >= (大于等于), <= (小于等于) |
| 逻辑             | && (逻辑与), \|\|(逻辑或), !(逻辑非)                         |
| 位               | & (按位与), \| (按位或), ^ (按位异或), ~ (按位取反), << (左移), >> (右移) |
| 赋值             | = (赋值), += (加后赋值), -= (减后赋值), *= (乘后赋值), /= (除后赋值), |
|                  | %= (取模后赋值), &= (按位与后赋值), \|= (按位或后赋值),      |
|                  | ^= (按位异或后赋值), <<= (左移后赋值), >>= (右移后赋值),     |
| 增减             | ++ (递增), -- (递减)                                         |
| 条件             | ? : (条件运算符)                                             |
| 成员访问         | . (成员访问), -> (成员指针访问)                              |
| 数组访问         | [] (数组下标)                                                |
| 指针             | * (指针), & (取地址)                                         |
| sizeof           | sizeof (求类型或变量长度)                                    |
| 类型转换         | static_cast, dynamic_cast, const_cast, reinterpret_cast      |
| 其他             | , (逗号), typeid, noexcept, alignof, decltype,               |
|  |  |
| **运算符**       | **说明**                                                     |
| ,                | 逗号, 按顺序执行, 并返回最后一个表达式的值, 优先级低, 最后执行 |
| **typeid**       | 返回表达式或类型的类型信息对象                               |
| **noexcept**     | 异常说明运算符, 判断表达式在执行时是否不抛出异常, [示例](#noexcept) |
| **alignof**      | 对齐要求运算符, 返回类型的对齐要求, [示例](#alignof)          |
| **decltype**     | 推导表达式的类型, [示例](#decltype)                    |
|                  |                                                              |
| static_cast      | 基础类型转换, 指针与引用转换, 基类与派生类转换(**无**运行时检查) |
| dynamic_cast     | **基类**指针/引用转换为**派生类**指针/引用, **有运行时类型检查**, 失败返回空指针 |
| const_cast       | 添加或移除类型的`const`或`volatile`限定符                    |
| reinterpret_cast | 不同类型**指针间转换**, **整型转指针**, **无类型检查**       |

### 逗号表达式

```
#include <iostream>

int main() {
    int a = 1, b = 2, c = 3;
    
    // 逗号表达式，返回最后一个表达式的值
    int result = (a += 10, b += 5, c += 3);
    
    std::cout << "a = " << a << std::endl; // 输出：a = 11
    std::cout << "b = " << b << std::endl; // 输出：b = 7
    std::cout << "c = " << c << std::endl; // 输出：c = 6
    std::cout << "result = " << result << std::endl; // 输出：result = 6
    
    return 0;
}
```

### 强制类型转换

static_cast用法

```
int i = 42;  
double d = static_cast<double>(i); // int到double的转换  

Base* basePtr = new Derived(); // 假设Base是基类，Derived是派生类  
Derived* derivedPtr = static_cast<Derived*>(basePtr); // 没有运行时类型检查
```

dynamic_cast

```
Base* basePtr = new Derived(); // 假设Base是基类，Derived是派生类  
Derived* derivedPtr = dynamic_cast<Derived*>(basePtr); // 运行时类型检查  
if (derivedPtr != nullptr) {  
    // 转换成功  
} else {  
    // 转换失败  
}
```

const_cast

```
const int i = 42;  
int* p = const_cast<int*>(&i); // 移除const限定符(不安全)  

volatile int v;  
int& ref = const_cast<int&>(v); // 移除volatile限定符
```

reinterpret_cast

```
int i = 42;  
int* pInt = &i;  
char* pChar = reinterpret_cast<char*>(pInt); // int*到char*的转换  

void* pVoid = &i;  
int& ref = *reinterpret_cast<int*>(pVoid); // void*到int&的转换
```

### typeid

```
#include <iostream>
#include <typeinfo>

int main() {
    int x = 5;
    const std::type_info& typeInfo = typeid(x);
    std::cout << typeInfo.name() << std::endl; // 输出变量类型的名称
    return 0;
}
```



## 2.7 语句

### 循环

|          | 说明                  |
| -------- | --------------------- |
| 循环语句 | for, while, do while  |
| 控制语句 | break, continue, goto |

```
#include <iostream>  
using namespace std;  
  
int main() {  
    for (int i = 0; i < 5; i++) {  
        cout << i << " ";  
    }  
    return 0;  
}  
// 输出：0 1 2 3 4
```

```
#include <iostream>  
using namespace std;  
  
int main() {  
    int i = 0;  
    while (i < 5) {  
        cout << i << " ";  
        i++;  
    }  
    return 0;  
}  
// 输出：0 1 2 3 4
```

```
#include <iostream>  
using namespace std;  
  
int main() {  
    int i = 0;  
    do {  
        cout << i << " ";  
        i++;  
    } while (i < 5);  
    return 0;  
}  
// 输出：0 1 2 3 4
```

```
do
{
	//编程技巧,用于多次返回的地方, 好统一处理.
	
}while(0);
```

### 条件

|        | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| if     | if,else if, else                                             |
| switch | switch, case, break, default. 只能用于整型/枚举值            |
|        |                                                              |
| switch | **switch使用注意事项**                                       |
|        | switch必须是整型表达式， case必须是整型                      |
|        | 不允许有重复的case标签                                       |
|        | 缺少break的影响，会穿透到下一个case/default分支，导致意外行为。 |
|        | 不能在case标签中申明变量                                     |

```
#include <iostream>  
using namespace std;  
  
int main() {  
    int number = 2;  
    switch (number) {  
        case 1:  
            cout << "Number is 1." << endl;  
            break;  
        case 2:  
            cout << "Number is 2." << endl;  
            break;  
        default:  
            cout << "Number is not 1 or 2." << endl;  
    }  
    return 0;  
}  
// 输出：Number is 2.
```

```
#include <iostream>  
using namespace std;  
  
int main() {  
    int value = 2;  
  
    switch (value) {  
        case 1:  
            cout << "Value is 1" << endl;  
            // 注意：这里没有 break 语句  
        case 2:  
            cout << "Value is 2" << endl;  
            // 注意：这里也没有 break 语句  
        case 3:  
            cout << "Value is 3" << endl;  
            // 注意：这里依然没有 break 语句  
        default:  
            cout << "Value is something else" << endl;  
    }  
  
    return 0;  
}

输出
Value is 2  
Value is 3  
Value is something else
```

## 2.8 函数

### 传参

| 参数传递   | 说明+用途+差异                                               |
| ---------- | ------------------------------------------------------------ |
| 传值       | 传递拷贝**副本**，函数内部修改**不影响原值**， **大对象复制性能开销大**。 |
| 传引用     | 函数内部修改会**影响原值**，适用于需要**修改原值或避免大对象的复制**。 |
| 传指针     | 函数内部通过指针可修改原值，适用于需要修改原值或动态内存分配。 |
| 传函数指针 | 可在函数内部调用传递的函数，适用于**回调函数或函数作为参数**的情况。 |
| 传数组指针 | 可在函数内部访问数组元素。                                   |
| 默认参数   | 调用函数时可省略默认参数，适用于**提供默认行为或减少函数重载**。 |
|            |                                                              |
| 默认参数   | **默认参数使用注意事项**                                     |
|            | 只能从右往走定义, 必须位于非默认参数的右侧;                  |
|            | 只在函数声明中指定一次, 多个声明中必须保持一致;              |
|            | 函数定义(实现)中不需要再次指定.                              |

#### 传值

```cpp
#include <iostream>

void passByValue(int x) {
    x = 10;
}

int main() {
    int a = 5;
    passByValue(a);
    std::cout << "After passByValue: " << a << std::endl; // 输出5
    return 0;
}
```

#### 传引用

```cpp
#include <iostream>

void passByReference(int &x) {
    x = 10;
}

int main() {
    int a = 5;
    passByReference(a);
    std::cout << "After passByReference: " << a << std::endl; // 输出10
    return 0;
}
```

#### 传指针

```cpp
#include <iostream>

void passByPointer(int *x) {
    *x = 10;
}

int main() {
    int a = 5;
    passByPointer(&a);
    std::cout << "After passByPointer: " << a << std::endl; // 输出10
    return 0;
}
```

#### 传函数指针

```cpp
#include <iostream>

void displayMessage() {
    std::cout << "Hello, World!" << std::endl;
}

void executeFunction(void (*func)()) {
    func();
}

int main() {
    executeFunction(displayMessage); // 输出"Hello, World!"
    return 0;
}
```

#### 传数组指针

```cpp
#include <iostream>

void passArrayPointer(int (*arr)[5]) {
    for (int i = 0; i < 5; ++i) {
        std::cout << (*arr)[i] << " ";
    }
    std::cout << std::endl;
}

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    passArrayPointer(&arr); // 输出"1 2 3 4 5"
    return 0;
}
```

#### 默认参数

|      | 默认参数使用注意事项                            |
| ---- | ----------------------------------------------- |
| 1    | 只能从右往走定义, 必须位于非默认参数的右侧;     |
| 2    | 只在函数声明中指定一次, 多个声明中必须保持一致; |
| 3    | 函数定义(实现)中不需要再次指定.                 |

```cpp
#include <iostream>

void greet(std::string name = "World") {
    std::cout << "Hello, " << name << "!" << std::endl;
}

int main() {
    greet(); // 输出"Hello, World!"
    greet("Alice"); // 输出"Hello, Alice!"
    return 0;
}
```

```
#include <iostream>  
using namespace std;  
  
// 函数声明，指定默认参数  
void displayMessage(string message, int repeatTimes = 1);  
  
int main() {  
    // 调用函数时，未提供第二个参数，将使用默认值 1  
    displayMessage("Hello, world!");  
  
    // 调用函数时，提供了第二个参数，将使用提供的值 3  
    displayMessage("Hello, again!", 3);  
  
    return 0;  
}  
  
// 函数实现  
void displayMessage(string message, int repeatTimes) {  
    for (int i = 0; i < repeatTimes; ++i) {  
        cout << message << endl;  
    }  
}
```

### 返回值

| 返回值       | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| 临时变量     | 函数内局部变量. 拷贝/RVO/移动语义来实现的.                   |
| 引用         | 返回有效引用(静态变量/全局变量/类成员), **避免函数内局部变量的引用(返回后被销毁->无效)** |
| 指针         | 返回有效指针(**动态分配/静态全局变量**),**避免局部变量指针**(返回后被销毁->无效) |
| 智能指针     | `std::unique_ptr`或`std::shared_ptr`                         |
|              |                                                              |
| **注意事项** | **避免返回函数内局部变量的指针/引用**, 离开函数作用域后, 被销毁, **导致野指针/悬挂引用** |
|              | 可以返回**静态变量或全局变量的引用/指针**,一直存在.          |
|              | 返回动态分配的指针时, 注意释放内存,防止内存泄漏.             |

#### 返回值优化(RVO)

- RVO是一种编译器优化技术，在函数返回时直接在调用者的上下文中构造返回值对象，而不是先在被调用函数的栈帧中构造临时对象再拷贝到调用者的上下文中。这避免了临时对象的拷贝和销毁，使得返回的对象在函数返回后依然有效。

#### 移动语义(Move Semantics)

- C++11引入了右值引用(rvalue references)和移动语义，使得可以高效地转移临时对象的资源，而不是拷贝它们。当函数返回临时对象时，编译器可以调用对象的移动构造函数，将资源转移到返回值中。

### 递归函数

|              | 说明                                                       |
| ------------ | ---------------------------------------------------------- |
| 定义         | 直接或间接调用自身的函数, 用于将复杂问题分解为子问题.      |
| **注意事项** | **明确终止条件**, 防止无限递归, 引起栈溢出.                |
|              | **逐步逼近**, 递归调用应当使问题规模减小, 逐步逼近终止条件 |
|              | **控制递归深度**, 防止栈溢出,                              |
|              | **避免重复计算**,影响性能, 可使用记忆化/动态规划来优化.    |

**函数格式**:

```
返回类型 函数名(参数列表) {  
    // 基本情况(base case)  
    if (满足某个条件) {  
        // 直接返回结果，不再递归  
        return 结果;  
    }  
      
    // 递归情况(recursive case)  
    // 将问题分解为更小的子问题，并递归调用自身  
    return 函数名(修改后的参数);  
}
```

**代码示例:**

```
#include <iostream>  
  
// 递归函数计算阶乘  
int factorial(int n) {  
    // 基本情况：0的阶乘是1  
    if (n == 0) {  
        return 1;  
    }  
      
    // 递归情况：n的阶乘是n乘以(n-1)的阶乘  
    return n * factorial(n - 1);  
}  
  
int main() {  
    int number;  
    std::cout << "Enter a non-negative integer: ";  
    std::cin >> number;  
      
    // 检查输入是否为非负整数  
    if (number < 0) {  
        std::cout << "Invalid input! Please enter a non-negative integer." << std::endl;  
        return 1;  
    }  
      
    // 调用递归函数并输出结果  
    std::cout << "Factorial of " << number << " is: " << factorial(number) << std::endl;  
      
    return 0;  
}
```

下面是一个计算阶乘的递归函数的例子：

```cpp
#include <iostream>  
  
// 递归函数计算阶乘  
int factorial(int n) {  
    // 基本情况：0的阶乘是1  
    if (n == 0) {  
        return 1;  
    }  
      
    // 递归情况：n的阶乘是n乘以(n-1)的阶乘  
    return n * factorial(n - 1);  
}  
  
int main() {  
    int number;  
    std::cout << "Enter a non-negative integer: ";  
    std::cin >> number;  
      
    // 检查输入是否为非负整数  
    if (number < 0) {  
        std::cout << "Invalid input! Please enter a non-negative integer." << std::endl;  
        return 1;  
    }  
      
    // 调用递归函数并输出结果  
    std::cout << "Factorial of " << number << " is: " << factorial(number) << std::endl;  
      
    return 0;  
}
```

### 内联函数

|              | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| 定义         | **请求编译器在函数调用时用函数实体替代调用**, 适用于**频繁调用小函数**. |
| 优点         | 减少函数调用开销, 优化代码.                                  |
| 缺点         | 代码膨胀, 调试困难, 编译时间增加.                            |
| **不宜内联** | 函数有: 大型,递归,含有静态变量,(含有循环/复杂控制流),虚函数, 构造和析构. |
|              | 虚函数不宜内联: 动态绑定和静态绑定的冲突                     |
|              | 构造和析构不宜内联: 复杂度, 编译器限制.                      |
| 注意事项     | **内联是建议而非强制**, 编译器可以忽略.                      |
|              | **不要过度依赖内联**, 可能导致代码膨胀及其他问题, 谨慎使用.  |
|              | **内联函数通常定义在头文件中**：方便调用点可见               |
|              | **类内定义的函数默认为内联函数**;                            |

### Lambda





# 3 class

## 3.1 基础

### 访问修饰符

|           | 说明                                    |
| --------- | --------------------------------------- |
| public    | 公开，无访问限制                        |
| protected | 只在类内部, 派生类中, 友元函数/类可访问 |
| private   | 只在类内部和**友元**函数/类访问         |

代码示例：

```
class MyClass {  
public:    // 公有成员  
    int publicVar;  
    void publicFunc() {}  
  
protected: // 受保护成员  
    int protectedVar;  
    void protectedFunc() {}  
  
private:   // 私有成员  
    int privateVar;  
    void privateFunc() {}  
};  
  
int main() {  
    MyClass obj;  
  
    // 可以访问公有成员  
    obj.publicVar = 10;  
    obj.publicFunc();  
  
    // 以下代码将产生编译错误，因为尝试访问受保护或私有成员  
    // obj.protectedVar = 20; // 错误：不能访问受保护成员  
    // obj.privateVar = 30;   // 错误：不能访问私有成员  
    // obj.protectedFunc();   // 错误：不能访问受保护成员  
    // obj.privateFunc();     // 错误：不能访问私有成员  
  
    return 0;  
}
```

### 特殊成员函数

| 特殊成员函数     | 说明                                                      |
| ---------------- | --------------------------------------------------------- |
| **概念**         | 不定义时, 编译器会自动生成的成员函数.                     |
| **包含**         | 构造, 析构, 拷贝构造, 拷贝赋值, (c++11)移动构造, 移动赋值 |
|                  |                                                           |
| **调用条件差异** |                                                           |
| 构造函数         | 无初始值创建对象                                          |
| 拷贝构造         | 初始化时, 用已存在对象/(按值传递/返回对象)                |
| 移动构造         | 初始化时, 用临时对象/std::move转右值                      |
| 拷贝赋值         | 赋值时, 用已存在对象                                      |
| 移动赋值         | 赋值时, 用临时对象/std::move转右值                        |


代码示例:

```
#include <iostream>
#include <string>

class MyClass {
public:
    std::string name;
    int value;

    // 默认构造函数
    MyClass() : name("default"), value(0) {
        std::cout << "Default constructor called" << std::endl;
    }

    // 析构函数
    ~MyClass() {
        std::cout << "Destructor called" << std::endl;
    }

    // 拷贝构造函数
    MyClass(const MyClass& other) : name(other.name), value(other.value) {
        std::cout << "Copy constructor called" << std::endl;
    }

    // 拷贝赋值运算符
    MyClass& operator=(const MyClass& other) {
        if (this != &other) {
            name = other.name;
            value = other.value;
        }
        std::cout << "Copy assignment operator called" << std::endl;
        return *this;
    }

    // 移动构造函数
    MyClass(MyClass&& other) noexcept : name(std::move(other.name)), value(other.value) {
        other.value = 0;
        std::cout << "Move constructor called" << std::endl;
    }

    // 移动赋值运算符
    MyClass& operator=(MyClass&& other) noexcept {
        if (this != &other) {
            name = std::move(other.name);
            value = other.value;
            other.value = 0;
        }
        std::cout << "Move assignment operator called" << std::endl;
        return *this;
    }

    // 自定义函数
    void display() const {
        std::cout << "Name: " << name << ", Value: " << value << std::endl;
    }
};

int main() {
    MyClass obj1;//默认构造
    obj1.display();

    MyClass obj2("custom", 10);//自定义构造
    obj2.display();

    MyClass obj3 = obj2; // 拷贝构造
    obj3.display();

    MyClass obj4 = std::move(obj2); // 移动构造
    obj4.display();
    obj2.display(); // 被移动后的对象

    obj3 = obj4; // 拷贝赋值
    obj3.display();

    obj3 = std::move(obj4); // 移动赋值
    obj3.display();
    obj4.display(); // 被移动后的对象

    return 0;
}

```



## 3.2 继承

### 概念和访问权限

|              | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| 概念         | 一个类继承自另一个类, 被继承的叫父类/基类, 另一个叫子类/派生类. |
| 继承属性     | public, protected, private                                   |
| **调用顺序** |                                                              |
| 构造函数     | 先基类, 后派生类.                                            |
| 析构函数     | 先派生类, 后基类.                                            |

| 继承\基类     | public 成员 | protected成员 | private成员 |
| ------------- | ----------- | ------------- | ----------- |
| public继承    | public      | protected     | private     |
| protected继承 | protected   | protected     | private     |
| private继承   | private     | private       | private     |

代码示例:

```

```

### 重载, 覆盖(重写),隐藏

|      | 说明                                          |
| ---- | --------------------------------------------- |
| 重载 | 类中函数名相同, 参数列表不同(类型/个数/顺序). |
| 覆盖 | 派生类重新定义基类中的虚函数.                 |
| 隐藏 | 派生类定义一个与基类同名, 参数列表不同的函数. |

|      | 英文     | 作用域       | 名字+参数列表+返回类型               | 虚函数   |
| ---- | -------- | ------------ | ------------------------------------ | -------- |
| 重载 | Overload | 同一作用域   | 名字相同, 参数列表不同, 返回类型无关 | 无关     |
| 覆盖 | Override | 基类和派生类 | 名字/参数列表/返回类型,均相同        | 虚函数   |
| 隐藏 | Hide     | 基类和派生类 | 名字相同                             | 非虚函数 |

代码示例

```
#include <iostream>

// 基类
class Base {
public:
    void func(int x) { // 非虚函数
        std::cout << "Base func(int): " << x << std::endl;
    }

    virtual void virtualFunc() { // 虚函数
        std::cout << "Base virtualFunc" << std::endl;
    }

    void overloadedFunc(int x) { // 重载函数
        std::cout << "Base overloadedFunc(int): " << x << std::endl;
    }

    void overloadedFunc(double x) { // 重载函数
        std::cout << "Base overloadedFunc(double): " << x << std::endl;
    }
};

// 派生类
class Derived : public Base {
public:
    void func() { // 隐藏
        std::cout << "Derived func()" << std::endl;
    }

    void virtualFunc() override { // 覆盖
        std::cout << "Derived virtualFunc" << std::endl;
    }

    void overloadedFunc(int x) { // 重载(基类同名函数被隐藏)
        std::cout << "Derived overloadedFunc(int): " << x << std::endl;
    }
};

int main() {
    Base base;
    Derived derived;

    base.func(10); // 调用 Base::func(int)
    derived.func(); // 调用 Derived::func()，隐藏 Base::func(int)

    base.virtualFunc(); // 调用 Base::virtualFunc
    derived.virtualFunc(); // 调用 Derived::virtualFunc(覆盖)

    base.overloadedFunc(10); // 调用 Base::overloadedFunc(int)
    base.overloadedFunc(3.14); // 调用 Base::overloadedFunc(double)

    derived.overloadedFunc(10); // 调用 Derived::overloadedFunc(int)，Base::overloadedFunc(double) 被隐藏

    return 0;
}
```

### 单继承与多继承

|        | 说明                                                 |
| ------ | ---------------------------------------------------- |
| 单继承 | 一个基类, 用于简单明确的场景,                        |
| 多继承 | 多个基类, 用于需要多个类的行为和属性场景,            |
|        |                                                      |
| 多继承 | **多继承使用注意事项**                               |
|        | 可能引入二义性, 小心处理. 如存在多个同名函数/变量时. |
|        | **菱形继承**时可使用**虚基类**来解决.                |

代码示例: 

```
#include <iostream>
#include <string>

// 基类 Animal
class Animal {
public:
    void eat() {
        std::cout << "Animal is eating." << std::endl;
    }
};

// 基类 Mammal
class Mammal {
public:
    void giveBirth() {
        std::cout << "Mammal gives birth to live young." << std::endl;
    }
};

// 派生类 Dog，单继承自 Animal
class Dog : public Animal {
public:
    void bark() {
        std::cout << "Dog is barking." << std::endl;
    }
};

// 派生类 Bat，继承自 Animal 和 Mammal
class Bat : public Animal, public Mammal {
public:
    void fly() {
        std::cout << "Bat is flying." << std::endl;
    }
};

int main() {
    Dog dog;
    Bat bat;

    // Dog 的单继承示例
    dog.eat();   // 从 Animal 继承
    dog.bark();  // Dog 自己的行为

    // Bat 的多继承示例
    bat.eat();      // 从 Animal 继承
    bat.giveBirth(); // 从 Mammal 继承
    bat.fly();       // Bat 自己的行为

    return 0;
}
```


### 虚继承

|              | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| **菱形继承** | 在多继承中, 当一个类从多个途径继承自同一基类时, 该类存在多个基类实例, |
|              | 二义性: 导致编译器无法确定该使用哪一个基类的成员.            |
|              | 浪费存储空间:                                                |
| **虚基类**   | 继承时加virtual, 确保菱形继承中, 只有一份虚基类的实例.       |
| **虚基指针** | Virtual Base Pointer, vbptr,  也叫**虚基类指针**             |
|              | 每个虚继承的派生类**对象**都包含一个虚基指针, 指向虚基类表.  |
| **虚基类表** | Virtual Base Table，vbtbl                                    |
|              | 存储虚基类的**偏移量**, 帮助定位虚基类的位置                 |
|              | 属于类级别, 通过虚基指针进行引用.                            |
| **偏移量**   | 虚基类表中的偏移量: 指虚基类(A) 在派生类对象中的相对位置     |
|              | 偏移量的基准:  相对于派生类对象(D)的起始地址                 |
|              |                                                              |
| **构造过程** | ABCD的具体构造过程                                           |
| 构造D        | 分配内存, D类对象内存,  B/C/A的实例区域以及虚基指针/虚函数指针. |
| 构造A        | 通过B和C的虚基指针查到A的偏移量, 确定A在D类对象内存中的位置. 调用A构造函数, 构造A |
| 构造B+C      | 调用B+C类构造函数, 通过B/C的虚基指针指向虚基类表, **确保A已构造** |
| 构造D        | 调用D的构造函数, 初始化D类的成员变量.                        |
|              |                                                              |
|              | 虚基类不改变访问控制属性.                                    |

代码示例：

```
#include <iostream>

class A {
public:
    int a;
    A() : a(0) { std::cout << "A constructed\n"; }
    virtual void foo() { std::cout << "A::foo\n"; }
};

class B : virtual public A {
public:
    int b;
    B() : b(1) { std::cout << "B constructed\n"; }
    virtual void foo() { std::cout << "B::foo\n"; }
};

class C : virtual public A {
public:
    int c;
    C() : c(2) { std::cout << "C constructed\n"; }
    virtual void foo() { std::cout << "C::foo\n"; }
};

class D : public B, public C {
public:
    int d;
    D() : d(3) { std::cout << "D constructed\n"; }
    virtual void foo() { std::cout << "D::foo\n"; }
};

int main() {
    D obj;
    obj.foo();  // 调用D::foo
    return 0;
}
}
```

如上代码中ABCD四各类的内存模型如下

```
//D类的内存布局
+---------------------+  <-- D object start
| vbptr for B         | --> 指向B类的虚基类表
+---------------------+
| vptr for B          | --> 指向B类的虚函数表
+---------------------+
|   b                 | --> B类的成员变量
+---------------------+
| vbptr for C         | --> 指向C类的虚基类表
+---------------------+
| vptr for C          | --> 指向C类的虚函数表
+---------------------+
|   c (from C)        | --> C类的成员变量
+---------------------+
|   a (from A)        | --> A类实例
+---------------------+
|   d (from D)        | --> D类的成员变量
+---------------------+

//B's vbtable:
[ Offset to A from D ]

//C's vbtable:
[ Offset to A from D ]

```

## 3.3 virtual

### 虚函数和纯虚函数

| 概念     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| 虚函数   | virtual成员函数,允许派生类重写, 可通过基类指针/引用调用派生类对象 |
| 纯虚函数 | virtual和=0的成员函数, 基类只声明不定义, 派生类必须提供具体实现. |
| 抽象类   | 含有纯虚函数的类, 称为抽象类, 不能实例化.                    |
|          |                                                              |
|          | **虚函数使用注意事项**                                       |
| 1        | 派生类重写虚函数时, 加上virtual和override, 便于编译器检查    |
| 2        | 避免隐藏虚函数, 确保为重写(同名+同参数列表),而不是隐藏       |
| 3        | 虚函数不能删除/修改/中间插入, 防止虚表错乱, 函数调用出错.    |
| 4        | 析构函数声明为虚函数, 基类指针/引用删除派生类对象时, 调动基类析构,防止资源泄漏 |
| 5        | 构造函数不能为虚函数.                                        |
|          |                                                              |
|          | **构造函数不能为虚函数的原因**                               |
| 1        | 构造函数调用时, 对象类型已确定,无需动态绑定.                 |
| 2        | 创建对象时, 对象未实例化完成, 内存空间不存在, 无法找到虚表.  |


### 虚指针和虚表

|          | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| 虚指针   | vptr, 每个包含虚函数**类对象**都有一个虚指针, 指向虚函数表.  |
| 虚函数表 | vtable, 每个包含虚函数的**类**都有一个虚函数表, 表中存储虚函数指针. |
|          |                                                              |
| **本质** | 根据指针对象的虚指针, 找到虚表, 再从虚表中找到虚函数指针, 最后调用对应的虚函数 |
|          | 虚指针->虚表->虚函数->调用.                                  |

代码示例：

```
#include <iostream>

class Base {
public:
    virtual void foo() { std::cout << "Base::foo\n"; }
    virtual void bar() { std::cout << "Base::bar\n"; }
    virtual ~Base() {} // 添加虚析构函数以正确释放派生类对象
};

class Derived : public Base {
public:
    virtual void foo() override { std::cout << "Derived::foo\n"; }
    virtual void bar() override { std::cout << "Derived::bar\n"; }
};

int main() {
    Base* obj = new Derived();
    obj->foo(); // 调用 Derived::foo
    obj->bar(); // 调用 Derived::bar
    delete obj; // 调用 Derived 和 Base 的析构函数
    return 0;
}
```

如上示例代码的详细说明如下: 

|                | 构造过程                                                     |
| -------------- | ------------------------------------------------------------ |
| **对象创建**   | 创建`Derived`类对象时, 插入 vptr(/初始化指向虚函数).         |
| **虚表初始化** | `Base` 类和 `Derived` 类各自有一个虚函数表                   |
|                | `Base` 类的虚函数表包含指向 `Base::foo` 和 `Base::bar` 的指针 |
|                | `Derived` 类的虚函数表包含指向 `Derived::foo` 和 `Derived::bar` 的指针 |
|                |                                                              |
|                | **虚函数调用过程 : 虚指针->虚表->虚函数->调用**              |
| 1              | 虚指针:  `Base*` 类型的 `obj` , 实际上指向 `Derived`, 找到 `Derived.vptr` |
| 2              | 虚表:  通过`Derived.vptr`找到`Derived.vtable`                |
| 3              | 虚函数: 从 `Derived.vtable` 中找到 `Derived::foo`的地址, 并调用 |
|                |                                                              |
|                | **Base 类的虚表 (vtable)**                                   |
| **Index**      | **Function Pointer**                                         |
| 0              | &Base::foo                                                   |
| 1              | &Base::bar                                                   |
| 2              | &Base::~Base                                                 |
|                |                                                              |
|                | **Derived 类的虚表 (vtable)**                                |
| **Index**      | **Function Pointer**                                         |
| 0              | &Derived::foo                                                |
| 1              | &Derived::bar                                                |
| 2              | &Derived::~Derived                                           |

**Derived 对象内存布局**

```
+------------------------+  <-- Derived object start
| vptr (指向Derived vtable) |
+------------------------+
| Base 类的成员           |
+------------------------+
| Derived 类的成员        |
+------------------------+
```



## 3.4 关联

### this

|      | this指针说明                      |
| ---- | --------------------------------- |
| 1    | 隐式指针, 指向调用成员函数的对象. |
| 2    | 只能在非静态成员函数中使用.       |

### const与class

| const    | 说明                                                      |
| -------- | --------------------------------------------------------- |
| 变量     | 又称const常量, 必须初始化, 且不可修改.                    |
| 传参     | 确保入参不被函数修改.                                     |
| 返回值   | 表示返回值不可修改, 放在函数定义最开头(返回值类型之前)    |
| 成员变量 | 必须在构造函数初始化列表中初始化, 之后不可修改.           |
| 成员函数 | 不修改成员变量的值, 即函数执行过程中, 对象的状态不会改变. |
|          |                                                           |
|          | **const成员函数说明**                                     |
| 1        | 不修改成员变量的值, mutable成员变量除外.                  |
| 2        | 只能调用const成员函数.                                    |
| 3        | 写法: const放在参数列表最后.                              |
| 4        | 声明和定义要一致,  即都加const                            |

示例代码

```
#include <iostream>

class MyClass {
private:
    int value;
    mutable int mutableValue;

public:
    MyClass(int val) : value(val), mutableValue(0) {}

    int getValue() const {
        return value; // 读取成员变量的值
    }

    void setValue(int val) {
        value = val; // 修改成员变量的值
    }

    void modifyMutableValue() const {
        mutableValue++; // 允许修改 mutable 变量
    }

    void display() const {
        std::cout << "Value: " << value << ", Mutable Value: " << mutableValue << std::endl;
    }
};

int main() {
    MyClass obj(10);

    obj.display();
    obj.setValue(20); // 修改成员变量的值
    obj.display();

    obj.modifyMutableValue(); // 修改 mutable 变量
    obj.display();

    const MyClass constObj(30);
    constObj.display();
    constObj.modifyMutableValue(); // 修改 mutable 变量
    constObj.display();

    // constObj.setValue(40); // 错误：不能在 const 对象上调用非 const 成员函数

    return 0;
}
```

### static与class

|                  | 说明                                                         |
| ---------------- | ------------------------------------------------------------ |
| **static成员**   | 访问属性依然存在, 和普通成员一样.                            |
| **静态成员变量** | 属于类, 所有对象共享一份, 类外定义.                          |
| **静态成员函数** | 属于类, 所有对象共享, 没有`this`指针, 可直接调用(通过类名::func方式) |
|                  | 不能访问非**非静态成员变量** 和 **非静态成员函数**           |
| **静态局部变量** | 作用域仅限于函数内部, 生命周期贯穿程序整个运行期间.          |
| **静态类**       | 无直接的静态类概念                                           |
|                  | 通过将构造+析构+拷贝构造 声明为 `delete`, 并将所有成员声明为 `static`来模拟. |
|                  | 很少使用, 适合纯函数和工具函数.                              |

示例代码:

```
#include <iostream>

class MyClass {
public:
    // 公有 static 成员变量
    static int publicStaticVar;
    
    // 公有 static 成员函数
    static void publicStaticFunc() {
        std::cout << "Public static function called." << std::endl;
        std::cout << "Accessing publicStaticVar: " << publicStaticVar << std::endl;
    }

protected:
    // 保护 static 成员变量
    static int protectedStaticVar;

    // 保护 static 成员函数
    static void protectedStaticFunc() {
        std::cout << "Protected static function called." << std::endl;
    }

private:
    // 私有 static 成员变量
    static int privateStaticVar;

    // 私有 static 成员函数
    static void privateStaticFunc() {
        std::cout << "Private static function called." << std::endl;
    }

public:
    // 公有成员函数，用于访问私有 static 成员
    static void accessPrivateStatic() {
        // 访问私有 static 成员变量和成员函数
        privateStaticVar = 10;
        privateStaticFunc();
        std::cout << "Private static variable: " << privateStaticVar << std::endl;
    }
};

// Static 成员变量的定义和初始化
int MyClass::publicStaticVar = 1;
int MyClass::protectedStaticVar = 2;
int MyClass::privateStaticVar = 3;

int main() {
    // 访问公有 static 成员变量
    MyClass::publicStaticVar = 5;
    std::cout << "Public static variable: " << MyClass::publicStaticVar << std::endl;

    // 调用公有 static 成员函数
    MyClass::publicStaticFunc();

    // 尝试直接访问保护 static 成员变量（会出错）
    // MyClass::protectedStaticVar = 6; // Error: protected member
    // MyClass::protectedStaticFunc();  // Error: protected member

    // 尝试直接访问私有 static 成员变量（会出错）
    // MyClass::privateStaticVar = 7;   // Error: private member
    // MyClass::privateStaticFunc();    // Error: private member

    // 通过公有成员函数访问私有 static 成员
    MyClass::accessPrivateStatic();

    return 0;
}
```

## 3.5 转换

|          | class的转换                                                  |
| -------- | ------------------------------------------------------------ |
| 自动转换 | 编译器自动完成, 通常通过构造/类型转换符来实现.               |
| 强制转换 | 程序员显式指定, static_cast/dynamic_cast/const_cast/reinterpret_cast |

自动转换代码示例:

```
#include <iostream>

class MyClass {
public:
    MyClass(int value) : value(value) {
        std::cout << "MyClass(int) constructor called\n";
    }

    operator int() const {
        std::cout << "operator int() called\n";
        return value;
    }

private:
    int value;
};

int main() {
    MyClass obj(42);

    // 自动转换：MyClass -> int
    int intValue = obj;  // 调用类型转换运算符
    std::cout << "intValue: " << intValue << std::endl;

    // 自动转换：int -> MyClass
    MyClass anotherObj = 100;  // 调用构造函数
    std::cout << "anotherObj: " << int(anotherObj) << std::endl;

    return 0;
}
```

强制转换代码示例:

```
#include <iostream>

class Base {
public:
    virtual void show() {
        std::cout << "Base show()" << std::endl;
    }
};

class Derived : public Base {
public:
    void show() override {
        std::cout << "Derived show()" << std::endl;
    }
};

int main() {
    Base* basePtr = new Derived();

    // 强制转换：Base* -> Derived*
    Derived* derivedPtr = static_cast<Derived*>(basePtr);
    derivedPtr->show();  // 调用 Derived 的 show()

    delete basePtr;
    return 0;
}
```

# 4 重载

|                | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| 重载           | 同一作用域, 同名+不同参数列表(类型/个数/顺序)的函数/运算符, 返回值类型无关 |
| 函数重载       | 可重载为普通函数/成员函数                                    |
| 运算符重载     | 可重载为普通函数/成员函数                                    |
| **链式调用**   | 当一个运算符被重载时, 其返回值应当使能够参与其他运算符操作的对象/引用. |
|                | 即通常放回类对象本身/引用.                                   |
|                | 用途: 一行代码中, 连续进行多次操作, 无需中间变量.            |
|                |                                                              |
| **运算符重载** | **代码格式**: 返回值 operator操作符(参数)                    |
|                |                                                              |
|                | **不可重载操作符**                                           |
| **::**         | 域运算符                                                     |
| .              | 成员访问运算符                                               |
| ->             | 成员指针访问运算符                                           |
| ?:             | 条件运算符                                                   |
| sizeof         | 长度运算符                                                   |
| typeid         | 类型识别运算符                                               |
| #              | 预处理符号                                                   |
| case           | 强制类型转换符, `static_cast`/`dynamic_cast`/`const_cast` /`reinterpret_cast` |
|                |                                                              |
|                | **操作符重载限制**                                           |
| 1              | 至少有一个操作数是用户自定义的类型, 为防止改变标准类型的原有语义. |
| 2              | 不能违反操作符原有的语法规则, 即操作数个数/语法结构/语义     |
| 3              | 不能改变操作符的优先级和结合律                               |
| 4              | 不能创建新的操作符                                           |
| 5              | 部分操作符不能被重载.                                        |
| 6              | 部分操作符只能通过**成员函数**重载. 如 =, []/, (), ->,       |
| 7              | 部分操作符只能通过**非成员函数**重载, 如 <</>>               |
| 8              | 重载操作符的参数不能全为默认参数                             |
| 9              | 返回值类型的限制: 通常返回做左操作数的引用, 以便支持**链式调用** |
| 10             | 操作符函数不能继承, 可重新定义.                              |
| 11             | 避免二义性, 防止出现多个操作符重置版本, 导致编译错误.        |
| 12             | new 和 delete, 必须重载为全局函数/类成员函数, 不能重载为局部函数/友元函数. |
| 13             | 访问权限: 操作符重载为非成员函数时, 如需访问类私有成员, 需要申明为友元. |
|                |                                                              |
| **运算符重载** | 只能通过**成员函数**                                         |
| =              | 赋值                                                         |
| []             | 数组                                                         |
| ()             | 调用                                                         |
| ->             | 指针访问                                                     |
|                |                                                              |
| **运算符重载** | 只能通过**非成员函数**                                       |
| >>             | 输入运算符                                                   |
| <<             | 输出运算符                                                   |
|                | 原因: 左操作数必须是标准输入输出流, 而不是类的实例, 所以只能通过非成员函数重载. |
|                |                                                              |
| **运算符重载** | **运算符重载其他注意事项**                                   |
| 一致性         | 重载运算符的行为与预期一致, 避免产生混淆.                    |
| 返回值类型     | 返回值类型应支持链式调用. 如 `operator+=` 通常返回`*this`的引用 |
|                | 对应返回新对象的运算符`operator+`,应返回一个临时对象.        |
| 友元/成员      | 某些运算符通常定义为友元函数, 以便访问私有成员.              |
|                | 一元运算符通常定义为成员函数, 二元运算符通常定义为友元/成员函数. |


## 函数重载

```
#include <iostream>

// 前向声明类 Calculator
class Calculator;

// 非成员函数重载
int add(int a, int b) {
    return a + b;
}

double add(double a, double b) {
    return a + b;
}

class Calculator {
public:
    // 成员函数重载
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    // 显示结果
    void display() {
        std::cout << "Using member function add(int, int): " << add(3, 4) << std::endl;
        std::cout << "Using member function add(double, double): " << add(3.5, 4.5) << std::endl;
    }
};

int main() {
    Calculator calc;

    // 使用成员函数重载
    calc.display();

    // 使用非成员函数重载
    std::cout << "Using non-member function add(int, int): " << add(10, 20) << std::endl;
    std::cout << "Using non-member function add(double, double): " << add(10.5, 20.5) << std::endl;

    return 0;
}
```

## 运算符重载

```
#include <iostream>

class Complex {
private:
    double real;
    double imag;

public:
    // 构造函数
    Complex(double r = 0.0, double i = 0.0) : real(r), imag(i) {}

    // 重载加法运算符，作为成员函数
    Complex operator+(const Complex& other) const {
        return Complex(real + other.real, imag + other.imag);
    }

    // 友元函数，用于重载输出运算符
    friend std::ostream& operator<<(std::ostream& os, const Complex& c);

    // 友元函数，用于重载输入运算符
    friend std::istream& operator>>(std::istream& is, Complex& c);
};

// 重载输出运算符，作为非成员函数
std::ostream& operator<<(std::ostream& os, const Complex& c) {
    os << "(" << c.real << ", " << c.imag << ")";
    return os;
}

// 重载输入运算符，作为非成员函数
std::istream& operator>>(std::istream& is, Complex& c) {
    is >> c.real >> c.imag;
    return is;
}

int main() {
    Complex c1(3.0, 4.0);
    Complex c2(1.0, 2.0);
    Complex c3;

    std::cout << "Enter a complex number (real and imaginary parts): ";
    std::cin >> c3;

    Complex c4 = c1 + c2;  // 使用重载的加法运算符

    std::cout << "c1: " << c1 << std::endl;
    std::cout << "c2: " << c2 << std::endl;
    std::cout << "c3: " << c3 << std::endl;
    std::cout << "c1 + c2: " << c4 << std::endl;

    return 0;
}
```

# 5.友元

|                | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| 友元函数       | 可访问类私有/保护成员的函数 在类声明时+friend.               |
| 友元类         | 可访问类私有/保护成员的类, 声明时+`friend class`             |
| **互为友元类** | 两个类互为友元类                                             |
|                |                                                              |
| **使用场景**   | 操作符重载**, **实现回调机制**, **避免过多的getter/setter方法 |
|                |                                                              |
|                | **使用注意事项**                                             |
| **破坏封装**   | 友元函数/友元类会破坏类的封装性, 暴露实现细节.               |
| **紧耦合**     | 增加耦合度, 导致维护/扩展变得复杂.                           |
| **谨慎使用**   | 谨慎使用, 尽量避免.                                          |

### 友元函数与友元类

```
#include <iostream>
#include <string>

// 前向声明类 B
class B;

class A {
private:
    int value;
public:
    A(int v) : value(v) {}

    // 声明友元函数
    friend void showValue(const A& a);

    // 声明友元类
    friend class B;
};

// 友元函数定义
void showValue(const A& a) {
    std::cout << "Value from friend function: " << a.value << std::endl;
}

class B {
public:
    void showValueFromA(const A& a) {
        std::cout << "Value from friend class: " << a.value << std::endl;
    }
};

int main() {
    A a(42);
    B b;

    // 使用友元函数
    showValue(a);

    // 使用友元类
    b.showValueFromA(a);

    return 0;
}
```

### 互为友元

```
#include <iostream>

class B; // 前向声明类 B

class A {
private:
    int valueA;
public:
    A(int v) : valueA(v) {}

    // 声明 B 为友元类
    friend class B;

    void showValueFromB(const B& b); // 声明一个方法展示 B 的私有值
};

class B {
private:
    int valueB;
public:
    B(int v) : valueB(v) {}

    // 声明 A 为友元类
    friend class A;

    void showValueFromA(const A& a); // 声明一个方法展示 A 的私有值
};

void A::showValueFromB(const B& b) {
    std::cout << "Value from class B: " << b.valueB << std::endl;
}

void B::showValueFromA(const A& a) {
    std::cout << "Value from class A: " << a.valueA << std::endl;
}

int main() {
    A a(10);
    B b(20);

    // 通过 A 类的方法展示 B 类的私有成员
    a.showValueFromB(b);

    // 通过 B 类的方法展示 A 类的私有成员
    b.showValueFromA(a);

    return 0;
}
```

# 6.模板

|            | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| 模板       | 泛型编程的一种, 允许编写类型无关的代码.                      |
| **用途**   | **类型无关的代码**                                           |
|            | **减少代码冗余**                                             |
|            | **增加代码灵活性**                                           |
|            | **编译时多态性**, 编译时根据类型生成相应代码, 并捕获类型错误. |
|            | **优化性能**, 编译时可能会对特性类型进行优化                 |
|            | **扩展性**, 模板可与其他特性(操作符重载/异常处理等)结合, 以创建强大易扩展的库/框架 |
|            |                                                              |
| 函数模板   | 通用算法: 与类型无关的通用函数                               |
| 类模板     | 通用类: 处理不同类型, 常用于实现通用数据结构,链表/栈/队列/树等. |
| 别名模板   | 提供了一种为模板定义新名字的方式, 用于简化模板类型名称, 增强代码可读性,c++11 |
| 变量模板   | 根据需要生产不同的变量                                       |
| 模板特化   | 允许为特定类型提供特化的实现.                                |
| 模板参数包 | 模板参数包允许你定义一个可变数量的模板参数                   |

##  函数模板

**定义**

函数模板是以关键字`template`开始，后跟一个尖括号`<>`中的类型参数列表，然后是函数声明和定义的常规格式。类型参数在函数体内作为占位符使用，当函数模板被实例化时，这些占位符会被具体的类型替换。

```
定义函数模板
template <typename type> return-type func-name(parameter list)
{
   // 函数的主体
}
```

```
#include <iostream>

template <typename T>
T add(T a, T b) {
    return a + b;
}

int main() {
    std::cout << add(5, 10) << std::endl;        // 整数相加
    std::cout << add(5.5, 10.5) << std::endl;    // 浮点数相加
    return 0;
}
```

## 类模板

```
template <typename type>
class class-name {
.
.
.
}
```

代码示例：

```
#include <iostream>

template <typename T>
class Stack {
private:
    T* arr;
    int size;
    int top;
public:
    Stack(int size) : size(size), top(-1) {
        arr = new T[size];
    }
    ~Stack() {
        delete[] arr;
    }
    void push(T value) {
        if (top < size - 1) {
            arr[++top] = value;
        }
    }
    T pop() {
        if (top >= 0) {
            return arr[top--];
        }
        return T(); // 返回默认值
    }
};

int main() {
    Stack<int> intStack(10);
    intStack.push(1);
    intStack.push(2);
    std::cout << intStack.pop() << std::endl;

    Stack<double> doubleStack(10);
    doubleStack.push(1.1);
    doubleStack.push(2.2);
    std::cout << doubleStack.pop() << std::endl;

    return 0;
}
```

## 别名模板

```
#include <iostream>
#include <vector>
#include <string>

template <typename T>
using Vec = std::vector<T>;

int main() {
    Vec<int> intVec = {1, 2, 3};
    Vec<std::string> stringVec = {"hello", "world"};

    for (int val : intVec) {
        std::cout << val << " ";
    }
    std::cout << std::endl;

    for (const auto& str : stringVec) {
        std::cout << str << " ";
    }
    std::cout << std::endl;

    return 0;
}
```

## 变量模板

```
#include <iostream>

template <typename T>
constexpr T pi = T(3.1415926535897932385);

int main() {
    std::cout << pi<float> << std::endl;  // 输出单精度 PI
    std::cout << pi<double> << std::endl; // 输出双精度 PI
    return 0;
}
```

## 模板特化

```
#include <iostream>

// 通用模板
template <typename T>
class TypeTraits {
public:
    static void printType() {
        std::cout << "Unknown type" << std::endl;
    }
};

// 特化模板
template <>
class TypeTraits<int> {
public:
    static void printType() {
        std::cout << "int" << std::endl;
    }
};

template <>
class TypeTraits<double> {
public:
    static void printType() {
        std::cout << "double" << std::endl;
    }
};

int main() {
    TypeTraits<int>::printType();    // 输出 int
    TypeTraits<double>::printType(); // 输出 double
    TypeTraits<char>::printType();   // 输出 Unknown type

    return 0;
}
```







# 5 异常处理



## 5.1 try catch throw

异常处理是一种处理程序中运行时错误或异常情况的机制

1. **try块**：将要检查的代码放在`try`块中。如果在执行`try`块中的代码时发生异常，控制将立即传递给与该异常类型匹配的`catch`块。
2. **catch块**：在`catch`块中处理异常。你可以有多个`catch`块来处理不同类型的异常。每个`catch`块都指定它可以处理的异常类型。
3. **throw语句**：使用`throw`语句抛出异常。你可以抛出任何类型的对象作为异常，但标准做法是抛出派生自`std::exception`的对象。
4. **异常类型**：标准库定义了一组异常类，你可以使用这些异常类，也可以定义自己的异常类。
5. **异常传播**：如果`try`块中的代码抛出异常，并且没有相应的`catch`块来捕获该异常，那么异常将继续向上传播，直到被捕获或导致程序终止。
6. **资源清理**：使用C++的RAII(Resource Acquisition Is Initialization)惯用法来确保在异常发生时资源得到正确清理。

```
#include <iostream>  
#include <stdexcept> // for std::runtime_error  
  
// 自定义异常类  
class MyException : public std::runtime_error {  
public:  
    explicit MyException(const std::string& what_arg) : std::runtime_error(what_arg) {}  
};  
  
int main() {  
    try {  
        // 可能抛出异常的代码  
        bool condition = false;  
        if (!condition) {  
            throw MyException("An error occurred!"); // 抛出自定义异常  
        }  
  
        // 其他代码...  
    } catch (const MyException& e) {  
        // 处理自定义异常  
        std::cerr << "Caught MyException: " << e.what() << std::endl;  
    } catch (const std::exception& e) {  
        // 处理其他标准异常  
        std::cerr << "Caught std::exception: " << e.what() << std::endl;  
    } catch (...) {  
        // 处理未知类型的异常  
        std::cerr << "Caught unknown exception" << std::endl;  
    }  
  
    return 0;  
}
```

## 5.2 exception类

自定义异常类： 可以通过从`std::exception`(或其任何派生类)继承来创建自定义异常类。

<stdexcept>中定义了标准异常，详细可以查看如下链接

[https://www.runoob.com/cplusplus/cpp-exceptions-handling.html](https://www.runoob.com/cplusplus/cpp-exceptions-handling.html)

```
#include <iostream>
#include <exception>
using namespace std;
 
struct MyException : public exception
{
  const char * what () const throw ()
  {
    return "C++ Exception";
  }
};
 
int main()
{
  try
  {
    throw MyException();
  }
  catch(MyException& e)
  {
    std::cout << "MyException caught" << std::endl;
    std::cout << e.what() << std::endl;
  }
  catch(std::exception& e)
  {
    //其他的错误
  }
}
```

## 5.3 其余异常处理

### 5.3.1 abort

`abort`函数是一个立即终止程序运行的函数，并返回一个非零的退出状态给操作系统。

此外，`abort`还会触发`SIGABRT`信号，你可以为这个信号设置一个信号处理函数，以在程序终止前执行一些清理工作。

```
#include <cstdlib> // 包含abort的声明  
  
int main() {  
    // ... 程序代码 ...  
  
    // 在某个条件下调用abort终止程序  
    if (/* 某些严重错误条件 */) {  
        abort();  
    }  
  
    // ... 更多程序代码(如果abort没有被调用，这些代码将会执行) ...  
  
    return 0;  
}
```

### 5.3.2 errno

`errno`是一个全局变量，用于表示某些系统调用和库函数执行时发生的错误。

`errno`的定义通常包含在`<errno.h>`(C语言风格)或`<cerrno>`(C++风格)头文件中。

在多线程环境中，`errno`通常是每个线程局部的，这意味着每个线程都有其自己的`errno`值，不会与其他线程共享。

```
#include <iostream>  
#include <cerrno>  
#include <cstring> // 包含strerror的声明  
  
int main() {  
    FILE *file = fopen("non_existent_file.txt", "r");  
    if (file == nullptr) {  
        std::cerr << "Error opening file: " << strerror(errno) << std::endl;  
        return 1;  
    }  
  
    // ... 文件的操作 ...  
  
    fclose(file);  
    return 0;  
}
```



# 6 内存与分配

## 6.1 内存模型

## 6.1.1 虚拟内存和物理内存

虚拟内存:

1. 操作系统内核为了对进程地址空间进行管理, 而设计的逻辑意义上的内存空间概念
2. 程序中的指针都是虚拟空间的地址
3. 每个进程都有自己独立的虚拟地址空间, 32位系统为4GB
4. 线性连续的.
5. 提高内存隔离带来的安全性.
6. 管理方式有分页和分段

物理内存

1. 硬件实际存在的，可供使用的内存空间。

虚拟内存到物理内存：

1. 通过**页映射表**， 将虚拟内存映射到物理内存。
2. 内核为每个进程维护一份相对独立的页映射表， 页(page)。

### 6.1.2 虚拟内存模型

c++ linux 32位(**4GB**) 进程的虚拟内存模型如下图所示:

![linux_memory_](F:\github\CPulsPlusPointTree\memory\linux_memory_.png)

 

|      | 管理           | 生长方向 | 说明                                              |
| ---- | -------------- | -------- | ------------------------------------------------- |
| 栈   | 编译器分配释放 | 向下生长 | 先进后出(FIFO), 存放局部变量,实参,返回地址等      |
| 堆   | 程序员分配释放 | 向上增长 | malloc,free,new,delete等. 如不释放则程序结束回收. |

|         | 可读写段                                                     |
| ------- | ------------------------------------------------------------ |
| .data   | 数据段, **已初始化**的全局变量/静态变量,可读可写.            |
| .bss    | Block Started by Symbol,未初始化数据段, **未初始化**的全局变量/静态变量,可读可写; |
|         |                                                              |
|         | **只读段**                                                   |
| .text   | Test Segment, 代码段,程序的二进制代码,只读                   |
| .rodata | Read-Only Data Segment 只读数据段, 常量，字面值等            |
| .init   | ELF文件的**非标准段**, 可能作用: 全局/静态变量初始化,构造函数调用,启动代码. |

## 6.2 内存分配

malloc/free和new/delete的差异

|                  | malloc/free            | new/delete                                |
| ---------------- | ---------------------- | ----------------------------------------- |
| 类型             | 函数                   | 操作符                                    |
| 初始化与构造析构 | 所申请内存空间未初始化 | 自动调用构造初始化和析构释放              |
| 定制性           | 需手动计算大小         | 自动计算大小,方便                         |
| 返回值           | void*, 需要强转        | 对应具体类型                              |
| 分配失败时       | 返回NULL               | 抛出异常std::bad_alloc, 可用try-catch处理 |

### 6.2.1 malloc,free

malloc： 堆内存申请

```
void* malloc(size_t size);
size 申请内存字节数
返回类型是void*类型, void*类型可以强制转换为任何其他类型的指针
```

free : 堆内存释放

```
void free(void* p);
形参中的指针声明为void*
```

代码示例：

```
#include <iostream>  
#include <cstdlib> // 包含 malloc 和 free 的头文件  
  
int main() {  
    // 使用 malloc 分配 4 个字节(一个 int 的大小)  
    int* ptr = (int*)malloc(sizeof(int));  
    if (ptr == nullptr) { // 检查 malloc 是否成功分配内存  
        std::cerr << "Memory allocation failed!" << std::endl;  
        return 1; // 非零返回值表示程序异常终止  
    }  
  
    // 给分配的内存赋值  
    *ptr = 42;  
  
    // 使用分配的内存  
    std::cout << "Value of the integer: " << *ptr << std::endl;  
  
    // 释放内存  
    free(ptr);  
    ptr = nullptr; // 将指针置空，避免悬挂指针  
  
    return 0; // 零返回值表示程序正常终止  
}
```

### 6.2.2 new,delete

|      | new                          | delete        |
| ---- | ---------------------------- | ------------- |
|      | 堆内存分配                   | 堆内存释放    |
|      | 调用构造初始化               | 调用析构释放  |
|      | 返回新分配并初始化的对象指针 | 传入new的指针 |
|      | 失败抛出std::bad_alloc异常   |               |

代码示例：

```
#include <iostream>  
#include <new> // 包含 nothrow 版本的 new 的头文件(虽然不是必须的，但为了说明可以包含)  
  
class MyClass {  
public:  
    MyClass() {  
        std::cout << "MyClass constructor called." << std::endl;  
    }  
      
    ~MyClass() {  
        std::cout << "MyClass destructor called." << std::endl;  
    }  
};  
  
int main() {  
    // 使用 new 分配内存，并自动调用 MyClass 的构造函数  
    MyClass* ptr = new MyClass;  
  
    // 使用对象  
    // ...  
  
    // 释放内存，并自动调用 MyClass 的析构函数  
    delete ptr;  
    ptr = nullptr; // 将指针置空，避免悬挂指针  
  
    // 也可以使用 nothrow 版本的 new 来避免抛出异常  
    MyClass* ptr2 = new(std::nothrow) MyClass;  
    if (ptr2 == nullptr) {  
        std::cerr << "Memory allocation failed without throwing an exception." << std::endl;  
        return 1; // 返回非零值表示程序异常终止  
    }  
  
    // 使用对象  
    // ...  
  
    // 释放内存  
    delete ptr2;  
    ptr2 = nullptr;  
  
    return 0; // 返回零表示程序正常终止  
}
```

### 6.2.3 new[],delete[] 

|      | new[]                        | delete[]             |
| ---- | ---------------------------- | -------------------- |
|      | 分配数组内存                 | 释放数组内存         |
|      | 调用构造函数初始化           | 调用析构函数释放资源 |
|      | 返回指向该数组首个元素的指针 |                      |
|      | 失败抛出std::bad_alloc异常   |                      |

代码示例:

```
#include <iostream>  
  
class MyClass {  
public:  
    MyClass() {  
        std::cout << "Object constructed." << std::endl;  
    }  
      
    ~MyClass() {  
        std::cout << "Object destroyed." << std::endl;  
    }  
};  
  
int main() {  
    // 使用 new[] 分配一个包含 5 个 MyClass 对象的动态数组  
    MyClass* array = new MyClass[5];  
  
    // 输出一些信息，以显示对象已被构造  
    std::cout << "Array allocated." << std::endl;  
  
    // 使用数组...  
    // ...  
  
    // 释放动态数组的内存  
    delete[] array;  
  
    // 输出一些信息，以显示对象已被销毁  
    std::cout << "Array deleted." << std::endl;  
  
    return 0;  
}
```

## 6.3 内存问题

常见内存问题有:

|                             | 说明                                  |
| --------------------------- | ------------------------------------- |
| memory leak                 | 内存泄漏, 只申请不释放                |
| memory overrun              | 内存越界, 访问超出分配内存大小的位置, |
| double free                 | 同一块内存释放两次,                   |
| use after free              | 内存释放后使用, 通常为野指针导致的    |
| wild free                   | 释放内存的参数为非法值                |
| access uninitialized memory | 访问未初始化内存                      |
| read invalid memory         | 读取非法内存，本质上也属于内存越界    |
| stack overflow              | 栈溢出                                |
|                             | 内存碎片化                            |

内存问题可能导致的后果:

1. **程序崩溃**：当遇到严重的内存错误，如访问空指针、使用已经释放的内存(Use After Free)或释放未分配的内存(Wild Free)时，程序可能会立即崩溃。
2. **数据损坏**：如果程序错误地写入了内存，特别是如果它写入了超出其分配范围的内存，可能会损坏其他重要的数据结构或变量。这种损坏可能在程序执行的后续阶段才变得明显，导致难以追踪的错误。
3. **内存泄漏**：如果在动态分配的内存使用完成后没有释放，就会导致内存泄漏。长时间的内存泄漏会逐渐耗尽系统资源，导致程序运行速度减慢，甚至最终崩溃。
4. **安全漏洞**：内存错误有时可被攻击者利用来执行恶意代码、读取敏感信息或进行其他未授权的操作。例如，缓冲区溢出是一种常见的安全漏洞，攻击者可以利用它来覆盖程序的内存并控制程序的执行流程。
5. **不稳定性和不可预测性**：内存问题可能导致程序表现出不稳定和不可预测的行为。由于内存错误可能导致程序状态的不确定，因此程序可能会在不同的时间或不同的运行环境中表现出不同的错误。
6. **性能下降**：内存泄漏和频繁的内存分配/释放操作可能会导致程序性能下降。内存泄漏会逐渐消耗系统资源，而频繁的内存操作可能会导致额外的开销，如垃圾收集或内存碎片整理。

### 6.3.1 内存泄漏

原因:

1. new/delete, new[]/delete[] 不配对
2. 异常处理中/异常返回时, 为正确释放.

案例:

```
#include <iostream>  
  
int main() {  
    while (true) {  
        char* leak = new char[1024]; // 分配1KB内存  
        std::cout << "Allocating memory..." << std::endl;  
        // 故意遗漏 delete[] leak;  
    }  
    return 0; // 这行代码实际上永远不会被执行  
}
```

### 6.3.2 内存越界

内存越界，也被称为缓冲区溢出(Buffer Overflow)，是指程序在访问数组或其他类似数据结构时，读取或写入了超出其分配内存大小的位置。这种错误可能导致程序崩溃、数据损坏或安全漏洞.

一般出现在以下情况:

1. 使用数组时，索引超出了数组的实际大小。
2. 字符串处理函数(如`strcpy`, `strcat`等)未检查边界就进行了操作。
3. 动态分配内存时，请求的内存大小少于实际需要的大小。

案例：

```
#include <iostream>  
#include <cstring>  
  
int main() {  
    char buffer[5]; // 分配了一个大小为5的字符数组  
    std::strcpy(buffer, "Hello"); // 试图将"Hello"字符串(实际上需要6个字节，包括结尾的'\0')复制到buffer中  
    std::cout << "Buffer content: " << buffer << std::endl; // 这可能会导致未定义行为，因为buffer没有足够的空间来存储整个字符串  
    return 0;  
}
```

### 6.3.3 double free

"double free"指的是尝试两次释放同一个内存块。

案例：

```
#include <iostream>  
  
int main() {  
    int* ptr = new int; // 分配一个整数的内存  
    *ptr = 42;  
  
    std::cout << "Value: " << *ptr << std::endl;  
  
    delete ptr; // 第一次正确释放内存  
    delete ptr; // 第二次尝试释放同一块内存，导致double free错误  
  
    return 0;  
}
```

### 6.3.4 Use After Free

"Use after free": 尝试访问/使用 已释放的内存.

"野指针": 是一个指向已经释放的内存或从未分配的内存的指针。当一个指针被释放后，如果没有将其设置为`nullptr`，它就变成了一个野指针。

"Use After Free" 通常涉及到 "野指针".

案例:

```
#include <iostream>  
  
int main() {  
    int* ptr = new int(42); // 动态分配内存  
    std::cout << "Value: " << *ptr << std::endl;  
  
    delete ptr; // 释放内存  
  
    // 此处未将ptr设置为nullptr，导致ptr成为悬空指针  
  
    std::cout << "Value after free: " << *ptr << std::endl; // Use After Free，未定义行为  
  
    return 0;  
}
```

### 6.3.5 wild free

"wild free" 一种错误的内存释放模式，尝试释放一个从未被分配或者不属于当前管理范围的内存。

示例：

```
#include <iostream>  
  
int main() {  
    int* ptr = (int*)0xDEADBEEF; // 一个随意的、未分配的内存地址  
    std::cout << "Attempting to free memory at address: " << ptr << std::endl;  
  
    free(ptr); // 尝试释放一个从未分配的内存地址，wild free  
  
    return 0;  
}
```

### 6.3.6 access uninitialized memory

"access uninitialized memory" 访问未初始化的内存指的是读取或写入一个已经分配但未设置初始值的内存区域。

未初始化的内存可能包含任何值，这些值取决于内存分配之前的状态或是系统/运行时环境的内部行为。

示例：

```
#include <iostream>  
  
int main() {  
    int *ptr = new int; // 分配了一个int大小的内存，但没有初始化  
  
    std::cout << "Value of uninitialized memory: " << *ptr << std::endl; // 访问未初始化的内存,可能输出任意值
  
    delete ptr; // 释放内存  
    return 0;  
}
```

### 6.3.7 read invalid memory

"read invalid memory"指的是程序尝试读取一个无效的内存地址。

无效的内存地址可能是未分配的、已经释放的(即悬空指针)、或者是超出了分配给某个对象的内存范围。

案例：

```
#include <iostream>  
  
int main() {  
    int *ptr = nullptr; // 初始化一个空指针  
  
    std::cout << "Value of invalid memory: " << *ptr << std::endl; // 尝试读取无效内存  
  
    return 0;  
}
```

```
#include <iostream>  
  
int main() {  
    int *ptr = new int(42); // 分配并初始化内存  
    delete ptr;             // 释放内存  
  
    std::cout << "Value after delete: " << *ptr << std::endl; // 尝试读取已经释放的内存  
  
    return 0;  
}
```

### 3.6.8 stack overflow

"stack overflow"指的是程序在运行时栈(stack)空间被过度使用，导致超出了为其分配的内存限制

栈是用于存储函数调用、局部变量和临时数据的数据结构。

避免栈溢出的方法：

1. 避免无限递归或深度递归，确保递归函数有明确的退出条件。
2. 小心处理大的局部变量和数组，考虑使用堆(heap)空间来存储它们。
3. 了解平台的栈大小限制，并适当调整栈大小(尽管这通常不是解决问题的最佳方法)。
4. 使用编译器提供的栈保护选项，如栈溢出保护(Stack Protection)或栈canary。
5. 仔细审查第三方库和代码，确保它们不会导致栈溢出。

案例：

```
#include <iostream>  
  
void recursive_function() {  
    // 分配一个较大的局部变量(可选，但会加速栈溢出的发生)  
    char large_array[1024 * 1024] = {0};  
  
    // 递归调用自己，没有退出条件  
    recursive_function();  
}  
  
int main() {  
    // 调用递归函数  
    recursive_function();  
  
    // 这行代码实际上永远不会被执行，因为程序会因为栈溢出而崩溃  
    std::cout << "Program ended normally." << std::endl;  
  
    return 0;  
}
```



## 6.4 内存使用注意事项

在C++中进行内存分配时，需要注意以下事项：

1. **初始化与赋值**：
   分配的内存区域不会自动初始化，它们的值是未定义的(即它们可能包含任何值)。因此，在使用之前，你应该显式地初始化它们，以避免不确定行为。

2. **内存分配失败**：
   当内存分配失败时，例如通过`new`运算符，它会抛出一个`std::bad_alloc`异常(除非你使用了`nothrow`版本的`new`)。你应该准备好捕获这个异常，并适当地处理它，以防止程序崩溃。

3. **内存释放**：
   使用`delete`或`delete[]`来释放通过`new`或`new[]`分配的内存。确保不要释放同一块内存两次，因为这会导致未定义行为(通常是程序崩溃)。

4. **内存泄漏**：
   内存泄漏发生在当你分配了内存但忘记释放它时。长时间运行的程序可能会因为内存泄漏而耗尽所有可用内存。使用智能指针(如`std::unique_ptr`和`std::shared_ptr`)可以帮助自动管理内存并防止泄漏。

5. **数组分配**：
   当分配数组时，使用`new[]`而不是`new`，并使用`delete[]`而不是`delete`来释放它们。这是因为数组和单个对象在内存中的布局和管理方式可能不同。

6. **避免野指针**：
   一旦释放了内存，任何指向它的指针都变成野指针。访问野指针会导致未定义行为。在释放内存后，立即将指针设置为`nullptr`是一种良好的做法。

7. **内存对齐**：
   某些平台对数据对齐有严格的要求，不合适的对齐可能导致性能下降或硬件错误。大多数情况下，编译器和`new`运算符会处理对齐问题，但在进行低级内存操作时需要注意。

8. **内存碎片**：
   频繁地分配和释放小块内存可能导致内存碎片，这会降低内存利用率并可能导致性能问题。使用内存池、自定义分配器或避免小块内存的频繁分配和释放可以帮助减少碎片。

9. **栈与堆**：
   了解栈内存(局部变量)和堆内存(动态分配)之间的区别。栈内存由编译器自动管理，而堆内存需要程序员显式管理。过度使用栈内存可能导致栈溢出，而堆内存使用不当可能导致内存泄漏和其他问题。

10. **使用RAII原则**：
    资源获取即初始化(Resource Acquisition Is Initialization, RAII)是C++中管理资源(如内存、文件句柄等)的一种重要技术。通过将资源的生命周期与对象的生命周期绑定，可以确保在对象销毁时自动释放资源，从而减少资源泄漏的可能性。

11. **避免使用裸指针**：
    尽可能使用智能指针(如`std::unique_ptr`、`std::shared_ptr`)和容器(如`std::vector`、`std::string`)来代替裸指针(原生指针)，以自动处理内存管理，并减少错误的可能性。

12. **检查内存完整性**：
    在调试阶段，使用工具(如Valgrind)来检查内存泄漏、越界访问和其他内存相关的问题。这些工具可以帮助你识别和修复内存管理中的错误。

遵循这些注意事项可以帮助你编写更健壮、更高效的C++代码，并减少内存相关的问题。



## 6.5 linux 内存问题分析工具

在Linux环境下分析C++程序的内存问题，可以使用多种工具来帮助诊断和优化内存使用。以下是一些常用的内存问题分析工具：

1. **Valgrind**：
   Valgrind是一个强大的内存调试、内存泄漏检测以及性能分析工具。它包含了多个工具集，其中最常用的是`Memcheck`，用于检测程序中的内存泄漏和内存错误。

   ```bash
   bash复制代码
   
   valgrind --tool=memcheck --leak-check=full ./your_program
   ```

2. **AddressSanitizer (ASan)**：
   AddressSanitizer是一个由Google开发的快速内存错误检测器。它可以集成在Clang、GCC和一些其他编译器中，用于检测堆栈缓冲区溢出、使用后释放(dangling pointers)、未初始化内存读取等问题。

   编译时添加`-fsanitize=address`选项即可启用AddressSanitizer。

   ```bash
   g++ -fsanitize=address -o output your_source.cpp  
   ./output
   ```

3. **GDB**：
   GDB是GNU项目的调试器，它允许你查看程序执行时的状态，包括内存内容、变量值、调用栈等。虽然GDB不是一个专门的内存分析工具，但它对于调试内存相关的问题非常有用。

4. **perf**：
   perf是Linux下的一个强大的性能分析工具，可以用来分析程序的CPU使用情况、缓存命中/未命中、分支预测等，也可以通过分析内存访问模式来辅助内存问题的诊断。

5. **pmap和/proc/[pid]/smaps**：
   `pmap`是一个命令行工具，用于显示进程的内存映射。`/proc/[pid]/smaps`文件提供了关于进程内存使用的详细信息，包括每个内存区域的大小、权限和内存消耗等。

6. **Massif**：
   Massif是Valgrind工具集中的一个堆分析器，它可以用来分析程序在堆上的内存分配情况，帮助识别内存使用的热点和潜在的优化点。

7. **HeapTrack**：
   HeapTrack是一个用于跟踪和分析堆内存分配的工具，它可以提供详细的堆内存使用报告，包括哪些代码行分配了内存、分配了多少内存以及何时释放等。

8. **cppcheck**：
   cppcheck是一个静态分析工具，用于检测C++代码中的各种问题，包括内存泄漏、缓冲区溢出、未初始化的变量等。

9. **LeakTrace**：
   LeakTrace是一个轻量级的C++内存泄漏检测库，它可以集成到你的项目中，用于在运行时检测内存泄漏。

10. **自定义工具和日志**：
    对于复杂的内存问题，有时可能需要编写自定义的内存分配器、包装器或使用日志记录技术来追踪和分析内存使用情况。

当分析内存问题时，通常需要结合多个工具和技术来进行综合分析和定位。每个工具都有其特定的优点和适用场景，选择合适的工具可以大大提高内存问题分析和解决的效率。



# 标准库



vector

list

string

deque

queue

stack

map

set

bitset










# 易混淆问题

## 简单问题

### .1 char数组的strlen和sizeof的区别

|        | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| strlen | 求第一个空字符之前的字符数目, **不包含终止空字符**           |
| sizeof | 求    数组大小, 以字节为单位, 和数组元素个数无关.  用于指针时返回指针大小. |

```
#include <cstring>  

char str[] = "Hello, world!";  
size_t len = strlen(str);  // len will be 13, because "Hello, world!" has 13 characters

size_t size = sizeof(str);  // size will be 14, because the array includes the null terminator '\0'

const char* ptr = "Hello, world!";  
size_t ptr_size = sizeof(ptr);  // ptr_size will be the size of the pointer, not the length of the string
```

### .2 字符串数组拷贝函数

相关头文件: <string.h>,<cstring>

| 函数原型                                                |      |
| ------------------------------------------------------- | ---- |
| char *strcpy(char *dest, const char *src);              |      |
| char *strncpy(char *dest, const char *src, size_t len); |      |
| void memcpy(void *dest, const void *src, size_t n);     |      |

## 3.遗漏内容

goto，

wchar_t

volatile

new/delete

new[]/delete[]

内存问题

c++ 的字符串函数常见的

c++ 日期和时间类型的运用

c++ 标准输入输出

explicit

decltype



# 参考文档:

[C++内存问题，看这篇就够了 - 个人文章 - SegmentFault 思否](https://segmentfault.com/a/1190000039348996)

​     