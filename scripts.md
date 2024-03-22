<div style="text-align: right"><a href="../../en/latest/scripts.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/scripts.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/scripts.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/scripts.html">🇯🇵 日本語</a></div>

# 脚本

quardCRT从V0.5.0版本开始支持脚本功能。脚本以Python语言的形式加载，可以在脚本中调用quardCRT的API，以实现自动化操作。

## 加载脚本

打开主界面，点击菜单栏的`脚本`，选择`运行...`，选择脚本文件，点击`打开`即可加载脚本。

## 示例

以下是一个简单的脚本示例，用于显示quardCRT的版本信息。

```python
import sys
from quardCRT import crt

def main():
    # Display quardCRT's version
    crt.Dialog.MessageBox("quardCRT version is: " + crt.Version)

if __name__ == '__main__':
    main()
```

quardCRT加载的脚本与通常的Python脚本并无区别，现在我们逐行解释这个脚本。

- `import sys`：导入`sys`模块，用于获取命令行参数。
- `from quardCRT import crt`：导入quardCRT的API。
- `def main():`：定义一个`main`函数，用于执行脚本的主要逻辑。
- `# Display quardCRT's version`：注释，用于解释下一行代码的作用。
- `crt.Dialog.MessageBox("quardCRT version is: " + crt.Version)`：调用quardCRT的API，显示一个消息框，显示quardCRT的版本信息。
- `if __name__ == '__main__':`：判断脚本是否作为主程序运行。
- `main()`：调用`main`函数，执行脚本的主要逻辑。

## API

quardCRT的API包括以下几个部分：

- `crt`：quardCRT的主要API。
- `crt.Dialog`：用于显示对话框。
- `crt.Session`：用于管理会话。
- `crt.Screen`：用于管理屏幕。

### crt

`crt`是quardCRT的主要API，包括以下几个部分：

#### 方法

- `crt.GetActiveTab() -> object`：获取当前活动的标签页。
- `crt.GetLastError() -> object`：获取最后一次发生的错误。
- `crt.GetLastErrorMessage() -> str`：获取最后一次发生的错误信息。
- `crt.ClearLastError()`：清除最后一次发生的错误。
- `crt.Sleep(milliseconds: int)`：暂停脚本的执行。
- `crt.Quit()`：退出quardCRT。

#### 属性

- `crt.Dialog`：全局对话框对象。
- `crt.Session`：当前会话对象。
- `crt.Screen`：当前屏幕对象。
- `crt.Window`：全局窗口对象。
- `crt.ScriptFullName`：当前脚本的完整路径。只读。
- `crt.ActivePrinter`：当前活动的打印机名称。
- `crt.Version`：quardCRT的版本信息。只读。

### Dialog

`Dialog`用于显示对话框，包括以下几个部分：

#### 方法

- `Dialog.MessageBox(message: str, title: str = None, type: int = 0) -> int`：显示一个消息框。
- `Dialog.InputBox(prompt: str, title: str = None, default: str = None, type: int = 0) -> str`：显示一个输入框。
- `Dialog.FileOpenDialog(title: str = None, filter: str = None, initial_dir: str = None) -> str`：显示一个打开文件对话框。
- `Dialog.FileSaveDialog(title: str = None, filter: str = None, initial_dir: str = None) -> str`：显示一个保存文件对话框。

#### 属性

- `Dialog.OK`：确定按钮。只读。
- `Dialog.Cancel`：取消按钮。只读。
- `Dialog.Abort`：中止按钮。只读。
- `Dialog.Retry`：重试按钮。只读。
- `Dialog.Ignore`：忽略按钮。只读。
- `Dialog.Yes`：是按钮。只读。
- `Dialog.No`：否按钮。只读。

### Session

`Session`用于管理会话，包括以下几个部分：

#### 方法

- `Session.Connect(hostname: str, port: int, protocol: int, username: str, password: str) -> bool`：连接到一个主机。
- `Session.Disconnect()`：断开当前会话。

### Screen

`Screen`用于管理屏幕，包括以下几个部分：

- `Screen.Send(text: str)`：发送文本到屏幕。
- `Screen.WaitForString(text: str, timeout: int) -> int`：等待屏幕出现指定的文本。

#### 属性

- `Screen.Synchronous`：同步模式。

### Window

`Window`用于管理应用窗口，包括以下几个部分：

#### 方法

- `Window.Activate()`：激活窗口。
- `Window.Show(type: int)`：显示窗口。

#### 属性

- `Window.State`：当前窗口显示类型。
- `Window.Active`：当前窗口是否激活。
- `Window.Hide`：隐藏窗口。只读。
- `Window.ShowNormal`：正常显示窗口。只读。
- `Window.ShowMinimized`：最小化窗口。只读。
- `Window.ShowMaximized`：最大化窗口。只读。
