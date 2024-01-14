[TOC]

# 总论

## 思维导图

思维导图见此链接 [https://s.shutu.cn/w/1ptl7l](https://s.shutu.cn/w/1ptl7l)

后续会做成图片或文件的形式放在这里。



# 1 基础

|      | 二进制说明                                  |
| ---- | ------------------------------------------- |
| bit  | bit , 位, 比特, 比特位.                     |
| B    | 字节Byte, 1B=8bit, **sizeof返回值**         |
| KB   | 千字节, kilobyte, 1KB = 1024B = 2^10B       |
| MB   | 兆字节, 1MB = 1024KB = 2^10KB               |
| GB   | 吉字节, 1GB = 1024MB = 2^10MB               |
| TB   | 万亿字节, 太字节, 1TB = 1024GB = 2^10GB     |
|      | 1 TB = 2^10 GB = 2^20 MB = 2^30 KB = 2^40 B |

## 1.1 预处理

|          | 预处理指令说明                            |
| -------- | ----------------------------------------- |
| #include | 包含头文件                                |
| #define  | 定义宏                                    |
| #undef   | 取消宏                                    |
| #ifdef   | 条件编译, ,#ifndef,#if,#elif,#else,#endif |
| #line    | 用于改变编译器报告的行号和文件名(不常用)  |
| #error   | 用于在预处理阶段生成一个错误消息          |

|      | 预处理运算符说明                                             |
| ---- | ------------------------------------------------------------ |
| #    | **字符串化运算符**,将宏参数转换为用双引号括起来的字符串字面量 |
| ##   | **连接运算符**，连接两个标记以形成一个标记                   |
| ...  | 可变参数宏, 用的不多.                                        |

|                |                                          |
| -------------- | ---------------------------------------- |
| **`__cplusplus`** | c++始终定义的宏, 表示编译的是c++代码     |
| **`__DATE__`** | 程序被编译的日期, 格式为 "Mmm dd yyyy" |
| **`__TIME__`** | 程序被编译的时间,格式为 "hh:mm:ss"     |
| **`__FILE__`** | 当前源代码文件的名称,字符串                 |
| **`__LINE__`** | 源代码文件中的当前行号,整型                |
| **`__func__`** | 预定义的标识符, (C++11 引入), 当前函数的名称 |
| **`__VA_ARGS__`** | 不是预定义, 在定义可变参数宏 时使用的一个特殊的标记符，用于表示可变参数列表 |



# 2 语法

## 2.1 变量

### 2.1.1 声明与定义

|      | 含义                                |
| ---- | ----------------------------------- |
| 声明 | 声明类型和名字, extern声明，        |
| 定义 | 声明类型和名字, 并**分配存储空间**. |

### 2.1.2 基础类型 固定类型 隐式转换 字面值 转移字符

| 基础类型    | linux32(Byte) | linux64(Byte) | win32 |
| ----------- | ------------- | ------------- | ----- |
| bool        | 1             | 1             |       |
| char        | 1             | 1             |       |
| short       | 2             | 2             |       |
| int         | 4             | 4             |       |
| long        | **4**         | **8**         |       |
| long long   | 8             | 8             |       |
| float       | 4             | 4             |       |
| double      | 8             | 8             |       |
| long double | **12**        | **16**        |       |
| pointer *   | **4**         | **8**         |       |

固定长度基础类型如下表所示：

`intptr_t`和`uintptr_t`的大小取决于平台，在特定平台上是固定的。

| cstdint | 说明    |          |          |          |               |
| ------- | ------- | -------- | -------- | -------- | ------------- |
| 整型    | int8_t  | int16_t  | int32_t  | int64_t  | **intptr_t**  |
|         | uint8_t | uint16_t | uint32_t | uint64_t | **uintptr_t** |


| 修饰符   | 解释说明 |
| -------- | -------- |
| signed   | 有符号   |
| unsigned | 无符号   |
| void     | 空类型   |

| 类型转换             | 解释说明                       |
| -------------------- | ------------------------------ |
| 非布尔>>bool         | 0->false, 其他->true           |
| bool>>非bool         | false->0, true->1              |
| 浮点型->整型         | 近似处理, 只保留整型           |
| 整型->浮点型         | 小数部分记作0,可能存在精度损失 |
| 给无符号类型赋超限值 | 取模后的余数                   |
| 给有符号类型赋超限值 | 结果未定义                     |

| 整型字面值常量       | 解释说明       |
| -------------------- | -------------- |
| 20                   | 十进制         |
| 024                  | 八进制         |
| 0x14                 | 十六进制       |
| **浮点型字面值常量** |                |
| 3.14159              |                |
| 3.14159E0            | e/E:科学计数法 |
| **字符与字符串常量** |                |
| 'a'                  | 字符常量       |
| "hello world"        | 字符串常量     |

| 转义字符  |              |              |           |               |        |
| --------- | ------------ | ------------ | --------- | ------------- | ------ |
| 换行符\n  | 横向制表符\t | 纵向制表符\v | 反斜线\\\ | 回车符\r      | 问号\? |
| 单引号\\' | 双引号\\"    | 退格符\b     | 进纸符\f  | 报警/响铃符\a |        |



**指定字面值的类型:**

| 前缀     | 字符/字符串字面值类型   |
| -------- | ----------------------- |
| u        | char16_t, unicode16字符 |
| U        | char32_t, unicode32字符 |
| L        | wchar_t, 宽字符         |
| u8       | char, UTF-8             |
| **后缀** | **整型字面值**          |
| u/U      | unsigned                |
| l/L      | long                    |
| ll/LL    | long long               |
| **后缀** | **浮点型字面值**        |
| f/F      | float                   |
| l/L      | long double             |

### 2.1.2  派生类型

#### 2.1.2.1 数组

```
声明和初始化数组
int arr[5] = {1, 2, 3, 4, 5}; // 声明一个整型数组并初始化  
char str[] = "Hello"; // 声明一个字符数组并初始化

数组的长度
int length = sizeof(arr) / sizeof(arr[0]); // 计算数组长度

多维数组
int matrix[3][4] = {{1, 2, 3, 4}, {5, 6, 7, 8}, {9, 10, 11, 12}}; // 二维整型数组
```

#### 2.1.2.2 指针

NULL指针：空指针，值为0.

普通指针：

```
int var = 10; // 声明一个整型变量  
int *ptr; // 声明一个整型指针变量
ptr = &var; // 将var的地址赋给ptr指针
int value = *ptr; // 通过指针访问变量的值
```

指向指针的指针：

```
int x = 10; // 声明一个整型变量  
int *p = &x; // 声明一个整型指针变量，并将x的地址赋给它  
int **pp = &p; // 声明一个整型指向指针的指针变量，并将p的地址赋给它 
```

#### 2.1.2.3 struct结构体

```
声明
struct Person {  
    std::string name;  
    int age;  
};  

定义:
struct Student
{
    int Code;
    char Name[20];
    char Sex;
    int Age;
}Stu,StuArray[10],*pStu;

初始化
Person p = {"Alice", 25};  

```

#### 2.1.2.4 enum枚举

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
```

#### 2.1.2.5 union联合体

可以在**同一块内存位置**存储**不同**的数据类型, 任意一时间**只能存储一种**，类型长度以**最长**的为准

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

```
struct BitField {  
    unsigned int field1 : 5;  // 使用5位存储数据  
    unsigned int field2 : 3;  // 使用3位存储数据  
    unsigned int field3 : 2;  // 使用2位存储数据  
};  
```

### 2.1.3 typedef 自定义类型

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

### 2.1.4 关联

#### 2.1.4.1 指针和函数

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

#### 2.1.4.2 指针和数组

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

#### 2.1.4.3 指针和const

|                  | 说明：                                                       |
| ---------------- | ------------------------------------------------------------ |
| 指针**常量**     | 本质是**常量**, 指针类型的常量, 指向不可修改, 指向的值可以修改. |
| 常量**指针**     | 本质是**指针**, 指向常量; 指向可修改, 指向的值不可修改.      |
| 指向常量的常指针 | 指针和指向都是常量                                           |
| **写法根本**     | **const靠右修饰原则**                                        |

指针**常量**的用法

```
int x = 10;  
int * const ptr = &x;  
// *ptr = 20;  // 这是合法的，会改变x的值为20  
// ptr++;      // 这是非法的，因为ptr是一个常量指针
```

常量**指针**的用法

```
int x = 10;  
const int * ptr = &x;  
int const * ptr = &x;
// *ptr = 20;  // 这是非法的，因为ptr指向一个常量  
// ptr++;      // 这是合法的，因为ptr本身不是常量
```

指向常量的常指针:

```
int x = 10;  
const int * const ptr = &x;  
// *ptr = 20;  // 这是非法的，因为ptr指向一个常量  
// ptr++;      // 这也是非法的，因为ptr本身是一个常量指针
```

#### 2.1.4.4 define,typedef,函数,inline,const

|         | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| #define | 预处理指令,只替换,不求解,无作用域,无优先级,无安全检查,内存开销大, 不便于调试, |
| typedef | 类型别名, 有类型安全, 便于阅读和维护                         |
| 函数    | 有作用域, 类型安全, 好调试追踪, 好传参                       |
| inline  | 有作用域, 编译时处理, 类型安全, 便于调试,                    |
| const   | 有作用域, 编译时处理, 类型安全, 便于调试                     |
| 建议    | 使用typedef,函数,inline,const                                |

#### 2.1.4.5 struct 和 class

| 说明         | struct   | class    |
| ------------ | -------- | -------- |
| 默认访问权限 | public   | private  |
| 继承方式     | public   | private  |
| 通常用法     | 表示数据 | 表示行为 |

#### 2.1.4.6 强制类型转换

|                  | 说明                                                         |
| ---------------- | ------------------------------------------------------------ |
| static_cast      | 基础类型转换, 指针与引用转换, 基类与派生类转换(无运行时检查) |
| dynamic_cast     | 基类指针/引用转换为派生类指针/引用, 有运行时类型检查, 失败返回空指针 |
| const_cast       | 添加或移除类型的`const`或`volatile`限定符                    |
| reinterpret_cast | 不同类型指针间的转换, 整型转指针, 无类型检查                 |

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
int* p = const_cast<int*>(&i); // 移除const限定符（不安全）  

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

## 2.2 类型限定符

|              | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| static       | 静态局部变量, 静态全局变量, 静态全局函数,静态成员变量,静态成员函数 |
| extern       | 用于全局函数/全局变量的声明                                  |
| const        | 该变量的值不能被修改                                         |
| register     | **已废弃**, 寄存器变量，被频繁使用，可存储在CPU的寄存器中，以提高程序的运行效率， |
| volatile     | 该变量的值可能会被程序以外的因素改变，如硬件或其他线程       |
| mutable      | 表示类中的成员变量可以在 const 成员函数中被修改              |
| thread_local | c++11开始, 仅在其创建的线程上可访问. 跟随线程的声明周期创建和销毁. |

|                | 说明                                                       |
| -------------- | ---------------------------------------------------------- |
| static局部变量 | 代码块可见                                                 |
| static全局变量 | 本文件可见                                                 |
| static全局函数 | 本文件可见                                                 |
| static成员变量 | 类内定义, 类外初始化, 可类名::直接访问, 所有类对象共享一份 |
| static成员函数 | 可类名::直接访问, 只能访问静态成员变量和静态成员函数,      |

static:

```
void foo() {  
    static int count = 0; // 静态局部变量，只初始化一次，程序结束时销毁  
    count++;  
}  

static int global_var = 42; // 静态全局变量，只在定义它的文件中可见  

static void bar() { /* ... */ } // 静态全局函数，同样只在定义它的文件中可见
```

extern

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

## 2.3 变量命名规则

规则（由C++语言标准强制）

1. **字母、数字和下划线**：变量名只能包含字母（a-z, A-Z）、数字（0-9）和下划线（_）。
2. **不能以数字开头**：变量名不能以数字开头，但可以以字母或下划线开头。
3. **区分大小写**：C++是区分大小写的语言，因此`variable`、`Variable`和`VARIABLE`是三个不同的变量名。
4. **不能是关键字**：变量名不能是C++的保留关键字，如`int`、`for`、`while`等。
5. **无特殊字符**：除了下划线（_）外，不能使用其他特殊字符（如`@`、`#`、`$`等）来命名变量。
6. **无空格**：变量名中不能包含空格。

## 2.4 命名空间

命名空间（namespace），防止同名冲突。

用法：

- using namespace【命名空间】; 不推荐，可能发生冲突
- using【命名空间】::【变量名】

## 2.5 运算符

|        |      |      |      |      |      |      |      |      |
| ------ | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 算术   | +    | -    | *    | /    | %    | ++   | --   |      |
| 关系   | ==   | !=   | >    | <    | >=   | <=   |      |      |
| 逻辑   | &&   | \|\| | !    |      |      |      |      |      |
| 位运算 | &    | \|   | ^    | ~    | <<   | >>   |      |      |
| 赋值   | =    | +=   | -=   | *=   | /=   | %=   | <<=  | >>=  |
|        | &=   | ^=   | \|=  |      |      |      |      |      |
| 成员   | .    | ->   | ::   |      |      |      |      |      |
| 条件   | ?:   |      |      |      |      |      |      |      |

| 其他       | 说明                                 |
| ---------- | ------------------------------------ |
| sizeof     | 计算类型或变量的大小,以字节为单位    |
| new/delete | 动态内存分配/释放                    |
| ()         | 函数调用运算符                       |
| []         | 数组下标运算符                       |
| *          | 指针解引用运算符，也用于声明指针类型 |
| &          | 取地址运算符，也用于声明引用类型     |

## 2.6 循环

|          | 说明                 |
| -------- | -------------------- |
| 循环语句 | for, while, do while |
| 修饰符   | break, continue      |

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

## 2.7 条件

|        | 说明                                              |
| ------ | ------------------------------------------------- |
| if     | if,else if, else                                  |
| switch | switch, case, break, default. 只能用于整型/枚举值 |

```
#include <iostream>  
using namespace std;  
  
int main() {  
    int number = 10;  
    if (number > 15) {  
        cout << "Number is greater than 15." << endl;  
    } else if (number == 10) {  
        cout << "Number is equal to 10." << endl;  
    } else {  
        cout << "Number is less than 10." << endl;  
    }  
    return 0;  
}  
// 输出：Number is equal to 10.
```

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



### 2.8.1 参数传递

|            | 说明                                       |
| ---------- | ------------------------------------------ |
| 传值       | 创建副本,  原值不可修改, 涉及数据拷贝开销. |
| 传引用     | 别名, 避免拷贝提高效率, 可修改原值         |
| 传指针     | 传递变量地址, 可访问和修改                 |
| 传数组指针 | 数组指针和长度需要同时传递, 可修改原值     |

```
void modifyArray(int* arr, int size) {  
    for (int i = 0; i < size; i++) {  
        arr[i] += 5; // 修改数组元素  
    }  
}  
  
int main() {  
    int myArray[] = {1, 2, 3, 4, 5};  
    int size = sizeof(myArray) / sizeof(myArray[0]);  
    modifyArray(myArray, size); // 传递数组和大小  
      
    // 输出修改后的数组  
    for (int i = 0; i < size; i++) {  
        cout << myArray[i] << " "; // 输出 6 7 8 9 10  
    }  
}
```

### 2.8.2 默认参数

默认参数:

- 只能从右往走定义, 必须位于非默认参数的右侧;
- 只在函数声明中指定一次, 多个声明中必须保持一致;
- 函数定义(实现)中不需要再次指定.

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

### 2.8.3 返回值

返回值说明：

- 当函数**返回局部变量的值**时，会发生**值的拷贝**。局部变量在函数退出时被销毁，但它们的值已经被拷贝给调用者，所以这是安全的。
- **不要返回局部变量的引用或指针**，因为局部变量在函数返回后不再存在，这将导致悬挂引用或野指针。

- 可以返回**局部静态变量或全局变量的引用**，因为这些变量在函数返回后仍然存在。

返回动态分配内存的指针

- 如果函数返回指向动态分配内存的指针（例如使用`new`操作符），调用者有责任在适当的时候释放这块内存（使用`delete`操作符），以避免内存泄漏。
- 更好的做法是使用智能指针（如`std::unique_ptr`或`std::shared_ptr`），它们可以自动管理内存的生命周期。

### 2.8.4 递归函数

| 递归函数定义:                                         |
| ----------------------------------------------------- |
| 直接或间接调用自身的函数, 用于将复杂问题分解为子问题. |

格式:

```
返回类型 函数名(参数列表) {  
    // 基本情况（base case）  
    if (满足某个条件) {  
        // 直接返回结果，不再递归  
        return 结果;  
    }  
      
    // 递归情况（recursive case）  
    // 将问题分解为更小的子问题，并递归调用自身  
    return 函数名(修改后的参数);  
}
```

使用递归函数时需要注意以下几点：

1. 确保递归有一个明确的终止条件，否则会导致无限递归，最终引起栈溢出。
2. 递归调用应该使问题规模减小，逐步逼近基本情况。
3. 对于大数据量或深层次递归，需要考虑递归的效率和栈空间的使用。有时候迭代（循环）可能是更好的选择。
4. 在设计递归函数时，尽量保持函数简洁易懂，避免复杂的递归逻辑。



示例:

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

### 2.8.5 内联函数

内联函数的优缺点:

- 优点:效率提升, 优化编译, 代码简洁
- 缺点:代码膨胀,编译时间增加,无法控制内联, 不适合大型函数.

不易做为内联函数的:

- 大型函数
- 递归函数
- 含有静态局部变量的函数
- 含有循环/复杂控制流的函数
- 虚函数：**动态绑定与静态绑定的冲突**
- 构造和析构函数： 对象构造和销毁的复杂性，编译器限制。

使用注意事项:

- **内联不是强制的** 即使函数被声明为`inline`，编译器也有权选择不进行内联。内联仅是一种优化提示，而非强制指令。
- **不要过度依赖内联**：过度使用内联可能导致代码膨胀和其他潜在问题。应该谨慎地选择哪些函数进行内联。
- **内联函数通常定义在头文件中**：由于内联函数需要在每个调用点可见，因此它们通常定义在头文件中。
- **类内定义的函数默认为内联函数**;

### 2.8.6 函数重载

函数重载: 

- 指**同一作用域内**,  具有**相同名字但参数列表不同**的函数. 
- 参数列表不同包括: 参数类型, 个数, 顺序.  
- **与返回类型无关**.
- 函数重载是在编译期间确定, 称为静态绑定.
- 适当使用可提高可读性和可维护性, 过度使用导致代码难以理解和维护.

```
#include <iostream>  
#include <string>  
  
// 函数重载示例  
// 第一个版本：接受两个整数  
void printSum(int a, int b) {  
    std::cout << "The sum of " << a << " and " << b << " is " << a + b << std::endl;  
}  
  
// 第二个版本：接受两个浮点数  
void printSum(double a, double b) {  
    std::cout << "The sum of " << a << " and " << b << " is " << a + b << std::endl;  
}  
  
// 第三个版本：接受一个字符串和一个整数  
void printSum(const std::string& str, int num) {  
    std::cout << "The string is " << str << " and the number is " << num << std::endl;  
    // 注意：这里并没有进行相加操作，因为字符串和整数的相加没有定义  
}  
  
int main() {  
    printSum(3, 4);          // 调用第一个版本  
    printSum(2.5, 3.2);      // 调用第二个版本  
    printSum("Hello", 5);    // 调用第三个版本  
    return 0;  
}
```

# 3 面向对象

## 3.1 概念

抽象 : 只展示必要信息，隐藏不必要的细节。

封装 : 指将数据（属性）和操作数据的方法（函数）封装在一个类中，保护私有数据。

继承 : 一个类（子类）继承另一个类（父类）的属性和方法，也称基类和派生类。

多态 : 通过基类指针或引用，来调用派生类的方法。

## 3.2 class类

### 3.2.1 访问修饰符

|           | 说明                         |
| --------- | ---------------------------- |
| public    | 公开，无访问限制             |
| protected | 只在类内部和派生类中可访问   |
| private   | 只在类内部和**友元**函数访问 |

示例1：

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

示例2：

```
#include <iostream>  
  
// 基类 Shape  
class Shape {  
protected:  // 受保护的成员  
    int width, height;  
  
public:  
    // 设置宽度和高度的公有方法  
    void setWidth(int w) { width = w; }  
    void setHeight(int h) { height = h; }  
};  
  
// 派生类 Rectangle 继承自 Shape  
class Rectangle : public Shape {  
public:  
    // 计算面积的公有方法  
    int getArea() {  
        return (width * height);  // 可以直接访问 protected 成员  
    }  
};  
  
int main() {  
    Rectangle rect;  
  
    // 使用公有方法设置宽度和高度  
    rect.setWidth(5);  
    rect.setHeight(7);  
  
    // 输出对象的面积  
    std::cout << "Total area: " << rect.getArea() << std::endl;  
  
    // 下面的代码会产生编译错误，因为 width 和 height 是 protected 成员  
    // std::cout << "Width: " << rect.width << std::endl;  // 错误：不能访问 protected 成员  
    // std::cout << "Height: " << rect.height << std::endl; // 错误：不能访问 rotected 成员  
  
    return 0;  
}
```

### 3.2.2 特殊成员函数

特殊成员函数，**不定义时, 编译器会自动生成默认的**：

- 构造函数
- 析构函数
- 拷贝构造函数
- 赋值运算
- 地址运算符
- 移动构造函数
- 移动赋值

代码示例:

```
class MyClass {  
public:  
    // 默认构造函数  
    MyClass() {  
        // 初始化代码  
    }  
  
    // 析构函数  
    ~MyClass() {  
        // 清理代码  
    }  
  
    // 拷贝构造函数  
    MyClass(const MyClass& other) {  
        // 拷贝代码  
    }  
  
    // 拷贝赋值运算符  
    MyClass& operator=(const MyClass& other) {  
        if (this != &other) {  
            // 赋值代码  
        }  
        return *this;  
    }  
  
    // 移动构造函数  
    MyClass(MyClass&& other) noexcept {  
        // 移动代码  
    }  
  
    // 移动赋值运算符  
    MyClass& operator=(MyClass&& other) noexcept {  
        // 移动赋值代码  
        return *this;  
    }  
  
private:  
    // 类成员  
};
```

### 3.2.3 class 和 static

|                    | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| static静态成员变量 | 只有一份，所有类共享；类中申明，类外定义和初始化。可通过 :: 或 对象来访问。 |
| static静态成员函数 | 只能访问静态成员变量和静态成员函数； 可通过 :: 来访问。      |

**static 成员的访问属性也分为public/protected/private**.

代码示例：

```
// header file: MyClass.h  
#ifndef MYCLASS_H  
#define MYCLASS_H  
  
class MyClass {  
public:  
    // 静态数据成员的声明  
    static int staticVar;  
  
    // 静态函数成员的声明  
    static void staticFunc();  
  
    // 非静态函数成员  
    void nonStaticFunc();  
};  
  
// 静态数据成员的定义和初始化  
// 注意：这通常在类的实现文件(.cpp)中完成，但为了简洁，这里放在头文件中了  
int MyClass::staticVar = 0;  
  
#endif // MYCLASS_H  
```

```
// implementation file: MyClass.cpp  
#include "MyClass.h"  
#include <iostream>  
  
// 静态函数成员的定义  
void MyClass::staticFunc() {  
    std::cout << "Static function called. StaticVar: " << staticVar << std::endl;  
}  
  
// 非静态函数成员的定义  
void MyClass::nonStaticFunc() {  
    std::cout << "Non-static function called." << std::endl;  
    // 可以访问静态成员  
    staticVar++;  
    staticFunc();  
}  
```

```
// main.cpp  
#include "MyClass.h"  
  
int main() {  
    // 访问静态数据成员  
    MyClass::staticVar = 42;  
  
    // 调用静态函数成员  
    MyClass::staticFunc();  
  
    // 创建对象并调用非静态函数成员  
    MyClass obj;  
    obj.nonStaticFunc();  
  
    // 注意：尽管我们调用了nonStaticFunc()一次，但staticVar增加了两次，  
    // 因为nonStaticFunc()内部也调用了staticVar++和staticFunc()  
  
    return 0;  
}
```

### 3.2.4 class 和 const

**const对象依然可以使用 public/protected/private修饰**.

|                        | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| 常量成员函数           | 不能修改类的**非静态数据成员**, 定义时加const                |
| 常量成员变量           | 必须在构造函数初始化列表中进行初始化，且后续不能修改         |
| 静态常量成员函数       | 属于类，静态常量整型可在类内直接初始化，其他必须在类外定义和初始化. |
| 常量对象               | 只能调用常量成员函数.                                        |
| 常量引用和常量指针成员 | 必须被初始化, 且不能通过它们来修改所引用的数据。             |

常成员函数:

```
class MyClass {  
public:  
    int value;  
  
    MyClass(int v) : value(v) {}  
  
    // 常量成员函数  
    int getValue() const {  
        return value;  
        // value = 42; // 错误！不能在常量成员函数中修改非静态数据成员  
    }  
};  
  
int main() {  
    const MyClass obj(10); // 声明一个常量对象  
    int val = obj.getValue(); // 可以调用常量成员函数  
    // obj.value = 20; // 错误！obj 是常量对象  
    return 0;  
}
```

常成员变量:

```
class MyClass {  
public:  
    const int constantValue; // 常量成员  
  
    MyClass(int value) : constantValue(value) {} // 在初始化列表中初始化常量成员  
};  
  
int main() {  
    MyClass obj(10);  
    // obj.constantValue = 20; // 错误！不能修改常量成员  
    return 0;  
}
```

静态常量成员:

```
class MyClass {  
public:  
    static const int staticConstant = 42; // 静态常量整型成员，类内初始化  
    static const double staticConstantDouble; // 静态常量非整型成员，类内声明  
};  
  
const double MyClass::staticConstantDouble = 3.14; // 类外定义和初始化  
  
int main() {  
    int val = MyClass::staticConstant; // 访问静态常量成员  
    double dVal = MyClass::staticConstantDouble;  
    return 0;  
}
```

常量引用和指针成员:

```
class MyClass {  
public:  
    const int& ref; // 常量引用成员  
    const int* const ptr; // 指向常量的常量指针成员  
  
    MyClass(int& r, int* p) : ref(r), ptr(p) {}  
};  
  
int main() {  
    int x = 10;  
    int y = 20;  
    MyClass obj(x, &y);  
    // obj.ref = 30; // 错误！不能通过常量引用来修改数据  
    // obj.ptr = &x; // 错误！ptr 是常量指针，不能改变它所指向的地址  
    // *obj.ptr = 40; // 错误！不能通过指向常量的指针来修改数据  
    return 0;  
}
```



## 3.3 class继承

### 3.3.1 概念

一个类继承另一个类，被继承的叫父类/基类，继承的叫子类/派生类。

### 3.3.2 继承控制(访问权限)

第一行：基类的成员访问属性，第一列：派生类对基类的继承类型。其余是基类成员在派生类中的访问属性。

|                | public 成员 | protected 成员 | private 成员 |
| -------------- | ----------- | -------------- | ------------ |
| public 继承    | public      | protected      | private      |
| protected 继承 | protected   | protected      | private      |
| private 继承   | private     | private        | private      |

调用顺序:

构造函数: 先调用基类, 再调用派生类.

析构函数: 先调用派生类, 再调用基类.

### 3.3.3 重载、覆盖(重写)、隐藏

|      | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| 重载 | **Overload**,同一作用域, 名字相同参数列表不同的函数.         |
| 覆盖 | **Override**, 重写, 派生类中与基类具有名字+参数列表+返回类型均相同的**虚函数**, 实现替换. |
| 隐藏 | **Hide**派生类的函数与**基类的非虚函数**具有相同名字, 基类的函数会被隐藏. |

|      | 作用域       | 名字+参数列表+返回类型               | 虚函数?  |
| ---- | ------------ | ------------------------------------ | -------- |
| 重载 | 同一作用域   | 名字相同, 参数列表不同, 返回类型无关 | 无关     |
| 覆盖 | 基类和派生类 | 名字/参数列表/返回类型,均相同        | 虚函数   |
| 隐藏 | 基类和派生类 | 名字相同                             | 非虚函数 |

注意点: 隐藏, 基类指针/引用调用该函数, 调用的是基类的版本; 派生类对象被当做基类对象使用时, 直接调用该函数,则会因为名字隐藏而导致编译错误/警告.

```
重载
void foo(int a);    // 函数foo，接受一个int参数  
void foo(double a); // 函数foo的重载版本，接受一个double参数
```

```
覆盖
class Base {  
public:  
    virtual void bar() { /* 基类实现 */ }  
};  

class Derived : public Base {  
public:  
    void bar() override { /* 派生类覆盖实现 */ }  
};
```

```
隐藏
class Base {  
public:  
    void baz() { /* 基类实现 */ }  
};  

class Derived : public Base {  
public:  
    void baz(int a) { /* 派生类隐藏了基类的baz()函数 */ }  
};
```

隐藏完整示例:

```
#include <iostream>  
  
class Base {  
public:  
    void show() {  
        std::cout << "Base::show()" << std::endl;  
    }  
};  
  
class Derived : public Base {  
public:  
    // 这里的show函数隐藏了基类中的show函数  
    void show(int x) {  
        std::cout << "Derived::show(int) with value: " << x << std::endl;  
    }  
};  
  
int main() {  
    Derived d;  
    // 调用派生类的show函数，需要传递一个参数  
    d.show(5);  
      
    // 错误：尝试调用没有参数的show函数，但编译器找不到这样的函数  
    // 因为基类的show函数被隐藏了  
    // d.show(); // 这行会导致编译错误  
  
    // 正确：使用基类作用域运算符来调用基类中被隐藏的show函数  
    d.Base::show();  
  
    return 0;  
}
```

### 3.3.4 多继承与虚继承

**多继承**: 同事从多个基类继承.

```
class Base1 {  
    // ...  
};  
  
class Base2 {  
    // ...  
};  
  
class Derived : public Base1, public Base2 {  
    // Derived 类同时继承自 Base1 和 Base2  
};
```

**虚继承** : 解决多继承中存在多个同一基类的问题.

```
class Top {  
    // ...  
};  
  
class Left : virtual public Top {  
    // ...  
};  
  
class Right : virtual public Top {  
    // ...  
};  
  
class Bottom : virtual public Left,virtual public Right {  
    // 由于 Left 和 Right 虚继承自 Top，Bottom 类中只有一个 Top 的子对象  
};
```

**虚继承原理**: 

1. **虚基类指针（Virtual Base Class Pointer）**：
   当一个类虚继承自一个基类时，编译器会在**派生类对象中**插入一个**指向虚基类的指针**，通常称为虚基类指针（vptr）。这个指针用于定位虚基类子对象在派生类对象中的位置。

2. **虚基类表（Virtual Base Class Table）**：
   与虚函数表（vtable）类似，编译器可能会为每个包含虚基类的对象生成一个虚基类表（vbtable）。虚基类表中包含了调整派生类对象指针以正确指向虚基类成员的偏移量。

3. **内存布局**：
   在包含虚基类的派生类对象中，虚基类子对象通常位于对象的内存布局的开始部分。紧接着是各个直接基类的子对象，这些子对象中不再包含虚基类子对象（因为已经被共享）。最后是派生类自己的成员。

4. **构造与析构**：
   在构造派生类对象时，虚基类的构造函数首先被调用，且只调用一次。接着是直接基类的构造函数，最后是派生类的构造函数。析构函数的调用顺序与构造函数相反。

   构造：虚基类的构造(只一次)-》直接基类的构造-》派生类的构造

   析构：相反。

5. **访问控制**：
   虚继承不会改变基类的访问权限。如果基类中的成员在基类中是私有的，那么它在派生类中仍然是不可访问的。

### 3.3.5 虚函数(说明,原理,注意事项)

虚函数是实现**动态多态性的关键机制**, 通过基类指针/引用调用派生类对象实现.

**虚函数的原理**：

1. **虚函数表（vtable）**：
   
   虚函数表是一个存储虚函数地址的数组.
   
   当一个类中有虚函数时,编译器 **编译时**会为该类**创建**一个虚函数表, 并**初始化**. 
   
   如果派生类重写了基类的虚函数，则虚表中对应的条目将指向派生类的函数实现.
   
2. **虚指针（vptr）**：

   指向虚函数表的指针，称为虚指针(vptr).

   **编译时**编译器会在类的内存布局中**预留一个指针**大小的空间来存放vptr， 这个空间是每个对象实例的一部分.

   对象实例化**构造函数的列表初始化**时，对虚指针进行初始化为指向该类的vtable的地址。

   每个对象都有自己的虚指针，为对象的第一个数据成员.

3. **动态绑定**：
   当通过基类指针或引用调用虚函数时，程序会在运行时查看该指针或引用所指向对象的虚指针，进而查找虚函数表，以确定应该调用哪个函数。这就是动态绑定的过程。

4. **重写（Override）**：
   在派生类中，如果提供了一个与基类虚函数签名相同的函数，那么这个函数将重写基类的虚函数。在派生类对象的虚函数表中，相应的槽位会指向派生类的这个函数。

代码示例: 

```
//声明虚函数
class Base {  
public:  
    virtual void func() { /* 基类实现 */ }  
};

//继承并重写虚函数
class Derived : public Base {  
public:  
    void func() override { /* 派生类实现 */ }  
};

//通过基类指针或引用调用虚函数
//指针
Base *ptr = new Derived();  
ptr->func();  // 将调用 Derived 类的 func 实现  
delete ptr;   // 不要忘记删除动态分配的对象
//引用
Base &ref = *static_cast<Derived*>(new Derived());  
ref.func();  // 将调用 Derived 类的 func 实现  
// 注意：这里存在内存泄漏，因为 new 返回的对象没有被删除  
// 在实际代码中，应避免这种写法，或者使用智能指针来管理资源
```

**虚函数使用注意事项**:

1. 派生类重写虚函数时, 加上virtual 和 override, 便于编译器检查.
2. 避免隐藏虚函数: 若派生类的函数与基类的虚函数同名不同参数列表, 将会导致该问题, 要保持一致正确重写.
3. 析构函数声明为虚函数: 通过基类指针删除派生类对象时, 调用基类的析构, 防止出现资源泄漏.
4. 构造函数不能为虚函数:  构造函数调用时,对象类型已确定, 无需动态绑定. 构造函数创建对象时, 对象还没有实例化完成, 内存空间还没有, **无法找到虚表**. 
5. 虚函数不能删除/修改/中间插入, 否则会导致虚表错乱, 函数调用出错.

### 3.3.6 纯虚函数和抽象类

**纯虚函数**: 声明函数时最后加 = 0, 表示为纯虚函数, 只有声明没有定义实现.

**抽象类**: 有纯虚函数的类称为抽象类, 抽象类不能实例化, 一般作为基类. 

​		 派生类继承时必须实现纯虚函数, 否则也不能实例化.

示例:

```
#include <iostream>  
  
// 抽象基类 Shape  
class Shape {  
public:  
    // 纯虚函数  
    virtual void draw() const = 0; // 注意 "= 0" 表示这是一个纯虚函数  
    virtual ~Shape() = default;    // 虚析构函数，虽然不是必需的，但通常是一个好习惯  
};  
  
// 派生类 Circle  
class Circle : public Shape {  
public:  
    void draw() const override {  
        std::cout << "Drawing a circle..." << std::endl;  
    }  
};  
  
// 派生类 Rectangle  
class Rectangle : public Shape {  
public:  
    void draw() const override {  
        std::cout << "Drawing a rectangle..." << std::endl;  
    }  
};  
  
int main() {  
    // Shape s; // 错误！不能实例化抽象类  
  
    Circle c;  
    c.draw(); // 输出: Drawing a circle...  
  
    Rectangle r;  
    r.draw(); // 输出: Drawing a rectangle...  
  
    return 0;  
}
```



## 3.4 多态

c++ 多态分为编译时多态和运行时多态。

|            | 说明                                                     |
| ---------- | -------------------------------------------------------- |
| 编译时多态 | 静态多态, 静态绑定, 编译时确定. 有函数**重载**，**模板** |
| 运行时多态 | 动态多态, 动态绑定, 运行时确定.  虚函数                  |

```
#include <iostream>  
#include <string>  
  
// 编译时多态：函数重载  
void print(int x) {  
    std::cout << "Printing int: " << x << std::endl;  
}  
  
void print(const std::string& str) {  
    std::cout << "Printing string: " << str << std::endl;  
}  
  
// 运行时多态：虚函数  
class Base {  
public:  
    virtual void sayHello() const {  
        std::cout << "Hello from Base!" << std::endl;  
    }  
    virtual ~Base() = default;  
};  
  
class Derived : public Base {  
public:  
    void sayHello() const override {  
        std::cout << "Hello from Derived!" << std::endl;  
    }  
};  
  
int main() {  
    // 编译时多态示例  
    print(42);          // 调用 print(int)  
    print("Hello");     // 调用 print(const std::string&)  
  
    // 运行时多态示例  
    Base* basePtr = new Derived();  
    basePtr->sayHello();  // 动态绑定到 Derived::sayHello()  
    delete basePtr;  
  
    return 0;  
}
```



# 4 代码复用



## 4.1 重载

重载: 同一个作用域, 函数名相同, 参数列表不同的函数, 返回类型无关.

### 4.1.1 函数重载

函数重载: 同一个作用域, 函数名相同, 参数列表不同得函数.  

参数列表: 包括类型, 个数, 顺序.

代码示例:

```
#include <iostream>  
#include <string>  
  
// 函数重载示例：print函数  
  
// 第一个版本，用于打印整数  
void print(int value) {  
    std::cout << "Printing int: " << value << std::endl;  
}  
  
// 第二个版本，用于打印浮点数  
void print(float value) {  
    std::cout << "Printing float: " << value << std::endl;  
}  
  
// 第三个版本，用于打印双精度浮点数  
void print(double value) {  
    std::cout << "Printing double: " << value << std::endl;  
}  
  
// 第四个版本，用于打印字符串  
void print(const std::string& value) {  
    std::cout << "Printing string: " << value << std::endl;  
}  
  
// 第五个版本，用于打印字符  
void print(char value) {  
    std::cout << "Printing char: " << value << std::endl;  
}  
  
int main() {  
    // 调用不同版本的print函数  
    print(42);           // 调用第一个版本，打印整数  
    print(3.14f);        // 调用第二个版本，打印浮点数  
    print(2.71828);      // 调用第三个版本，打印双精度浮点数（注意这里没有'f'后缀，所以是double类型）  
    print("Hello, World!"); // 调用第四个版本，打印字符串  
    print('A');          // 调用第五个版本，打印字符  
  
    return 0;  
}
```

输出:

```
Printing int: 42  
Printing float: 3.14  
Printing double: 2.71828  
Printing string: Hello, World!  
Printing char: A
```

### 4.1.2 运算符重载

操作符重载格式:

```
返回值 operator操作符(参数)
```

示例:

```
#include <iostream>  
  
// 自定义复数类  
class Complex {  
public:  
    double real;  
    double imag;  
  
    Complex(double r = 0.0, double i = 0.0) : real(r), imag(i) {}  
  
    // 重载+操作符  
    Complex operator+(const Complex& other) const {  
        return Complex(real + other.real, imag + other.imag);  
    }  
  
    // 输出复数  
    void print() const {  
        std::cout << "(" << real << ", " << imag << ")" << std::endl;  
    }  
};  
  
int main() {  
    Complex c1(1.0, 2.0);  
    Complex c2(3.0, 4.0);  
    Complex sum = c1 + c2; // 使用重载的+操作符  
    sum.print(); // 输出结果  
    return 0;  
}
```

**不可重载操作符**：

|               | 不可重载操作符说明 |
| ------------- | ------------------ |
| **.**         | 成员访问运算符     |
| **.**, **->** | 成员指针访问运算符 |
| **::**        | 域运算符           |
| **sizeof**    | 长度运算符         |
| **?:**        | 条件运算符         |
| **#**         | 预处理符号         |
| case          | 4个强制类型转换符  |

下面是可重载的运算符列表：

| 双目算术运算符 | + (加)，-(减)，*(乘)，/(除)，% (取模)                        |
| -------------- | ------------------------------------------------------------ |
| 关系运算符     | ==(等于)，!= (不等于)，< (小于)，> (大于)，<=(小于等于)，>=(大于等于) |
| 逻辑运算符     | \|\|(逻辑或)，&&(逻辑与)，!(逻辑非)                          |
| 单目运算符     | + (正)，-(负)，*(指针)，&(取地址)                            |
| 自增自减运算符 | ++(自增)，--(自减)                                           |
| 位运算符       | \| (按位或)，& (按位与)，~(按位取反)，^(按位异或),，<< (左移)，>>(右移) |
| 赋值运算符     | =, +=, -=, *=, /= , % = , &=, \|=, ^=, <<=, >>=              |
| 空间申请与释放 | new, delete, new[ ] , delete[]                               |
| 其他运算符     | **()**(函数调用)，**->**(成员访问)，**,**(逗号)，**[]**(下标) |

### 4.1.3 重载限制

C++中的操作符重载有一些限制，这些限制旨在保持语言的一致性和防止滥用。以下是一些主要的限制：

1. **至少有一个操作数是用户定义的类型**：
   重载的操作符必须至少有一个操作数是用户自定义类型（类类型、结构体类型或枚举类型）。这是为了防止用户为标准类型重载操作符，从而改变它们原有的语义。

2. **不能违反操作符原有的语法规则**：
   重载的操作符必须保持其原有的操作数个数、语法结构和基本语义。例如，不能将二元操作符重载为单元操作符，也不能改变操作符的优先级或结合性。

3. **不能创建新的操作符**：
   不能定义新的操作符符号。只能重载C++语言中已有的操作符。例如，不能定义一个新的`operator@`。

4. **部分操作符不能被重载**：
   有一些操作符在C++中是不能被重载的，包括：

   - `sizeof`：获取对象或类型的大小。
   - `.*`：成员指针访问。
   - `::`：域解析操作符。
   - `?:`：条件操作符（三元操作符）。
   - 四个类型转换操作符：`const_cast`、`dynamic_cast`、`reinterpret_cast` 和 `static_cast`。

5. **部分操作符只能通过成员函数重载**：
   一些操作符只能通过类的成员函数来重载。这些操作符通常与类的特定对象紧密相关，包括：

   - 赋值操作符 `=`
   - 下标操作符 `[]`
   - 函数调用操作符 `()`
   - 成员访问箭头操作符 `->`

   这些操作符通常需要访问类的私有或受保护成员，因此它们被限制为只能通过成员函数进行重载。

6. **不能改变操作符的优先级和结合性**：
   重载的操作符继承其在语言中的原有优先级和结合性。这意味着，例如，重载的`+`操作符仍然保持其左结合性，并且优先级与原始的加法操作符相同。

7. **重载操作符的参数不能全为默认参数**：
   这会导致编译器在解析表达式时产生歧义，因为它无法确定应该使用哪个重载版本。

8. **返回值类型的限制**：
   虽然大多数操作符的返回值类型可以由用户自定义，但有一些约定和限制。例如，赋值操作符通常返回左操作数的引用，以便支持链式赋值。

9. **二义性的避免**：
   当存在多个可能的操作符重载版本时，编译器必须能够唯一确定应该使用哪个版本。如果编译器无法确定，则会产生编译错误。

在重载操作符时，应仔细考虑这些限制，以确保代码的清晰性、可读性和正确性。

## 4.2 友元

在C++中，`friend`关键字用于声明友元函数或友元类。当一个函数或一个类被声明为另一个类的友元时，它可以访问该类的私有（private）和保护（protected）成员。这是一种突破数据封装和隐藏的方式，应谨慎使用。

友元可以用于以下情况：

1. 当两个类需要紧密协作，并且要求其中一个类能够访问另一个类的私有或受保护成员时。
2. 重载操作符时，特别是当操作符需要访问类的私有或受保护成员时。

### 4.2.1 友元函数

友元函数分为两种：

- 友元函数， friend void ClassB::func(ClassA& a);
- 友元成员函数，

友元函数的主要用途：

1. **重载操作符**：当需要为类类型的对象重载操作符时，友元函数特别有用。例如，重载`<<`操作符以便与`std::ostream`一起使用，或者重载比较操作符如`==`和`<`等。这些操作符通常需要访问类的私有或受保护成员，而友元函数能够直接访问这些成员。
2. **提供对类私有成员的访问**：有时，出于某种原因（如调试、测试或特殊的实用程序函数），你可能想要提供一个能够直接访问类私有成员的函数。虽然这通常被认为是一种破坏封装性的做法，但在某些情况下可能是必要的。
3. **实现回调机制**：在某些设计模式中，可能需要将一个类的私有数据传递给另一个类的方法进行处理。通过将另一个类的方法声明为友元，可以直接访问私有数据而无需通过类的公共接口。
4. **增强两个类之间的协作**：当两个类需要紧密协作时，有时将一个类的方法声明为另一个类的友元可以更高效地共享信息。这样做可以减少不必要的公共接口方法，并且可以直接在两个类之间传递数据。
5. **保持接口的一致性**：在某些情况下，将某些函数作为友元而不是类的成员函数，可以帮助保持类的接口更加一致和简洁。这样做可以避免在类的公共接口中暴露过多的实现细节。

**友元成员函数**：

```
class ClassB; // 前向声明  
  
class ClassA {  
    friend void ClassB::accessPrivateMember(ClassA& a); // 声明ClassB的成员函数为友元  
private:  
    int secret = 42;  
};  
  
class ClassB {  
public:  
    void accessPrivateMember(ClassA& a); // 此函数将能够访问ClassA的私有成员  
};  
  
void ClassB::accessPrivateMember(ClassA& a) {  
    std::cout << "ClassA's secret is: " << a.secret << std::endl; // 直接访问ClassA的私有成员  
}  
  
int main() {  
    ClassA a;  
    ClassB b;  
    b.accessPrivateMember(a); // 输出：ClassA's secret is: 42  
    return 0;  
}
```

**友元函数**：

```
#include <iostream>  
  
class Box {  
    // 声明一个友元函数  
    friend void printWi00dth(Box box);  
  
public:  
    Box() : width(0.0), height(0.0) {}  
  
    // 成员函数，设置宽度和高度  
    void setDimensions(double w, double h) {  
        width = w;  
        height = h;  
    }  
  
private:  
    double width;  
    double height;  
};  
  
// 定义一个友元函数  
void printWidth(Box box) {  
    // 友元函数可以直接访问Box类的私有成员  
    std::cout << "Width of box: " << box.width << std::endl;  
}  
  
int main() {  
    Box box;  
  
    // 使用成员函数设置宽度和高度  
    box.setDimensions(5.0, 10.0);  
  
    // 使用友元函数打印宽度  
    printWidth(box);  
  
    return 0;  
}
```

### 4.2.2 友元类

**含义**

当一个类B被声明为类A的友元类时，类B的成员函数可以访问类A的所有成员，包括私有和保护成员。这是一种突破数据封装的方式，应当谨慎使用，因为它可能破坏对象的封装性和隐藏数据的原则。

**用途**

1. **操作符重载**：当需要重载涉及两个不同类对象的操作符时，常常将一个类声明为另一个类的友元，以便能够访问对方的私有和保护成员。
2. **紧密协作**：在某些情况下，两个类需要非常紧密地协作，以至于一个类需要直接访问另一个类的内部状态。
3. **避免过多的getter/setter方法**：通过友元类，可以直接访问私有成员，而不需要为每个需要访问的成员编写getter和setter方法。

**示例**

```
#include <iostream>  
  
class Box {  
    // 声明FriendClass为友元类  
    friend class FriendClass;  
  
public:  
    Box() : width(0.0), height(0.0) {}  
  
    // 普通的公有成员函数  
    void setDimensions(double w, double h) {  
        width = w;  
        height = h;  
    }  
  
private:  
    double width;  
    double height;  
};  
  
class FriendClass {  
public:  
    void printWidth(Box& box) {  
        // 作为友元类，可以直接访问Box的私有成员width  
        std::cout << "Width of box: " << box.width << std::endl;  
    }  
};  
  
int main() {  
    Box box;  
    FriendClass friendObj;  
  
    // 设置Box的尺寸  
    box.setDimensions(5.0, 10.0);  
  
    // 使用友元类来打印Box的宽度  
    friendObj.printWidth(box);  
  
    return 0;  
}
```

### 4.2.3 互为友元类

当两个类相互声明对方为友元类时，它们被称为“互为友元”。

```
#include <iostream>  
  
class ClassB; // 前向声明  
  
class ClassA {  
    // 声明ClassB为友元类  
    friend class ClassB;  
  
private:  
    int privateDataA = 100;  
  
public:  
    void showBPrivate(ClassB& b);  
};  
  
class ClassB {  
    // 声明ClassA为友元类  
    friend class ClassA;  
  
private:  
    int privateDataB = 200;  
  
public:  
    void showAPrivate(ClassA& a);  
};  
  
// ClassA的成员函数实现  
void ClassA::showBPrivate(ClassB& b) {  
    std::cout << "ClassA can access ClassB's private data: " << b.privateDataB << std::endl;  
}  
  
// ClassB的成员函数实现  
void ClassB::showAPrivate(ClassA& a) {  
    std::cout << "ClassB can access ClassA's private data: " << a.privateDataA << std::endl;  
}  
  
int main() {  
    ClassA a;  
    ClassB b;  
  
    // 互相展示私有数据  
    a.showBPrivate(b); // ClassA can access ClassB's private data: 200  
    b.showAPrivate(a); // ClassB can access ClassA's private data: 100  
  
    return 0;  
}
```



## 4.3 模板

模板编程是一种编程范式，允许编写类型无关的代码。

**模板编程的用途**：

1. **类型无关的代码**：模板允许编写不依赖于特定数据类型的代码。这意味着你可以用相同的逻辑来处理不同类型的数据，提高了代码的重用性。
2. **减少代码冗余**：在没有模板的情况下，对于每一种数据类型，你可能需要编写几乎相同的代码。模板减少了这种冗余，使代码更加简洁。
3. **增加代码灵活性**：模板提供了一种方式来编写更加通用的代码，这些代码可以适应多种不同的数据类型和场景。
4. **编译时多态性**：与运行时的多态性（如虚函数）不同，模板提供了编译时的多态性。编译器在编译时根据提供的类型参数生成相应的代码，这有助于在编译期间捕获类型错误，并且通常没有运行时开销。
5. **优化性能**：由于模板实例化是在编译时完成的，编译器有机会进行针对特定类型的优化，这可能会产生比非模板代码更高的运行效率。
6. **扩展性**：模板可以与C++的其他特性（如操作符重载、异常处理等）结合使用，以创建强大且易于扩展的库和框架。

### 4.3.1 函数模板

**定义**

函数模板是以关键字`template`开始，后跟一个尖括号`<>`中的类型参数列表，然后是函数声明和定义的常规格式。类型参数在函数体内作为占位符使用，当函数模板被实例化时，这些占位符会被具体的类型替换。

```
定义函数模板
template <typename type> ret-type func-name(parameter list)
{
   // 函数的主体
}
```

```
#include <iostream>  
  
// 函数模板声明  
template <typename T>  
void swap(T& a, T& b) {  
    T temp = a;  
    a = b;  
    b = temp;  
}  
  
int main() {  
    int x = 5, y = 10;  
    std::cout << "Before swap: x = " << x << ", y = " << y << std::endl;  
  
    // 实例化函数模板，用于int类型  
    swap(x, y);  
    std::cout << "After swap: x = " << x << ", y = " << y << std::endl;  
  
    double p = 3.14, q = 2.71;  
    std::cout << "Before swap: p = " << p << ", q = " << q << std::endl;  
  
    // 实例化函数模板，用于double类型  
    swap(p, q);  
    std::cout << "After swap: p = " << p << ", q = " << q << std::endl;  
  
    return 0;  
}
```

### 4.3.2 类模板

模板类（也称为类模板）是一种特殊的类，它可以被参数化以工作在多种不同的数据类型上。

定义模型

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
  
// 声明模板类  
template <typename T>  
class Array {  
private:  
    T* data;  
    int size;  
  
public:  
    // 构造函数  
    Array(int size) {  
        this->size = size;  
        data = new T[size];  
    }  
  
    // 析构函数  
    ~Array() {  
        delete[] data;  
    }  
  
    // 设置元素  
    void set(int index, T value) {  
        if (index >= 0 && index < size) {  
            data[index] = value;  
        }  
    }  
  
    // 获取元素  
    T get(int index) {  
        if (index >= 0 && index < size) {  
            return data[index];  
        }  
        // 抛出异常或返回一个默认值可能是更好的做法  
        return T();  
    }  
  
    // 获取数组大小  
    int getSize() const {  
        return size;  
    }  
};  
  
int main() {  
    // 实例化模板类用于int类型  
    Array<int> intArray(5);  
    intArray.set(0, 10);  
    std::cout << "intArray[0] = " << intArray.get(0) << std::endl;  
  
    // 实例化模板类用于double类型  
    Array<double> doubleArray(3);  
    doubleArray.set(0, 3.14);  
    std::cout << "doubleArray[0] = " << doubleArray.get(0) << std::endl;  
  
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
6. **资源清理**：使用C++的RAII（Resource Acquisition Is Initialization）惯用法来确保在异常发生时资源得到正确清理。

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

自定义异常类： 可以通过从`std::exception`（或其任何派生类）继承来创建自定义异常类。

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
  
    // ... 更多程序代码（如果abort没有被调用，这些代码将会执行） ...  
  
    return 0;  
}
```

### 5.3.2 errno

`errno`是一个全局变量，用于表示某些系统调用和库函数执行时发生的错误。

`errno`的定义通常包含在`<errno.h>`（C语言风格）或`<cerrno>`（C++风格）头文件中。

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

本节内容来自 [第5篇:C/C++ 内存布局与程序栈 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/184957568)





## 6.2 内存分配



### 6.2.1 new,delete



### 6.2.2 new[],delete[]



### 6.2.3 malloc,free


















# 易混淆问题

## 简单问题

### .1 char数组的strlen和sizeof的区别

|        | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| strlen | 求第一个空字符之前的字符数目, **不包含终止空字符**           |
| sizeof | 求数组大小, 以字节为单位, 和数组元素个数无关.  用于指针时返回指针大小. |

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





