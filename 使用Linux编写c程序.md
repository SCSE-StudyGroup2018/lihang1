# 终端的打开方式
快捷键:Ctrl+Alt+T    
从工具栏中打开
# 终端中常见的命令即应用
+ `cd`:返回当前目录    
例如：`cd Desktop/program`指返回到Desktop(桌面)的program文件夹。
+ `gedit`:打开某文件或创建某文件，相当于windowns的记事本。   
例如：`gedit Isprimer.c`指打开或创建一个叫Isprimer.c的文件。
+ `gcc`:编译器，格式为：`gcc [options] [filenames]`,即根据输入的选择命令对文件进行相应处理。    
例如：
    + `gcc 文件`指生成可执行文件  
    + `gcc -g 文件名`-g的作用实在进行gdb调试时调出代码 
    + `gcc -o 文件名 文件` 修改文件的名称 
    + `-lm sqrt`函数无法编译成功，在编译指令补上-lm 
    + `-std = c99`参照c99的标准
+ `./`指当前目录，`./ 文件`指执行当前目录下文件
+ gdb调试 
1.输入file 文件，表示gdb调试的对象； 
2.输入l，显示出程序的代码； 
3.输入b n(数字) 表示设置的断点位置； 
4.输入r表示调试开始； 
5.输入s或n(字母)表示进入下一步； 
6.输入p 变量名可查看该变量的数值； 
7.输入q 退出gdb调试。
# 在终端编写c程序
    1.用ctrl+alt+T来打开终端
    2.要在某个文件夹里创建文本，首先要回到该文件夹的目录。如我在桌面(desktop)建立文本。 (在终端中输入) 
    cd Desktop //然后按下回车 
    3.创建文件夹（此步骤可跳过，但建议创建）
    mkdir 文件名
    4.建立文本 
    gedit hello world.c //然后按下回车，会跳出一个类似于windows的记事本 
    5.往里面敲代码 
    C 
    # include <stdio.h> 
    int main(void) { 
    printf("hello world!"); 
    return 0; 
    } 
    6.保存代码，关闭文本框。
    *** 按esc，再输入：wq***（一开始看不到尽管输进去，*wq为保存并关闭*，也可为*w则为保存不关闭*） 
    7.启动gcc对代码进行编译。 
    gcc helloworld.c -o execFile（此步骤会生成一个execFlie的文件，可用ls查看）
    8.如果有错误，系统会提示，按方向键找回gedit helloworld.c 的指令，按下回车，弹出文本框后根据系统提示对代码进行修改，完成后记得保存，
    关闭文本框。 
    9.运行
    `./execFlie`则会开始运行

