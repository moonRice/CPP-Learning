# C / C++



## 1.1 CPP Learning Note

### 1.1.1 基础入门

#### 1.1.1.1 你好，世界！

```c++
#include <iostream>
using namespace std;

void main() {
	system("pause");
	cout << "Hello World" << endl;
}
```

#### 1.1.1.2 注释

```c++
/*
	多行注释
*/
#include <iostream>
using namespace std;

// 单行注释
void main() {
	system("pause");
	cout << "Hello World" << endl;
}
```

#### 1.1.1.3 变量

```c++
#include <iostream>
using namespace std;

void main() {
    // 定义变量
	int a = 0;
    cout << "a = " << a << endl;
}
```

#### 1.1.1.4 常量

两种方法（**值不可被修改**）：

`#define 常量名 常量值`

`const 数据类型 常量名 常量值`

```c++
#include <iostream>
using namespace std;
// 定义常量
#define MAX_LENGTH 1000

void main() {
	system("pause");
	cout << "Hello World" << endl;
}
```

#### 1.1.1.5 关键字

**作用：**关键字是C++中预先保留的单词（标识符）

- **在定义变量或者常量时候，不要用关键字**

C++关键字如下：

| asm        | do           | if               | return      | typedef  |
| ---------- | ------------ | ---------------- | ----------- | -------- |
| auto       | double       | inline           | short       | typeid   |
| bool       | dynamic_cast | int              | signed      | typename |
| break      | else         | long             | sizeof      | union    |
| case       | enum         | mutable          | static      | unsigned |
| catch      | explicit     | namespace        | static_cast | using    |
| char       | export       | new              | struct      | virtual  |
| class      | extern       | operator         | switch      | void     |
| const      | false        | private          | template    | volatile |
| const_cast | float        | protected        | this        | wchar_t  |
| continue   | for          | public           | throw       | while    |
| default    | friend       | register         | true        |          |
| delete     | goto         | reinterpret_cast | try         |          |

```
提示：在给变量或者常量起名称时候，不要用C++得关键字，否则会产生歧义。
```

#### 1.1.1.6 标识符命名规则

**作用**：C++规定给标识符（变量、常量）命名时，有一套自己的规则

- 标识符不能是关键字
- 标识符只能由字母、数字、下划线组成
- 第一个字符必须为字母或下划线
- 标识符中字母区分大小写

> 建议：给标识符命名时，争取做到见名知意的效果，方便自己和他人的阅读

### 1.1.2 数据类型

#### 1.1.2.1 基本内置类型

C++ 为程序员提供了种类丰富的内置数据类型和用户自定义的数据类型。下表列出了七种基本的 C++ 数据类型：

|   类型   | 关键字  |
| :------: | :-----: |
|  布尔型  |  bool   |
|  字符型  |  char   |
|   整型   |   int   |
|  浮点型  |  float  |
| 双浮点型 | double  |
|  无类型  |  void   |
| 宽字符型 | wchar_t |

其实 wchar_t 是这样来的：

```c++
typedef short int wchar_t;
```

所以 wchar_t 实际上的空间是和 short int 一样。

一些基本类型可以使用一个或多个类型修饰符进行修饰：

- signed
- unsigned
- short
- long

下表显示了各种变量类型在内存中存储值时需要占用的内存，以及该类型的变量所能存储的最大值和最小值。

**注意：**不同系统会有所差异，一字节为 8 位。

**注意：**long int 8 个字节，int 都是 4 个字节，早期的 C 编译器定义了 long int 占用 4 个字节，int 占用 2 个字节，新版的 C/C++ 标准兼容了早期的这一设定。

| 类型               | 位            | 范围                                                         |
| :----------------- | :------------ | :----------------------------------------------------------- |
| char               | 1 个字节      | -128 到 127 或者 0 到 255                                    |
| unsigned char      | 1 个字节      | 0 到 255                                                     |
| signed char        | 1 个字节      | -128 到 127                                                  |
| int                | 4 个字节      | -2147483648 到 2147483647                                    |
| unsigned int       | 4 个字节      | 0 到 4294967295                                              |
| signed int         | 4 个字节      | -2147483648 到 2147483647                                    |
| short int          | 2 个字节      | -32768 到 32767                                              |
| unsigned short int | 2 个字节      | 0 到 65,535                                                  |
| signed short int   | 2 个字节      | -32768 到 32767                                              |
| long int           | 8 个字节      | -9,223,372,036,854,775,808 到 9,223,372,036,854,775,807      |
| signed long int    | 8 个字节      | -9,223,372,036,854,775,808 到 9,223,372,036,854,775,807      |
| unsigned long int  | 8 个字节      | 0 到 18,446,744,073,709,551,615                              |
| float              | 4 个字节      | 精度型占4个字节（32位）内存空间，+/- 3.4e +/- 38 (~7 个数字) |
| double             | 8 个字节      | 双精度型占8 个字节（64位）内存空间，+/- 1.7e +/- 308 (~15 个数字) |
| long double        | 16 个字节     | 长双精度型 16 个字节（128位）内存空间，可提供18-19位有效数字。 |
| wchar_t            | 2 或 4 个字节 | 1 个宽字符                                                   |

