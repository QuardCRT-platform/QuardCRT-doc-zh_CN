<div style="text-align: right"><a href="../../en/latest/plugins.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/plugins.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/plugins.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/plugins.html">🇯🇵 日本語</a></div>

# 插件

quardCRT 从 V0.4.0 开始支持插件。插件以 Qt 插件方式实现，并以动态库形式加载。

本页同时覆盖插件系统的两个方面：

- 普通用户如何理解和使用插件功能
- 开发者如何基于 quardCRT 插件 API 编写插件

## 面向用户

插件可以根据自身能力，从多个方向扩展 quardCRT，例如：

- 为主界面添加动作或菜单
- 向终端右键菜单中添加条目
- 在应用侧边栏区域提供自定义插件面板
- 触发与连接相关的操作，例如打开 SSH、串口、Raw Socket 或 VNC 会话

quardCRT 还提供插件信息窗口，用于展示插件状态、兼容性信息以及初始化错误。

### 插件加载行为

启动时，quardCRT 会尝试从自身插件目录加载内置插件。如果你在应用设置中配置了额外的插件目录，也会尝试从该目录加载插件。

如果某个插件加载失败，quardCRT 不会静默当作成功，而是会在插件信息对话框中记录失败原因。

常见原因包括：

- 缺少插件元数据
- 插件 API 版本不受支持
- 初始化失败
- 缺少 quardCRT 预期的菜单或控件入口点

### 启用和禁用插件

插件启用状态会保存在应用设置中。对于支持的插件，可以在插件信息对话框中启用或禁用。

这在以下场景中很有用：

- 你想临时禁用某个插件，而不删除它的文件
- 你在测试新插件，希望可以快速回退
- 你希望在不同机器上使用不同的插件组合

## 插件开发

### API

插件 API 规范维护在 [plugininterface](https://github.com/QuardCRT-platform/plugininterface) 仓库中。

开发自定义插件时，常见流程如下：

- 包含 plugininterface.h 头文件
- 定义插件类，并继承 PluginInterface
- 实现 PluginInterface 要求的方法
- 针对目标平台构建 `dll`、`so` 或 `dylib` 等原生插件库
- 将构建好的插件放到 quardCRT 可以加载的位置

在实际开发中，一个有用的插件通常会提供以下一项或多项能力：

- 主菜单动作或菜单
- 侧边栏面板
- 终端右键菜单项
- 通过插件设置读写钩子保存自己的配置
- 通过 `setLanguage()` 和 `retranslateUi()` 实现多语言支持

以下是一个最简单的示例：

```c++
#include "plugininterface.h"

#include <QMap>
#include <QMessageBox>
#include <QDebug>

#define PLUGIN_NAME    "Hello World"
#define PLUGIN_VERSION "0.0.1"

class HelloWorld : public PluginInterface
{
    Q_OBJECT
    Q_PLUGIN_METADATA(IID "org.quardCRT.PluginInterface" FILE "../plugininterface.json")
    Q_INTERFACES(PluginInterface)

public:
    HelloWorld() : m_action(nullptr) {}
    virtual ~HelloWorld() {}

    int init(QMap<QString, QString> params, QWidget *parent) {
        foreach (QString key, params.keys()) {
            qDebug() << key << " : " << params[key];
        }
        qDebug() << "Hello World init";
        m_action = new QAction("Hello World", parent);
        connect(m_action, &QAction::triggered, [parent](){
            QMessageBox::information(parent, "Hello World", "Hello World");
        });

        return 0;
    }

    void setLanguage(const QLocale &language,QApplication *app) {Q_UNUSED(language);Q_UNUSED(app);}
    void retranslateUi() {}
    QString name() { return PLUGIN_NAME; }
    QString version() { return PLUGIN_VERSION; }

    QMap<QString,void *> metaObject() {
        QMap<QString,void *> ret;
        ret.insert("QAction", (void *)m_action);
        return ret;
    }

    QMenu *terminalContextMenu(QString selectedText, QString workingDirectory, QMenu *parentMenu) {Q_UNUSED(selectedText);Q_UNUSED(workingDirectory);Q_UNUSED(parentMenu); return nullptr;}
    QList<QAction *> terminalContextAction(QString selectedText, QString workingDirectory, QMenu *parentMenu) {Q_UNUSED(selectedText);Q_UNUSED(workingDirectory);Q_UNUSED(parentMenu); return QList<QAction *>();}
    
private:
    QAction *m_action;
};
```

### 模板工程

对于新插件开发，我们推荐使用 GitHub 模板工程 [plugin-template](https://github.com/QuardCRT-platform/plugin-template)。

这个模板已经包含：

- 插件开发所需的项目结构
- 构建脚本和工程配置
- 基于 GitHub Actions 的 CI 设置

这样你可以把更多精力放在插件逻辑本身，而不是从零搭建项目骨架。

### 兼容性说明

构建插件时，请注意以下几点：

- 插件必须匹配运行中 quardCRT 所期望的插件 API 版本
- 插件是原生二进制，因此编译器、Qt 版本、架构和平台兼容性都很重要
- 如果插件依赖额外的共享库，这些库在运行时也必须可用

如果一个插件看起来没问题但仍然无法加载，插件信息窗口通常是首个排查位置。

## 实例

目前 quardCRT 已经有一些开源插件，可以作为开发参考：

- [plugin-SearchOnWeb](https://github.com/QuardCRT-platform/plugin-SearchOnWeb)

为终端右键菜单增加搜索动作，可将选中文本快速发送到 Google、Bing、百度、GitHub 等服务。

- [plugin-quickcomplete](https://github.com/QuardCRT-platform/plugin-quickcomplete)

提供用户自定义命令，用于快速发送到当前会话。

- [plugin-onestep](https://github.com/QuardCRT-platform/plugin-onestep)

提供预填写 SSH 信息和更高效的主机选择流程，在嵌入式开发或设备初始化场景中比较实用。

## 更多

想了解更多信息、模板和相关仓库，请参考 quardCRT 插件开放平台：

- [https://github.com/QuardCRT-platform](https://github.com/QuardCRT-platform)

插件系统仍在持续演进中。如果你对插件 API、扩展点或开发者工具有想法，欢迎在 GitHub 或 Gitee 上提交 issue 或 discussion。
