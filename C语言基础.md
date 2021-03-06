# 一、C语言的基本语法单位
## 1、标识符
标识符是对程序所使用的常量、变量、函数、语句标号和类型定义等命名的字符串。    
标识符只能由字母、下划线和数字组成，且第一个字符必须是字母或下划线。    
示例：a，str2，student，_class5，ADD
## 2、关键字
关键字是指C语言中被特定保留的、已经具有特定意义的标识符，关键字不能被作为普通的标识符使用。

|种类|关键字|
|:--|:--|
|数据类型关键字|char，double,enum,float,int,long,short,signed,struct,union,unsigned,void|
|控制语句关键字|for,do,while,break,continue,if,else,goto,switch,case,default,return|
|存储类型关键字|auto,extern,register,static|
|其他关键字|const,sizeof,typedef,volatile|
## 3、数据类型
### 1、整型
整型可分为short（短整型），int（普通整型），long（长整型）   
根据有无符号又可分为unsigned（无符号），signed（有符号）其中signed通常被省略
### 2、浮点型
浮点型可分为float（单精度型），double（双精度型），long double（长双精度型）
### 3、字符型
字符型可分为char（有符号），unsigned（无符号）
## 4、常量与变量
### 1、常量指在程序运行中其值不会改变的量。   
数字常量：1，2   
字符常量：'a','M'  
定义符号常量：`#define pi=3.14`(宏定义)，`const int float pi=3.14`(在函数内定义)
### 2、变量是指在程序运行中其值可以改变的量   
C语言规定：任意一个变量使用前必须先定义，即说明变量的名称和数据类型
#### 定义变量
示例：`int a,b,c;`定义三个整型变量a，b，c     
`float x,y;`定义三个浮点型变量下，y   
注意：在同一个函数内，一个变量名称不能重复定义
##### 变量的初始化
示例：`int a=2,b=3,c=2;`对定义的整型变量a、，b，c初始化
## 4、数组
### 一维数组的定义
`int score[10];`
int表示整型，score是他的地址，含有10个元素，依次为score[0]……score[9]
### 一维数组的初始化
`int score[3]={10,11,12};`
若部分赋值，则余下的默认为0.
### 二维数组
`int score[2][3]={{1,2,3},{4,5,6}};`
两行三列的二维数组。
### 字符数组
`char person[4]={'a','b','c','\0'];`
`char person[4]="abc";`
用字符串初始化数组时，没有初始化的第一个元素默认添一个`\0`.    
即这两个数组等价。
## 5、结构
```
struct student
{
int a;
float b;
……
};
```
定义了一个student类型的变量，其中含有a，b等变量；
`struct student x;`
定义了一个叫x的student类型变量
### 结构成员的访问
如上访问`x.a`即访问的是x的a成员。
## 6、指针
指针是一个普通变量的地址
### 指针的定义
`int *p`表示定义一个整型指针变量，`p`是指针变量的名称  `%p`输出变量的地址值
### 指针的初始化
```
int a;
int *p=&a;
```
表示p指向的是a的首地址   
`int *p;p=NULL;`表示p是空指针
### 指针的赋值
```
int m=5,*p;
p=&m;
```
***当“=”的左操作数是`*p`时，改变的是p所指向的地址存放的数据；
当“=”的左操作数是p时，改变的是p所指向的地址***
p指向m的地址，`*p`等于5；   
指针变量 可以相互赋值    
### 地址转换
```
int a=100;
char *pa;
pa=(char*)&a;
```
将a的地址强行转换为字符型
### 指针的运算
`&与*`互为逆运算   
`&`为取地址运算`*`为取地址中的内容运算   
示例:
`int *pa;int=a;`
即`&(*pa)=pa;*(&a)=a;`
### 指针与数组
*数组名称就是数组的首地址，可以看成常量指针（不可修改的常数）*
*访问数组元素时，可用指针访问*  
`int a[10],*p;`
访问方式：`a[i],p[i],*(a+i),*(p+i）`
#### 指针与二维数组
`int a[i][j],*p;`
那么
```
a=&a[0],a+i=&a[i];
*(a+i)=a[i]=&a[i][0];
a[i]+j=&a[i][j];*(a[i]+j)=a[i][j];
```
行指针：
```
int (*P)[4];
p=a;
```
即p指向第一行；   
*列指针就是普通指针*
#### 指针数组：
`int *p[2]={'l','m'}`
`p[0]`表示l的地址；`*p[0]=l;``
### 指针与结构
```
struct x
{
int a;
char b;
};
struct x x1,*p;
p=&x1;
```
`即访问时x1.a=(*p).a=p->a`
`->`指向成员符，只用于结构指针指向结构成员
### 动态内存的分配
分配内存是要使用头文件`stdlib.h`   
```
int *p=(int*)malloc(n*sizeof(int));
int *q=(int*)calloc(n,sizeof(int));
```
表示想要分配n个整型空间   
如果`p!=NULL`,则分配成功  
最后使用完之后要进行空间的释放`free(p);free(q);`  
然后将指针变为空指针`p=NULL;q=NULL;`
## 7、联合
```
union nmae
{
int i;
int x[10];
}
union name name1;
```
union的形式与结构大致相同；不同的是，union里只分配一个空间，通常用来得到一个数的字节。
## 8、变量的生存区与作用域
全局变量的生存区和作用域在定义了变量之后，    
本地变量的生存区和作用域在定义了变量之后直到大括号，  
静态本地变量**（在类型前面加上static ）**的生存区与全局变量相同，作用 域与本地变量相同。
# 二、C语言的基本运算
#### 运算符是用来表示某种运算的特殊符号  
##### 1、基本运算符
`+` 加法运算符  `-`减法运算符  `*`乘法运算符   `/`除法运算符   `%`取模或求余运算符    `=`赋值运算符
##### 2、自增，自减运算符
`++i`对i进行自增（加一）   `--i`对i进行子自减（减一）  
注意：`++i`实现运算再赋值   `i++`是线赋值在运算
##### 3、关系运算符
`a>b`如果a大于b，则结果为真，否则为假   
`a==b`如果a等于b，则结果为真，否则为假  
`a!=b`如果a不等于b，则结果为真，否则为假  
注意：C语言中以数字0表示假，以数字1表示真
示例：
```
a=1,b=2,c=3;
d=a<b>3;
```
d的值为0.解析：a<b为真，即表达式a<b的值为1，1>c为假，值为0，所以d=0
#### 4、逻辑运算符
注意：在逻辑运算时，当且仅当其值等于0时为假，逻辑值用0表示，其余都为真，逻辑值用1表示  
`!i`逻辑非运算：若i为真，则!i为假;若i为假，则!i为真  
`a&&b`逻辑与运算：当且仅当a与b都为真时，结果为真；否则为假   
`a||b`逻辑或运算：只要a与b中至少一个为真时，结果为真；否则为假 
#### 5、位运算符
注意：在进行位运算时先将数字化为二进制
`a&b`位与运算：当且仅当相应的二进制位都为1时，该位为1；否则为0  
`a|b`位或运算：相应的二进制位只要有一位是1，该位位为1，否则为0  
`a^b`位异或运算：相应的二进制位相同，该为为0，否则为1  
`~a`位取反运算：将二进制位的1变为0，0变为1  
#### 6、移位运算符
`a<<n`：讲a的二进制位数向左移n位，左边位置被占据，右边添0（即将a扩大2^n倍）  
`a>>n`：讲a的二进制位数向右移n位，右边位置被占据，左边添0（即将a缩小2^n倍）   
#### 7、条件运算符
`表达式1?表达式2:表达式3`先计算表达式1的值，若为真，取表达式2；否则，取表达式3   
### 分隔符是用来分隔变量、数据、表达式等多个单词的符号，主要指空格、制表符和换行符
# 三、C语言程序的基本结构
## 1、预处理命令
示例：`#include<stdio.h>`   `#include<stdlib.h>`
## 宏定义
宏定义就是用名称代表后面的表达式    
`#define 名称 表达式`  
需要换行的话  
```
#define 名称 表达式1\
            表达式2
```
## 2、main函数
示例：
```
int main()
{
return 0;
}
```
`return 0`是指函数的返回值
## 3、语句
每句语句之间都要用`;`分隔
### 1、输入语句：
`scanf_s("%d",&a);`输入一个整型常量，存储在地址a（整型变量a）中   
整型：`%d`(十进制)`%x` (十六进制)`%o`(八进制) `%f`:浮点型 `%c`:字符型 `%s`:字符串型
### 2、输出语句
`printf("%d",a)`将地址a的变量以整型输出
`%f`:单精度 `%lf`:双精度 `%.2f`:按照小数点后两位输出
### 3、注释语句
`/*注释的内容*/`多行注释   `//`单行注释
### 4、if条件分支语句
```
if(表达式){语句一；语句二；……}；
else {语句一；语句二；……}；
```
如果表达式为真，则执行if后面的语句；否则执行else后面的语句。  
其中else语句不需要可以不写，if语句也可以嵌套；
### 5、switch多路开关语句
```
switch(表达式)
{
case常量1:语句1;break；
case常量2:语句2;break;
……
default:语句；
}
```
注意：switch后面的表达式可以是整型或字符型表达式，但不能是关系表达式或逻辑表达式；  
先计算switch表达式的值，将之与case后面的常量比较，若相等，则进行对应case后面的语句；否则进行default后面的语句。
### 6、for循环语句
```
for(表达式1;表达式2;表达式3)
{
循环的语句；
}
```
注意：表达式1一般是赋值表达式，为循环控制的变量变赋初值；   
表达式2一般是关系或逻辑表达式，作为控制循环结束的条件；   
表达式3一般是赋值表达式，对循环变量进行修改；   
三个表达式都可以为空语句。
依次计算表达式1、2，判断循环条件：若为真，执行一次循环，计算表达式3，继续上述操作；若为假，退出循环。
### 7、while循环语句
```
while(表达式)
{
进行循环的语句；
}
```
判断表达式：若为真，执行一次循环；否则，退出循环。
### 8、do while语句
```
do
{
循环体；
}while(表达式）；
```
先执行一次循环，然后判断表达式：若为真，继续执行一次循环；否则，退出循环。
### 9、break语句
break语句加到其他语句后可以提前终止循环
### 10、continue语句
用于循环中，忽略continue之后的语句，结束一次循环。
### 11、goto语句
```
goto 标号；
……
标号：语句：
```
直接从跳入标号后面的语句。
## 4、函数
+ 函数的结构形式：
```
int sum(int ,int b)
{
return (a+b);
}
```
int表示函数的类型；p,q指的是定义的形参指针；return表示返回值；    
*注意*：   
1、返回值的类型应该与函数的类型一样，且返回值不能是临时变量的地址。
2、函数中定义的变量和生成的空间都会被释放。
+ 函数的调用：
```
int a=1,b=2;
int x;
x=sum(a,b);
printf("%d",x);
```
*注意*：形参和实参的类型必须相同
### 指针型函数
```
int *sum()
{
}
```
指针型函数的返回值也是指针，即变量的首地址。我们可以通过指针型函数达到返回多个函数值的目的；     
同样的，我们也可以通过输出参数来达到相同的目的：
### 递归函数
即函数在自己内部中调用自己；
```
int jc(int n)
{
if(n==0)return 1;
else return(n*jc(n-1));
}
```
此函数即可以求出n的阶乘。   
*注意*：递归时一定要设置结束条件，否则就会进入死循环。
# 四、C语言的一般算法
## 随机数的生成
```
#include<time.h>
int a,x,y;
srand((unsiged int)time(NULL));
a=rand()%(y-x+1)+x;
```
此代码即生成一个x到y的一个随机数赋值给a
