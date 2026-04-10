.. raw:: html

   <div style="text-align: right"><a href="../../en/latest/index.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/index.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/index.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/index.html">🇯🇵 日本語</a></div>

quardCRT
----------------------------------

.. image:: https://img.shields.io/github/actions/workflow/status/qqxiaoming/quardCRT/windows.yml?branch=main&logo=data:image/svg+xml;base64,PHN2ZyByb2xlPSJpbWciIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48dGl0bGU+V2luZG93czwvdGl0bGU+PHBhdGggZD0iTTAsMEgxMS4zNzdWMTEuMzcySDBaTTEyLjYyMywwSDI0VjExLjM3MkgxMi42MjNaTTAsMTIuNjIzSDExLjM3N1YyNEgwWm0xMi42MjMsMEgyNFYyNEgxMi42MjMiIGZpbGw9IiNmZmZmZmYiLz48L3N2Zz4=
   :target: https://github.com/QQxiaoming/quardCRT/actions/workflows/windows.yml
   :alt: Windows ci
.. image:: https://img.shields.io/github/actions/workflow/status/qqxiaoming/quardCRT/linux.yml?branch=main&logo=linux&logoColor=white
   :target: https://github.com/QQxiaoming/quardCRT/actions/workflows/linux.yml
   :alt: Linux ci
.. image:: https://img.shields.io/github/actions/workflow/status/qqxiaoming/quardCRT/macos_arm64.yml?branch=main&logo=apple
   :target: https://github.com/QQxiaoming/quardCRT/actions/workflows/macos_arm64.yml
   :alt: Macos ci
.. image:: https://img.shields.io/codefactor/grade/github/qqxiaoming/quardCRT.svg?logo=codefactor
   :target: https://www.codefactor.io/repository/github/qqxiaoming/quardCRT
   :alt: CodeFactor
.. image:: https://img.shields.io/readthedocs/quardcrt.svg?logo=readthedocs
   :target: https://quardcrt.readthedocs.io/en/latest/?badge=latest
   :alt: Documentation Status
.. image:: https://img.shields.io/github/license/qqxiaoming/quardCRT.svg?colorB=f48041&logo=gnu
   :target: https://github.com/QQxiaoming/quardCRT
   :alt: License
.. image:: https://img.shields.io/github/v/tag/QQxiaoming/quardCRT?filter=V*&logo=git
   :target: https://github.com/QQxiaoming/quardCRT/releases
   :alt: GitHub tag (latest SemVer)
.. image:: https://img.shields.io/github/downloads/QQxiaoming/quardCRT/total.svg?logo=pinboard
   :target: https://github.com/QQxiaoming/quardCRT/releases
   :alt: GitHub All Releases
.. image:: https://img.shields.io/github/stars/QQxiaoming/quardCRT.svg?logo=github
   :target: https://github.com/QQxiaoming/quardCRT
   :alt: GitHub stars
.. image:: https://img.shields.io/github/forks/QQxiaoming/quardCRT.svg?logo=github
   :target: https://github.com/QQxiaoming/quardCRT
   :alt: GitHub forks
.. image:: https://gitee.com/QQxiaoming/quardCRT/badge/star.svg?theme=dark
   :target: https://gitee.com/QQxiaoming/quardCRT
   :alt: Gitee stars
.. image:: https://gitee.com/QQxiaoming/quardCRT/badge/fork.svg?theme=dark
   :target: https://gitee.com/QQxiaoming/quardCRT
   :alt: Gitee forks

.. image:: ./img/social_preview.jpg
   :align: center
   :alt: quardCRT

quardCRT 是一款面向 Windows、Linux 和 macOS 的跨平台终端模拟器与远程桌面客户端。它强调跨平台一致的使用体验，同时提供现代日常终端软件常见的能力，例如多标签工作流、会话管理、文件传输、主题切换、界面语言切换，以及持续扩展中的插件生态。

quardCRT 的设计目标，是让用户可以低门槛开始使用，同时又具备足够的能力来胜任日常开发、嵌入式调试、服务器维护以及轻量级远程桌面工作。

----------------------------------
快速开始
----------------------------------

1. 阅读 :doc:`安装指南 <installation>`，选择与你的平台匹配的安装包。
2. 按照 :doc:`使用指南 <usage>` 熟悉主界面布局、快速连接流程和常见操作。
3. 使用 :doc:`配置指南 <configuration>` 调整外观、终端行为、传输目录和高级选项。

----------------------------------
quardCRT 提供什么
----------------------------------

