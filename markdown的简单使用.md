# 一、markdown基本语法
## 1、设置标题
在设置的标题前加#，用空格隔开。#是一级标题，##是二级标题，以此类推
## 2、字体的转变
加粗：用两个`**`包起来，示例：`**加粗的文字** `   
斜体：用两个`*`包起来，示例：`*倾斜的文字* `   
斜体加粗：用两个`***`包起来，示例：`***斜体加粗***`   
删除线：`~~加删除线的文字~~`
## 字体颜色的转变
<font color="red">改变字体颜色的文字</font>
## 3、换行
文字后插入超过一个空格,并回车
## 4、代码引用
### 单行代码
示例：` `被引用的文字` `
### 代码块
示例：` ```   
被引用的代码块   
    ``` `
## 5、分割线
使用三个或三个以上的`*`或`-`加以分割
## 6、插入图片
`![图片alt]（图片地址"图片tittle")`    图片alt就是显示在图片下方的文字，tittle可以不加
## 7、超链接
`[超链接名](超链接地址"超链接tittle")`   tittle可以不加
## 8、列表
### 无序列表
在文字前加`+-*`任何一个，用空格隔开
### 有序列表
在列表文字前面`数字.`
### 列表嵌套
在上一级和下一级之间插入三个空格
## 9、插入表格
```
|表头|表头|表头|   
|:---|:--|:---|   
内容|内容|内容|    
内容|内容|内容|   
```
第二行分割表头和内容。   
文字默认居左  
-两边加：表示文字居中 
-右边加：表示文字居右   
在表格与文字前插入空格
# 二、VS code的markdown的简单使用
## 1、Markdown Yellow主题
Code安装插件的快捷键和Sublime、Atom的都一样，是⌘+⌂+P，也可以用F1，调出快速安装命令栏之后，输入Install Extension回车，然后输入过滤字符Markdown Theme快速定位到这个插件，选择最右边的那个下载按钮安装重启即可。
![](https://github.com/SCSE-StudyGroup2018/lihang1/blob/master/图片示例.png)
## 2、配置中文字体
在Code中按⌘+,快捷键，调出配置文件，修改如下：
```
{ 
//-------- Editor configuration -------- 
// Controls the font family.  
"editor.fontFamily": "PingFang SC",
"editor.fontSize": 16,
}
```
我比较喜欢苹方字体，所以将编辑器默认字体改成了PingFang SC，如果你的Mac系统没有更新到最新版本，可以在网上下载这个字体文件，对于Windows用户来说，可以设置成YaHei-Consolas-Hybrid，这是雅黑和Consolas的合并字体，中西文都有很好的显示效果。
![](http://upload-images.jianshu.io/upload_images/1749344-e43f2f20b082c30c.png)
## 3、配置预览风格
1、先打开配置文件，在里面增加一行：
```
"markdown.styles": [ 
"file:///Users/you-name/Documents/vscode-markdown.css"
 ],
 ```
 这表示markdown预览的风格将用我自定义的vscode-markdown.css文件，记得这里需要填写file://协议。      
 2、创建一个css文件
 ```
@charset "utf-8"; 
/** * vscode-markdown.css */
h1, h2, h3, h4, h5, h6, p, blockquote { margin: 0; padding: 0;} 
body { font-family: "PingFang SC", "Hiragino Sans GB", Helvetica, Arial, sans-serif; padding: 1em; margin: auto; max-width: 42em; color: #737373; background-color: white; margin: 10px 13px 10px 13px;}
table { margin: 10px 0 15px 0; border-collapse: collapse;}
td, th { border: 1px solid #ddd; padding: 3px 10px;} 
th { padding: 5px 10px; }
a { color: #0069d6; } 
a:hover { color: #0050a3; text-decoration: none;} 
a img { border: none; } 
p { margin-bottom: 9px; }
h1, h2, h3, h4, h5, h6 { color: #404040; line-height: 36px;} 
h1 { margin-bottom: 18px; font-size: 30px; }
h2 { font-size: 24px; }
h3 { font-size: 18px; } 
h4 { font-size: 16px; }
h5 { font-size: 14px; } 
h6 { font-size: 13px; } 
hr { margin: 0 0 19px; border: 0; border-bottom: 1px solid #ccc;} 
blockquote{ color:#666666; margin:0; padding-left: 3em; border-left: 0.5em #EEE solid; font-family: "STKaiti", georgia, serif;}
code, pre { font-family: Monaco, Andale Mono, Courier New, monospace; font-size: 12px;} 
code { background-color: #ffffe0; border: 1px solid orange; color: rgba(0, 0, 0, 0.75); padding: 1px 3px; -webkit-border-radius: 3px; -moz-border-radius: 3px; border-radius: 3px;}
pre { display: block; background-color: #f8f8f8; border: 1px solid #2f6fab; border-radius: 3px; overflow: auto; padding: 14px; white-space: pre-wrap; word-wrap: break-word;}
pre code { background-color: inherit; border: none; padding: 0;} 
sup { font-size: 0.83em; vertical-align: super; line-height: 0;} 
* { -webkit-print-color-adjust: exact;}
@media screen and (min-width: 914px) 
{ body { width: 854px; margin: 10px auto; }
} 
@media print 
{ body, code, pre code, h1, h2, h3, h4, h5, h6 { color: black; } 
table, pre { page-break-inside: avoid; } 
}
```
将
`font-family: "PingFang SC", "Hiragino Sans GB", Helvetica, Arial, sans-serif;`
中的PingFang SC和Hiragino Sans GB替换成你自己系统中安装的合适字体名称即可   
[Visual Studio Code 0.10.11](https://pan.baidu.com/s/1eRacbh4)      
[苹方字体](https://pan.baidu.com/s/1gdO4JIV)   
[Markdown的CSS配置文件](https://pan.baidu.com/s/1botKLbT)   

