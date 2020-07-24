## 问题描述
Windows上面安装Visual Studio Code编辑器后,常常会因为安装的时候忘记勾选等原因,没有将`"Open with Code(右键快捷方式)"`添加到鼠标右键菜单里,使用起来多有不便,所以需要我们手动将VSCode添加至鼠标右键菜单之中.

## 解决办法
- 新建reg后缀文件。
- 复制下面内容到刚才新建的reg文件中,文本内容如下（**注意修改为自己的vscode安装路径**）:
- 双击运行该脚本即可。
```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\*\shell\VSCode]
@="Open with Code"
"Icon"="C:\\Program Files\\Microsoft VS Code\\Code.exe"

[HKEY_CLASSES_ROOT\*\shell\VSCode\command]
@="\"C:\\Program Files\\Microsoft VS Code\\Code.exe\" \"%1\""

Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\shell\VSCode]
@="Open with Code"
"Icon"="C:\\Program Files\\Microsoft VS Code\\Code.exe"

[HKEY_CLASSES_ROOT\Directory\shell\VSCode\command]
@="\"C:\\Program Files\\Microsoft VS Code\\Code.exe\" \"%V\""

Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\Background\shell\VSCode]
@="Open with Code"
"Icon"="C:\\Program Files\\Microsoft VS Code\\Code.exe"

[HKEY_CLASSES_ROOT\Directory\Background\shell\VSCode\command]
@="\"C:\\Program Files\\Microsoft VS Code\\Code.exe\" \"%V\""
```