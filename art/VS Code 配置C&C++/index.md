 #  VS Code配置C/C++调试环境
 ## 需要准备的程序
* [Visual Studio Code]([https://code.visualstudio.com/ # alt-downloads](https://code.visualstudio.com/#alt-downloads)
) 建议选择System Installer
* [MinGW-w64]([https://sourceforge.net/projects/mingw-w64/](https://sourceforge.net/projects/mingw-w64/)
)  编译器，如果下载太慢的话，我还传了一个[蓝奏云](http://t.cn/EKEhkmM)
---
 ## 开始配置
*  #### 注册环境变量
将MinGW解压到一个合适的目录，比如我解压到C:\Program Files下，找到解压的目录
>复制解压出来的bin目录的地址![](https://upload-images.jianshu.io/upload_images/17890238-20615b29542a9e97.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
右击此电脑选择属性![](https://upload-images.jianshu.io/upload_images/17890238-50870c4b71549a9d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
点击环境变量![](https://upload-images.jianshu.io/upload_images/17890238-56341a7502a629b7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
点击Path，选择编辑![](https://upload-images.jianshu.io/upload_images/17890238-64e1ca803826a53d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
新建，将复制的目录位置粘贴到此，确定![](https://upload-images.jianshu.io/upload_images/17890238-c630a7c16ab6ffcb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在桌面上按住shift点击鼠标右键-在此处打开powershell， 输入```gcc -v```,看到如下界面说明环境变量配置成功
>![环境变量配置成功](https://upload-images.jianshu.io/upload_images/17890238-b5694536e2258ba2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

*  ### 配置VS Code
建议在配置之前新建一个目录专门用来存储C/CPP文件，因为配置设置VS Code会默认保存到配置时文件的目录下。
>![Open with Code](https://upload-images.jianshu.io/upload_images/17890238-399174175e83191d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>新建一个C文件Code就会提示安装相关插件![](https://upload-images.jianshu.io/upload_images/17890238-aba20331f6cfa7f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>安装拓展![](https://upload-images.jianshu.io/upload_images/17890238-8240fa9b3f67f258.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>我们写点代码，然后进入调试界面，左边第三个为调试界面，然后点击绿色小三角![](https://upload-images.jianshu.io/upload_images/17890238-8b2b06de497a8da8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
就会弹出环境选项，我们选择第一个![](https://upload-images.jianshu.io/upload_images/17890238-25850e4b82e5eb98.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)这里我们先选择第一个gcc.exe，这个选项会生成gcc编译的task，同时生成lauch.json，顺利的话会同时编译调试当前代码
![](https://upload-images.jianshu.io/upload_images/17890238-af68483854605acd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

为插件开发者点赞，一键生成配置省去不少步骤。然后我们来看一下生成的两个文件。
>*  task.json
可以看到已经自动添加了编译命令`gcc -g ${file} -o {fileBasenameNoExtension}.exe`,这个命令会将我们的`a.c`编译生成`a.exe`
![](https://upload-images.jianshu.io/upload_images/17890238-9bb20e311a53e5b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> * launch.json![](https://upload-images.jianshu.io/upload_images/17890238-de1bf73f1bf088ac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如果你仅仅编写C语言文件，到此 VS Code已经能够满足你的要求。编写好文件，设置断点，点击绿色小三角或者使用快捷键`F5`进行调试即可
>![](https://upload-images.jianshu.io/upload_images/17890238-fbc0596c4c077341.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

不过，我们看到控制台输出了乱码，原因在于VS Code默认编码为UTF-8，而我们用的中文系统的控制台默认编码为GBK，只需要更改VS Code保存编码

>点击右下角的UTF-8![](https://upload-images.jianshu.io/upload_images/17890238-d97f98ac2e42ca59.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)点击第二个 save with encoding![](https://upload-images.jianshu.io/upload_images/17890238-be487c131f400aa9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
接着在框内输入gbk，点击下面的选项即可![](https://upload-images.jianshu.io/upload_images/17890238-cc8d5b949b39534e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)可以看到已经可以正常输出
![](https://upload-images.jianshu.io/upload_images/17890238-996681fb2cea288a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

调试的两个快捷键与Visual Studio相同，`F10`逐过程，`F11`逐语句。
好了，至此C环境已经配置完成。如果你只需要编写C的话下面的不用看了
---
 ### C++环境配置
我们参照已经生成的C的配置文件
>打开lauch.json,点击Add Configuration，选择箭头所指的（gdb）lauch![](https://upload-images.jianshu.io/upload_images/17890238-c8a8253898084cee.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)可以看到为我们生成的新调试方式![](https://upload-images.jianshu.io/upload_images/17890238-c638e7318720a213.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

对比着之前的gcc调试方式，我们需要修改一点细节,从之前生成的复制过来修改lauch.json，主要修改这几个选项
> * program
`${fileDirname}\\${fileBasenameNoExtension}.exe`
>* miDebuggerPath
`复制之前生成的`
>* externalConsole
`false`
>* 添加preLaunchTask![](https://upload-images.jianshu.io/upload_images/17890238-d31108052ff646a9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/17890238-27985d4c15604724.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

name也可以修改下，让自己能识别是哪个命令就行。
完成后的lauch.json
```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(g++) Launch",
            "type": "cppdbg",
            "request": "launch",
            "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "miDebuggerPath": "C:\\Program Files\\mingw64\\bin\\gdb.exe",
            "preLaunchTask": "g++",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
        },
        
    
        {
            "name": "gcc",
            "type": "cppdbg",
            "request": "launch",
            "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "miDebuggerPath": "C:\\Program Files\\mingw64\\bin\\gdb.exe",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "gcc"
        }
    ]
}
```


然后我们打开task.json,按照之前生成的gcc编译命令，添加g++编译命令.只需将之前的复制更改
>* label
`g++`
>* command
`复制之前生成的，将gcc.exe改成g++.exe`

完成后的task.json
```
{
    "tasks": [
        {
            "type": "shell",
            "label": "gcc",
            "command": "C:\\Program Files\\mingw64\\bin\\gcc.exe",
            "args": [
                "-g",
                "${file}",
                "-o",
                "${fileDirname}\\${fileBasenameNoExtension}.exe"
            ],
            "options": {
                "cwd": "C:\\Program Files\\mingw64\\bin"
            }
        },
        {
            "type": "shell",
            "label": "g++",
            "command": "C:\\Program Files\\mingw64\\bin\\g++.exe",
            "args": [
                "-g",
                "${file}",
                "-o",
                "${fileDirname}\\${fileBasenameNoExtension}.exe"
            ],
            "options": {
                "cwd": "C:\\Program Files\\mingw64\\bin"
            }
        }
    ],
    "version": "2.0.0"
}
```
回到我们的调试界面，已经可以看到添加的g++调试选项,修改保存编码为GBK，调试成功
>![](https://upload-images.jianshu.io/upload_images/17890238-07b915f5b41dd0af.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

至此，你的 VS Code 已经可以编译调试C/C++了 ，当然是在我们创建的目录下的c/cpp文件。
***
 ## 注意（同时安装了Visual Studio）
如果你的电脑同时安装了VS的话，会出现头文件的提示错误，并且有些函数无法自动补全。原因在于**VS Code会默认使用msvc编译和VS的头文件目录**，如果你没有安装VS的话，VS Code当然不会找到msvc及VS头文件相关配置目录，就会默认使用gcc
>![默认使用msvc编译](https://upload-images.jianshu.io/upload_images/17890238-63d9c2d43b976344.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>![默认使用VS 的头文件](https://upload-images.jianshu.io/upload_images/17890238-5f5483c856c7e66b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
>![头文件错误，并且不会检查代码错误](https://upload-images.jianshu.io/upload_images/17890238-7f823652fe06e67f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 ### 解决办法
将默认编译器更改为gcc即可
>![更改成gcc](https://upload-images.jianshu.io/upload_images/17890238-a8a3203a9add6c08.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)我们可以看到在setting.json里多了默认gcc的设置
![](https://upload-images.jianshu.io/upload_images/17890238-3f033a5e776d48ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

不会再提示头文件的错误，也会检查代码错误了
>![成功检查代码错误，并给出代码补全](https://upload-images.jianshu.io/upload_images/17890238-a57abedb8f49b834.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


***
 ## 最后推荐几款好用的VS Code 插件
* Chinese (Simplified) Language Pack for Visual Studio Code 
中文插件
* One Dark Pro 
很好看的主题插件
* Tabout 
Tab键跳出右括号，对于习惯了 Visual Studio 的用户超级方便
>效果如下![](https://upload-images.jianshu.io/upload_images/17890238-24e2c09009c574a4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

本编文章面向未使用过 VS Code 的用户及编程初学者。如果您正在寻找一款轻量化，颜值高的文本编辑器，同时又有轻度调试需求的话，不妨试试VS Code。