- 在 Windows、Linux、macOS 上提供大体一致工作流的跨平台桌面客户端
- 在一个应用中整合常见终端和远程访问协议
- 已保存会话、标签工作流、分屏布局和浮动窗口
- 支持 SFTP、Xmodem、Ymodem、Zmodem、Kermit 的文件传输能力
- 面向用户的字体、配色、光标、滚动缓冲区、背景媒体等自定义能力
- 多语言界面和插件扩展能力

.. list-table:: 
   :widths: 33 33 33
   :header-rows: 0

   * - .. image:: ./img/windows.png
          :align: center
          :height: 160px
     - .. image:: ./img/macos.png
          :align: center
          :height: 160px
     - .. image:: ./img/linux.png
          :align: center
          :height: 160px
   * - Windows
     - MacOS
     - Linux

----------------------------------
功能
----------------------------------

- **跨平台**: Windows、macOS、Linux
- **协议**: SSH、Telnet、Serial、Local Shell、Raw Socket、Named Pipe、VNC
- **会话工作流**: 多标签、多窗口、分屏、浮动窗口
- **语言**: 英语、简体中文、繁体中文、日语、韩语、西班牙语、法语、俄语、德语、葡萄牙语（巴西）、捷克语、阿拉伯语
- **主题**: 亮色与暗色
- **会话历史**: 历史保存与快速搜索
- **会话管理**: 创建、保存、整理、导入、导出会话
- **HEX显示**: 以十六进制查看终端输出
- **文件传输**: SFTP、Xmodem、Ymodem、Zmodem、Kermit
- **终端定制**: 字体、颜色、光标、回滚、背景图片或视频等

----------------------------------
特别功能
----------------------------------

- 标签浮动预览
- 支持浮动窗口，标签拖拽到浮动窗口
- SSH2会话一键打开SFTP文件传输窗口
- 工作目录书签
- 自动发送
- 终端背景图支持gif动画和视频
- 终端关键字高亮匹配
- 选中文本翻译功能
- 路径匹配一键直达
- 工作路径直达
- Windows本地终端增强（Tab键选择完整命令等）
- 广播会话
- 会话标签颜色
- 块选择（Shift+单击）和列选择（Alt+Shift+单击）

----------------------------------
文档导读
----------------------------------

- :doc:`安装 <installation>`：下载渠道、安装包选择和平台安装步骤
- :doc:`使用 <usage>`：界面概览、第一次上手操作、菜单和工具栏说明
- :doc:`配置 <configuration>`：全局选项、会话行为、存储位置和高级设置
- :doc:`脚本 <scripts>`：脚本功能使用方式与 API 概览
- :doc:`插件 <plugins>`：插件体系、模板工程和参考示例
- :doc:`常见问题 <faq>`：许可证、隐私和常见问答

----------------------------------
插件
----------------------------------

quardCRT 从 V0.4.0 开始支持插件。插件以 Qt 插件形式提供，并以动态库方式加载。若想了解插件开发资源、模板和示例，请参见插件 `platform <https://github.com/QuardCRT-platform>`_。如果你对插件系统有想法或建议，欢迎在 `GitHub <https://github.com/QQxiaoming/quardCRT>`_ 或 `Gitee <https://gitee.com/QQxiaoming/quardCRT>`_ 上提交 issue 或 discussion。

----------------------------------
从商店安装
----------------------------------

- .. image:: https://get.microsoft.com/images/zh-cn%20dark.svg
   :target: https://apps.microsoft.com/detail/quardCRT/9p6102k9qb3t?mode=direct
   :alt: Microsoft Store

- .. image:: https://www.spark-app.store/assets/favicon-96x96-BB0Q9LsV.png
   :target: https://spk-resolv.spark-app.store/?spk=spk://store/development/quardcrt
   :alt: Spark Store

----------------------------------
捐赠
----------------------------------

如果你觉得 quardCRT 对你有帮助，可以通过捐赠支持项目持续开发。

.. list-table:: 
   :widths: 33 33 33
   :header-rows: 0

   * - .. image:: ./img/donate/paypal.jpg
          :align: center
     - .. image:: ./img/donate/alipay.jpg
          :align: center
     - .. image:: ./img/donate/wechat.jpg
          :align: center
   * - paypal
     - alipay
     - wechat

.. toctree::
   :maxdepth: 3
   :caption: 目录:

   安装<installation.md>
   使用<usage.md>
   配置<configuration.md>
   脚本<scripts.md>
   插件<plugins.md>
   常见问题<faq.md>
   贡献<contributing.md>
   更新日志<changelog.md>
   许可证<license.md>
   路线图<roadmap.md>
   致谢<acknowledgements.md>
   隐私<privacy.md>
 