从上表可得知，变量的大小会根据编译器和所使用的电脑而有所不同。

下面实例会输出您电脑上各种数据类型的大小。

##### 1、实例

```c++
#include<iostream>  
#include <limits>
 
using namespace std;  
  
int main()  
{  
    cout << "type: \t\t" << "************size**************"<< endl;  
    cout << "bool: \t\t" << "所占字节数：" << sizeof(bool);  
    cout << "\t最大值：" << (numeric_limits<bool>::max)();  
    cout << "\t\t最小值：" << (numeric_limits<bool>::min)() << endl;  
    cout << "char: \t\t" << "所占字节数：" << sizeof(char);  
    cout << "\t最大值：" << (numeric_limits<char>::max)();  
    cout << "\t\t最小值：" << (numeric_limits<char>::min)() << endl;  
    cout << "signed char: \t" << "所占字节数：" << sizeof(signed char);  
    cout << "\t最大值：" << (numeric_limits<signed char>::max)();  
    cout << "\t\t最小值：" << (numeric_limits<signed char>::min)() << endl;  
    cout << "unsigned char: \t" << "所占字节数：" << sizeof(unsigned char);  
    cout << "\t最大值：" << (numeric_limits<unsigned char>::max)();  
    cout << "\t\t最小值：" << (numeric_limits<unsigned char>::min)() << endl;  
    cout << "wchar_t: \t" << "所占字节数：" << sizeof(wchar_t);  
    cout << "\t最大值：" << (numeric_limits<wchar_t>::max)();  
    cout << "\t\t最小值：" << (numeric_limits<wchar_t>::min)() << endl;  
    cout << "short: \t\t" << "所占字节数：" << sizeof(short);  
    cout << "\t最大值：" << (numeric_limits<short>::max)();  
    cout << "\t\t最小值：" << (numeric_limits<short>::min)() << endl;  
    cout << "int: \t\t" << "所占字节数：" << sizeof(int);  
    cout << "\t最大值：" << (numeric_limits<int>::max)();  
    cout << "\t最小值：" << (numeric_limits<int>::min)() << endl;  
    cout << "unsigned: \t" << "所占字节数：" << sizeof(unsigned);  
    cout << "\t最大值：" << (numeric_limits<unsigned>::max)();  
    cout << "\t最小值：" << (numeric_limits<unsigned>::min)() << endl;  
    cout << "long: \t\t" << "所占字节数：" << sizeof(long);  
    cout << "\t最大值：" << (numeric_limits<long>::max)();  
    cout << "\t最小值：" << (numeric_limits<long>::min)() << endl;  
    cout << "unsigned long: \t" << "所占字节数：" << sizeof(unsigned long);  
    cout << "\t最大值：" << (numeric_limits<unsigned long>::max)();  
    cout << "\t最小值：" << (numeric_limits<unsigned long>::min)() << endl;  
    cout << "double: \t" << "所占字节数：" << sizeof(double);  
    cout << "\t最大值：" << (numeric_limits<double>::max)();  
    cout << "\t最小值：" << (numeric_limits<double>::min)() << endl;  
    cout << "long double: \t" << "所占字节数：" << sizeof(long double);  
    cout << "\t最大值：" << (numeric_limits<long double>::max)();  
    cout << "\t最小值：" << (numeric_limits<long double>::min)() << endl;  
    cout << "float: \t\t" << "所占字节数：" << sizeof(float);  
    cout << "\t最大值：" << (numeric_limits<float>::max)();  
    cout << "\t最小值：" << (numeric_limits<float>::min)() << endl;  
    cout << "size_t: \t" << "所占字节数：" << sizeof(size_t);  
    cout << "\t最大值：" << (numeric_limits<size_t>::max)();  
    cout << "\t最小值：" << (numeric_limits<size_t>::min)() << endl;  
    cout << "string: \t" << "所占字节数：" << sizeof(string) << endl;  
    // << "\t最大值：" << (numeric_limits<string>::max)() << "\t最小值：" << (numeric_limits<string>::min)() << endl;  
    cout << "type: \t\t" << "************size**************"<< endl;  
    return 0;  
}
```

