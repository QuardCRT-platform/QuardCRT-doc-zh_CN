<div style="text-align: right"><a href="../../en/latest/installation.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/installation.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/installation.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/installation.html">🇯🇵 日本語</a></div>

# 安装

quardCRT 提供 Windows、macOS 和 Linux 安装包。如果你的平台有官方应用商店条目，通常这是最简单的安装方式。否则，你可以从 GitHub、Gitee 或 SourceForge 下载发布包。

## 下载前建议

- 如果你只是想安装并使用 quardCRT，选择与你的操作系统和 CPU 架构对应的安装包即可。
- 如果你打算在 Windows 上构建或加载原生插件，建议优先选择 MSVC 安装包，以便运行时与常见 MSVC 插件工具链保持一致。
- 如果你使用 Apple Silicon，请选择 macOS 的 `arm64` 安装包。
- 在 Linux 上，如果你需要便携的单文件启动方式，可选 AppImage；如果你使用 Debian 系发行版并希望交给包管理器管理，可选 `deb` 包。

## 应用商店

quardCRT 目前可在以下应用商店获取：

- [![Microsoft Store](https://get.microsoft.com/images/zh-cn%20dark.svg)](https://apps.microsoft.com/detail/quardCRT/9p6102k9qb3t?mode=direct)
- [星火商店](https://www.spark-app.store/store/application/quardcrt)
- 深度商店

如果你的平台或发行版商店未列在这里，请使用下面的发布包安装。

## 下载

### 所有平台

要下载最新版本，请访问以下发布页：

- [GitHub Releases](https://github.com/QQxiaoming/quardCRT/releases)
- [Gitee Releases](https://gitee.com/QQxiaoming/quardCRT/releases)
- [SourceForge](https://sourceforge.net/projects/quardcrt/files/)

发布资源目前提供以下格式：

- Windows:
    - `quardCRT_windows_Vxxx_x86_64_setup.exe`
    - `quardCRT_windows_Vxxx_x86_64_msvc_setup.exe`
- macOS:
    - `quardCRT_macos_Vxxx_x86_64.dmg`
    - `quardCRT_macos_Vxxx_arm64.dmg`
- Linux:
    - `quardCRT_Linux_Vxxx_x86_64.AppImage`
    - `quardCRT_Linux_Vxxx_x86_64.deb`
- 源代码:
    - `quardCRT_Vxxx_source.tar.gz`
    - `quardCRT_Vxxx_source.zip`

### Windows

Windows 下可选择 `quardCRT_windows_Vxxx_x86_64_setup.exe` 或 `quardCRT_windows_Vxxx_x86_64_msvc_setup.exe`。

- `setup.exe`：MinGW 构建，适合普通用户，兼容性较好。
- `msvc_setup.exe`：MSVC 构建，如果你需要与 MSVC 构建的插件或其他原生组件保持运行时兼容，建议使用此版本。

#### 安装

运行安装程序并按照向导完成安装：

1. 选择语言，然后点击 `确定`。

![Windows安装包示例](./img/installation_4.png)

2. 点击 `下一步`。

![Windows安装包示例](./img/installation_5.png)

3. 选择安装目录，然后点击 `下一步`。

![Windows安装包示例](./img/installation_6.png)

4. 选择是否创建桌面快捷方式，然后点击 `下一步`。

![Windows安装包示例](./img/installation_7.png)

5. 点击 `安装`。

![Windows安装包示例](./img/installation_8.png)

6. 点击 `完成`。

![Windows安装包示例](./img/installation_9.png)

安装完成后，你可以从开始菜单或桌面快捷方式启动 quardCRT。

### macOS

Intel Mac 请下载 `quardCRT_macos_Vxxx_x86_64.dmg`，Apple Silicon Mac 请下载 `quardCRT_macos_Vxxx_arm64.dmg`。

#### 安装

打开 DMG 后，按常规 macOS 应用安装方式操作：

1. 双击 `quardCRT` 图标。
2. 将 `quardCRT` 图标拖到 `应用程序` 文件夹。

![dmg包安装示例](./img/installation_3.png)

> 注意：当前提供的 macOS 预构建安装包尚未经过 Apple 官方签名。首次打开时，macOS 可能提示应用来自未识别的开发者。如果你信任该安装包，可以执行 `xattr -cr /Applications/quardCRT.app` 去掉隔离属性；如果你不信任它，请不要绕过系统警告，而应改为自行从源码构建。

### Linux

Linux 下可以在以下两种格式中选择：

- `quardCRT_Linux_Vxxx_x86_64.AppImage`：便携式单可执行文件
- `quardCRT_Linux_Vxxx_x86_64.deb`：适用于 Debian、Ubuntu、Deepin 等 Debian 系发行版

#### 安装

- AppImage

AppImage 不需要安装，赋予可执行权限后即可直接运行：

```bash
chmod +x quardCRT_Linux_Vxxx_x86_64.AppImage
./quardCRT_Linux_Vxxx_x86_64.AppImage
```

- deb

你可以使用图形化包管理器安装 Debian 包，也可以在命令行安装。

图形界面安装：

1. 双击安装包。
2. 点击 `安装软件包`。

![deb包安装示例1](./img/installation_1.png)

3. 输入密码，然后点击 `验证`。
4. 点击 `关闭`。

![deb包安装示例2](./img/installation_2.png)

命令行安装：

```bash
sudo dpkg -i quardCRT_Linux_Vxxx_x86_64.deb
```

如果系统报告依赖问题，可以改用包管理器处理，例如：

```bash
sudo apt install ./quardCRT_Linux_Vxxx_x86_64.deb
```

## 首次启动

安装完成后，常见的第一步是：

1. 打开 quardCRT。
2. 如果发行包提示选择语言，则选择你需要的界面语言。
3. 通过会话管理器或快速连接创建一个连接。
4. 如果需要调整主题、字体、传输路径或高级设置，打开 `选项 > 全局选项`。

接下来可以继续阅读 [使用指南](./usage.md)。
