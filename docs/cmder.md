---
typora-root-url: img
---

# cmder 使用介绍

[<img src="https://img.shields.io/badge/github-Welcome-yellow">](https://github.com/rea-leaf/IT-Developer/tree/master/docs) [<img src="https://img.shields.io/badge/%E7%A4%BA%E4%BE%8B-%E6%AC%A2%E8%BF%8E%E8%AE%BF%E9%97%AE-important">](https://github.com/rea-leaf/IT-Developer/tree/master/docs)

[github](https://github.com/rea-leaf/IT-Developer/tree/master/docs)

![](/main.png)

# 1、简介

cmder 是一个软件包，cmder是一个增强型命令行工具，不仅可以使用windows下的所有命令，还可以使用linux的命令

# 2、下载

官网：https://cmder.net/

![](/cmder.png)

下载的时候，会有两个版本，分别是mini与full版；唯一的差别在于有没有内建msysgit工具，这是Git for Windows的标准配备；全安装版 cmder 自带了 msysgit, 压缩包 23M, 除了 git 本身这个命令之外, 里面可以使用大量的 linux 命令；比如 grep, curl(没有 wget)； 像vim, grep, tar, unzip, ssh, ls, bash, perl 

# 3、安装

直接将cmder.zip解压

![image-20200411165648221](/image-20200411165648221.png)

## 配置环境变量

添加系统环境变量：CMDER_HOME

![image-20200411170223540](/image-20200411170223540.png)

添加path: ***%CMDER_HOME%\***

![image-20200411170410775](/image-20200411170410775.png)

## 添加 cmder 到右键菜单

配置环境变量后，在**管理员权限**的终端输入以下语句。
Win8或者Win10可以直接 win+x 再按 a 键进入。

```
Cmder.exe /REGISTER ALL
```

![image-20200411170516085](/image-20200411170516085.png)

# 4、使用



## 新标签打开个管理员权限终端

快捷键 Ctrl + t 后勾选

![img](/763945-20180404153613615-2060677905.png)

![img](https://images2018.cnblogs.com/blog/763945/201804/763945-20180404153625094-1840631790.png)

 

## 设置

快捷键：win + alt + p
或者在右下角图标，右击

![img](/763945-20180404153635483-1809536389.png)

 

## **设置bash作为默认开启的选项**

![img](/763945-20180404153648116-1451607138.png)

 

## 解决中文乱码问题

之前在网找了好多方法，可是都解决不了，很多人在在Environment里添加set LANG=zh_CN.UTF-8来解决中文乱码的问题，可是我用这个方法并没有成功，可能是环境的原因吧，我的系统是win10的。
最后找到解决办法：
Settings->Startup->Environment 添加
set LANG=zh_CN.UTF-8
set LC_ALL=zh_CN.utf8

![img](/763945-20180404153700272-1516801389.png)

 

重启Cmder，发现使用ls，中文正确显示了。

![img](/763945-20180404153753549-62760106.png)

 

## 更改背景

![img](/763945-20180404153813574-2036831489.png)

 

## 更换主题

内置了几款不错的主题，当然如果你觉得不合适，当然也支持自己设定。

![img](/763945-20180404153852546-1032635388.png)

 

# 5、常用功能介绍

![img](/763945-20180404153903760-263210617.png)

 

### 使用前需要解决的几个问题

- ls命令不支持中文

  > `win+alt+p`打开设置面板，找到`Startup -> Envrioment`选项
  > 在下面的文本框里添加一行 `set LANG=zh_CN.UTF-8`
  > 然后重启cmder
  > 然后用ls命令查看目录下的文件，带中文的文件名都能正常显示了。

- 添加 cmder 到右键菜单

  > 首先打开具有管理员权限的终端，快捷键`Ctrl + t` 勾选`Run as current user`和 `Run as administrator`这两 项，然后点start开启，然后在命令行输入`Cmder.exe /REGISTER ALL`

现在在文件夹上右键点击`Cmder here` 就能在cmder里进入该目录

### 修改命令提示符号

cmder默认的命令提示符是 λ ，如果想改成常见的 $ ,具体操作如下：
打开cmder安装目录下的**\vendor\clink.lua**文件找到`lambda = "λ"`和`lambda = "("..env..") λ"`把λ替换成$
然后重启cmder即可，但powerShell需要另行设置
打开cmder安装目录下的**\vendor\profile.ps1**文件找到`λ  `和`λ  |`和***Microsoft.PowerShell.UtilityWrite-Host "`nλ " -NoNewLine -ForegroundColor "DarkGray"\***把λ替换成$ ,然后重启cmder即可

### 设置默认打开目录

`win+alt+p`打开设置面板，找到`Startup -> Tasks`选项,在右侧选中`{cmd::Cmder}` 把
**cmd /k "%ConEmuDir%..init.bat"** 修改成 **cmd /k "%ConEmuDir%..init.bat" -new_console:d:`E:\www`** 即可。
`E:\www`就是我们指定的默认打开目录

### 自定义aliases

cmder还增加了alias功能，它让你用短短的指令执行一些常见但指令超长又难以记忆的语法;比如 ls cls等等
打开cmder安装目录下的**\config\user-aliases.cmd**文件
下面是我自己定义的常用的

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
st="D:\Sublime Text 3\sublime_text.exe" //输入st打开Sublime Text 3编辑器
w=cd /d E:/www  //输入w跳转到E盘下的www目录
..=cd ..  //输入..返回上一级文件夹
wp=.\node_modules\.bin\webpack $* //如果webpack不是全局安装而是安装在项目下webpack命令不能直接用，
                                  //需要.\node_modules\.bin\webpack调用，每次都这样写太麻烦。
                                  //现在只要输入wp就可以用webpack命令
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

如上图示编号的部分说明如下：

1, Cmder常用快捷键

- 利用Tab，自动路径补全；
- 利用Ctrl+T建立新页签；利用Ctrl+W关闭页签;
- 利用Ctrl+Tab切换页签;
- Alt+F4：关闭所有页签
- Alt+Shift+1：开启cmd.exe
- Alt+Shift+2：开启powershell.exe
- Alt+Shift+3：开启powershell.exe (系统管理员权限)
- Ctrl+1：快速切换到第1个页签
- Ctrl+n：快速切换到第n个页签( n值无上限)
- Alt + enter： 切换到全屏状态；
- Ctr+r 历史命令搜索

2, 可在视窗内搜寻画面上出现过的任意关键字。

3, 新增页签按钮。

4, 切换页签按钮。

5, 锁定视窗，让视窗无法再输入。

6, 切换视窗是否提供卷轴功能，启动时可查询之前显示过的内容。

7, 按下滑鼠左键可开启系统选单，滑鼠右键可开启工具选项视窗。 Win+Alt+P ：开启工具选项视窗。