本实例使用了 **endl**，这将在每一行后插入一个换行符，**<<** 运算符用于向屏幕传多个值，**sizeof()** 函数用来获取各种数据类型的大小。

当上面的代码被编译和执行时，它会产生以下的结果，结果会根据所使用的计算机而有所不同：

```c++
type:         ************size**************
bool:         所占字节数：1    最大值：1        最小值：0
char:         所占字节数：1    最大值：        最小值：?
signed char:     所占字节数：1    最大值：        最小值：?
unsigned char:     所占字节数：1    最大值：?        最小值：
wchar_t:     所占字节数：4    最大值：2147483647        最小值：-2147483648
short:         所占字节数：2    最大值：32767        最小值：-32768
int:         所占字节数：4    最大值：2147483647    最小值：-2147483648
unsigned:     所占字节数：4    最大值：4294967295    最小值：0
long:         所占字节数：8    最大值：9223372036854775807    最小值：-9223372036854775808
unsigned long:     所占字节数：8    最大值：18446744073709551615    最小值：0
double:     所占字节数：8    最大值：1.79769e+308    最小值：2.22507e-308
long double:     所占字节数：16    最大值：1.18973e+4932    最小值：3.3621e-4932
float:         所占字节数：4    最大值：3.40282e+38    最小值：1.17549e-38
size_t:     所占字节数：8    最大值：18446744073709551615    最小值：0
string:     所占字节数：24
type:         ************size**************
```

##### 2、typedef 声明

您可以使用 **typedef** 为一个已有的类型取一个新的名字。下面是使用 typedef 定义一个新类型的语法：

```
typedef type newname; 
```

例如，下面的语句会告诉编译器，feet 是 int 的另一个名称：

```
typedef int feet;
```

现在，下面的声明是完全合法的，它创建了一个整型变量 distance：

```
feet distance;
```

##### 3、枚举类型

枚举类型(enumeration)是C++中的一种派生数据类型，它是由用户定义的若干枚举常量的集合。

如果一个变量只有几种可能的值，可以定义为枚举(enumeration)类型。所谓"枚举"是指将变量的值一一列举出来，变量的值只能在列举出来的值的范围内。

创建枚举，需要使用关键字 **enum**。枚举类型的一般形式为：

```
enum 枚举名{ 
     标识符[=整型常数], 
     标识符[=整型常数], 
... 
    标识符[=整型常数]
} 枚举变量;
    
```

如果枚举没有初始化, 即省掉"=整型常数"时, 则从第一个标识符开始。

例如，下面的代码定义了一个颜色枚举，变量 c 的类型为 color。最后，c 被赋值为 "blue"。

```
enum color { red, green, blue } c;
c = blue;
```

默认情况下，第一个名称的值为 0，第二个名称的值为 1，第三个名称的值为 2，以此类推。但是，您也可以给名称赋予一个特殊的值，只需要添加一个初始值即可。例如，在下面的枚举中，**green** 的值为 5。

```
enum color { red, green=5, blue };
```

在这里，**blue** 的值为 6，因为默认情况下，每个名称都会比它前面一个名称大 1，但 red 的值依然为 0。

#### 1.1.2.2 整型

**作用**：整型变量表示的是整数类型的数据

C++中能够表示整型的类型有以下几种方式，**区别在于所占内存空间不同**：

|    **数据类型**     |                  **占用空间**                   |     取值范围     |
| :-----------------: | :---------------------------------------------: | :--------------: |
|    short(短整型)    |                      2字节                      | (-2^15 ~ 2^15-1) |
|      int(整型)      |                      4字节                      | (-2^31 ~ 2^31-1) |
|    long(长整形)     | Windows为4字节，Linux为4字节(32位)，8字节(64位) | (-2^31 ~ 2^31-1) |
| long long(长长整形) |                      8字节                      | (-2^63 ~ 2^63-1) |

#### 1.1.2.3 sizeof

**作用：**利用sizeof关键字可以统计数据类型所占内存大小

**语法：** `sizeof( 数据类型 / 变量)`

**示例：**

```C++
int main() {

	cout << "short 类型所占内存空间为： " << sizeof(short) << endl;

	cout << "int 类型所占内存空间为： " << sizeof(int) << endl;

	cout << "long 类型所占内存空间为： " << sizeof(long) << endl;

	cout << "long long 类型所占内存空间为： " << sizeof(long long) << endl;

	system("pause");

	return 0;
}
1234567891011121314
```

> **整型结论**：short < int <= long <= long long

