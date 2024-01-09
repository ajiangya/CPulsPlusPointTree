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


# 2 语法
## 2.1 变量

### 2.1.1 声明与定义

|      | 含义                                |
| ---- | ----------------------------------- |
| 声明 | 声明类型和名字, extern声明，        |
| 定义 | 声明类型和名字, 并**分配存储空间**. |

### 2.1.2 基础类型

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

| cstdint | 说明    |          |          |          |           |
| ------- | ------- | -------- | -------- | -------- | --------- |
| 整型    | int8_t  | int16_t  | int32_t  | int64_t  | intptr_t  |
|         | uint8_t | uint16_t | uint32_t | uint64_t | uintptr_t |


| 修饰符        | 解释说明                                         |
| ------------- | ------------------------------------------------ |
| signed        | 有符号                                           |
| unsigned      | 无符号                                           |
| signed char   | 有符号字符，与char不完全对等, 与编译器的实现有关 |
| unsigned char | 无符号字符                                       |
| void          | 空类型                                           |

| 类型转换             | 解释说明                       |
| -------------------- | ------------------------------ |
| 非布尔>>bool         | 0->false, 1->true              |
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

可以在**同一块内存位置**存储**不同**的数据类型, 任意一时间**只能存储一种**.

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

#### 2.1..4.4 define

|         | 说明                                                     |
| ------- | -------------------------------------------------------- |
| #define | 预处理指令, 只替换, 不计算, 不求解, 无优先级, 无安全检查 |
| typedef | 定义别名, 有类型封装, 类型安全, 便于阅读和维护           |
| 建议    | 使用typedef                                              |

|         | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| #define | 预处理指令, 只替换, 不计算, 不求解, 无优先级, 无安全检查, 性能快, 内存开销大, 不便于调试 |
| 函数    | 类型安全, 好调试追踪, 好传参                                 |

|         | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| #define | 预处理指令, 只替换, 不计算, 不求解, 无优先级, 无安全检查, 无作用域 |
| inline  | 编译阶段处理, 类型安全, 便于调试, 有作用域,                  |
| 共同点  | 都是替换,都会导致代码膨胀                                    |
| 建议    | 使用inline函数                                               |

|         | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| #define | 预处理指令, 只替换, 不计算, 不求解, 无优先级, 无安全检查, 无作用域 |
| const   | 编译时处理, 类型安全, 便于调试, 有作用域                     |

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

## 2.2 存储类型说明符

|        | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| static | 静态局部变量, 静态全局变量, 静态全局函数,静态成员变量,静态成员函数 |
| extern | 用于全局函数/全局变量的声明                                  |

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

返回局部变量的值

- 当函数返回局部变量的值时，会发生**值的拷贝**。局部变量在函数退出时被销毁，但它们的值已经被拷贝给调用者，所以这是安全的。
- 不要返回局部变量的**引用或指针**，因为局部变量在函数返回后不再存在，这将导致悬挂引用或野指针。



返回局部静态变量或全局变量的引用

- 可以返回局部静态变量或全局变量的引用，因为这些变量在函数返回后仍然存在。



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
- 虚函数
- 构造和析构函数

使用注意事项:

- **内联不是强制的** 即使函数被声明为`inline`，编译器也有权选择不进行内联。内联仅是一种优化提示，而非强制指令。
- **不要过度依赖内联**：过度使用内联可能导致代码膨胀和其他潜在问题。应该谨慎地选择哪些函数进行内联。
- **内联函数通常定义在头文件中**：由于内联函数需要在每个调用点可见，因此它们通常定义在头文件中。

**类内定义的函数默认为内联函数**;

### 2.8.6 函数重载

函数重载: 

- 指**同一作用域内**,  具有**相同名字但参数列表不同**的函数. 
- 参数列表不同包括: 参数类型, 个数, 顺序.  
- 返回值不参与重载的区分.
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

|           | 说明                       |
| --------- | -------------------------- |
| public    | 公开，无访问限制           |
| protected | 只在类内部和派生类中可访问 |
| private   | 只在类内部和友元函数访问   |

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

特殊成员函数, **不定义时, 编译器会自动生成默认的**.

| 特殊成员函数   |
| -------------- |
| 构造函数 :     |
| 析构函数 :     |
| 拷贝构造函数 : |
| 赋值运算符 :   |
| 地址运算符 :   |
| 移动构造函数   |
| 移动赋值       |

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