#### 1.1.2.4 浮点型

**作用**：用于表示小数

浮点型变量分为两种：

1. 单精度float
2. 双精度double

两者的**区别**在于表示的有效数字范围不同。

| **数据类型** | **占用空间** | **有效数字范围** |
| ------------ | ------------ | ---------------- |
| float        | 4字节        | 7位有效数字      |
| double       | 8字节        | 15～16位有效数字 |

**示例：**

```C++
int main() {
    
    // 因为系统会自动转换3.14为双精度，所以末尾要加f
	float f1 = 3.14f;
	double d1 = 3.14;

	cout << f1 << endl;
	cout << d1<< endl;

	cout << "float  sizeof = " << sizeof(f1) << endl;
	cout << "double sizeof = " << sizeof(d1) << endl;

	//科学计数法
	float f2 = 3e2; // 3 * 10 ^ 2 
	cout << "f2 = " << f2 << endl;

	float f3 = 3e-2;  // 3 * 0.1 ^ 2
	cout << "f3 = " << f3 << endl;

	system("pause");

	return 0;
}
```

#### 1.1.2.5 字符型

**作用：**字符型变量用于显示单个字符

**语法：**`char ch = 'a';`

> 注意1：在显示字符型变量时，用单引号将字符括起来，不要用双引号

> 注意2：单引号内只能有一个字符，不可以是字符串

- C和C++中字符型变量只占用1个字节。
- 字符型变量并不是把字符本身放到内存中存储，而是将对应的ASCII编码放入到存储单元

示例：

```C++
int main() {
	
	char ch = 'a';
	cout << ch << endl;
	cout << sizeof(char) << endl;

	//ch = "abcde"; //错误，不可以用双引号
	//ch = 'abcde'; //错误，单引号内只能引用一个字符

	cout << (int)ch << endl;  //查看字符a对应的ASCII码
	ch = 97; //可以直接用ASCII给字符型变量赋值
	cout << ch << endl;

	system("pause");

	return 0;
}
1234567891011121314151617
```

ASCII码表格：

| **ASCII**值 | **控制字符** | **ASCII**值 | **字符** | **ASCII**值 | **字符** | **ASCII**值 | **字符** |
| :---------: | :----------: | :---------: | :------: | :---------: | :------: | :---------: | :------: |
|      0      |     NUT      |     32      | (space)  |     64      |    @     |     96      |    、    |
|      1      |     SOH      |     33      |    !     |     65      |    A     |     97      |    a     |
|      2      |     STX      |     34      |    "     |     66      |    B     |     98      |    b     |
|      3      |     ETX      |     35      |    #     |     67      |    C     |     99      |    c     |
|      4      |     EOT      |     36      |    $     |     68      |    D     |     100     |    d     |
|      5      |     ENQ      |     37      |    %     |     69      |    E     |     101     |    e     |
|      6      |     ACK      |     38      |    &     |     70      |    F     |     102     |    f     |
|      7      |     BEL      |     39      |    ,     |     71      |    G     |     103     |    g     |
|      8      |      BS      |     40      |    (     |     72      |    H     |     104     |    h     |
|      9      |      HT      |     41      |    )     |     73      |    I     |     105     |    i     |
|     10      |      LF      |     42      |    *     |     74      |    J     |     106     |    j     |
|     11      |      VT      |     43      |    +     |     75      |    K     |     107     |    k     |
|     12      |      FF      |     44      |    ,     |     76      |    L     |     108     |    l     |
|     13      |      CR      |     45      |    -     |     77      |    M     |     109     |    m     |
|     14      |      SO      |     46      |    .     |     78      |    N     |     110     |    n     |
|     15      |      SI      |     47      |    /     |     79      |    O     |     111     |    o     |
|     16      |     DLE      |     48      |    0     |     80      |    P     |     112     |    p     |
|     17      |     DCI      |     49      |    1     |     81      |    Q     |     113     |    q     |
|     18      |     DC2      |     50      |    2     |     82      |    R     |     114     |    r     |
|     19      |     DC3      |     51      |    3     |     83      |    S     |     115     |    s     |
|     20      |     DC4      |     52      |    4     |     84      |    T     |     116     |    t     |
|     21      |     NAK      |     53      |    5     |     85      |    U     |     117     |    u     |
|     22      |     SYN      |     54      |    6     |     86      |    V     |     118     |    v     |
|     23      |      TB      |     55      |    7     |     87      |    W     |     119     |    w     |
|     24      |     CAN      |     56      |    8     |     88      |    X     |     120     |    x     |
|     25      |      EM      |     57      |    9     |     89      |    Y     |     121     |    y     |
|     26      |     SUB      |     58      |    :     |     90      |    Z     |     122     |    z     |
|     27      |     ESC      |     59      |    ;     |     91      |    [     |     123     |    {     |
|     28      |      FS      |     60      |    <     |     92      |    /     |     124     |    \|    |
|     29      |      GS      |     61      |    =     |     93      |    ]     |     125     |    }     |
|     30      |      RS      |     62      |    >     |     94      |    ^     |     126     |    `     |
|     31      |      US      |     63      |    ?     |     95      |    _     |     127     |   DEL    |

ASCII 码大致由以下**两部分组**成：

- ASCII 非打印控制字符： ASCII 表上的数字 **0-31** 分配给了控制字符，用于控制像打印机等一些外围设备。
- ASCII 打印字符：数字 **32-126** 分配给了能在键盘上找到的字符，当查看或打印文档时就会出现。

#### 1.1.2.6 转义字符

**作用：**用于表示一些不能显示出来的ASCII字符

现阶段我们常用的转义字符有：`\n \\ \t`

| **转义字符** |                **含义**                 | **ASCII**码值（十进制） |
| :----------: | :-------------------------------------: | :---------------------: |
|      \a      |                  警报                   |           007           |
|      \b      |     退格(BS) ，将当前位置移到前一列     |           008           |
|      \f      |    换页(FF)，将当前位置移到下页开头     |           012           |
|    **\n**    | **换行(LF) ，将当前位置移到下一行开头** |         **010**         |
|      \r      |    回车(CR) ，将当前位置移到本行开头    |           013           |
|    **\t**    | **水平制表(HT) （跳到下一个TAB位置）**  |         **009**         |
|      \v      |              垂直制表(VT)               |           011           |
|    **\\**    |        **代表一个反斜线字符""**         |         **092**         |
|      ’       |       代表一个单引号（撇号）字符        |           039           |
|      "       |           代表一个双引号字符            |           034           |
|      ?       |              代表一个问号               |           063           |
|      \0      |                  数字0                  |           000           |
|     \ddd     |         8进制转义字符，d范围0~7         |        3位8进制         |
|     \xhh     |    16进制转义字符，h范围09，af，A~F     |        3位16进制        |

示例：

```C++
int main() {
	
	
	cout << "\\" << endl;
	cout << "\tHello" << endl;
	cout << "\n" << endl;

	system("pause");

	return 0;
}
```

#### 1.1.2.7 字符串型

**作用**：用于表示一串字符

**两种风格**

1. **C风格字符串**： `char 变量名[] = "字符串值"`

   示例：

   ```C++
   int main() {
   
   	char str1[] = "hello world";
   	cout << str1 << endl;
       
   	system("pause");
   
   	return 0;
   }
   123456789
   ```

> 注意：C风格的字符串要用双引号括起来

1. **C++风格字符串**： `string 变量名 = "字符串值"`

   示例：

   ```C++
   int main() {
   
   	string str = "hello world";
   	cout << str << endl;
   	
   	system("pause");
   
   	return 0;
   }
   123456789
   ```

   

> 注意：C++风格字符串，需要加入头文件==#include<string>==

#### 1.1.2.8 布尔类型 bool

**作用：**布尔数据类型代表真或假的值

bool类型只有两个值：

- true — 真（本质是1）
- false — 假（本质是0）

**bool类型占1个字节大小**

示例：

```C++
int main() {

	bool flag = true;
	cout << flag << endl; // 1

	flag = false;
	cout << flag << endl; // 0

	cout << "size of bool = " << sizeof(bool) << endl; //1
	
	system("pause");

	return 0;
}
1234567891011121314
```

2.8 数据的输入

**作用：用于从键盘获取数据**

**关键字：**cin

**语法：** `cin >> 变量`

示例：

```C++
int main(){

	//整型输入
	int a = 0;
	cout << "请输入整型变量：" << endl;
	cin >> a;
	cout << a << endl;

	//浮点型输入
	double d = 0;
	cout << "请输入浮点型变量：" << endl;
	cin >> d;
	cout << d << endl;

	//字符型输入
	char ch = 0;
	cout << "请输入字符型变量：" << endl;
	cin >> ch;
	cout << ch << endl;

	//字符串型输入
	string str;
	cout << "请输入字符串型变量：" << endl;
	cin >> str;
	cout << str << endl;

	//布尔类型输入
	bool flag = true;
	cout << "请输入布尔型变量：" << endl;
	cin >> flag;
	cout << flag << endl;
	system("pause");
	return EXIT_SUCCESS;
}
```