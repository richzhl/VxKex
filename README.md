引言
============

VxKex 是一套适用于 Windows 7 的 API 扩展工具，可让部分仅支持 Windows 8、8.1 和 10 的应用程序在 Windows 7 上运行。
如需下载和安装，请访问 [发布页面](https://github.com/i486/VxKex/releases)。
安装完成后，使用方法非常简单：只需右键点击某个程序（.exe 或 .msi 文件），打开属性对话框，选择 VxKex 标签页，然后勾选“为该程序启用 VxKex”复选框，即可尝试运行该程序。
![VxKex 配置 GUI](/example-screenshot.png)  
某些程序需要额外的配置。VxKex 安装文件夹（默认为 C:\Program Files\VxKex）中有一个名为“Application Compatibility List.docx”的文件，详细说明了这些步骤，但大多数情况下，所有配置都较为直观易懂。  
如果您是开发者，源代码将以 7z 文件形式提供在发布页面上。
常见问题
===
**问：它适用于游戏吗？****
**A：** 目前，VxKex 并不适用于游戏，因此你可能取得的成果有限。我希望在未来的版本中解决这一不足。
**Q：支持哪些应用程序？****
**A：** 兼容的应用程序列表包括但不限于：
- Bespoke Synth
- Blender
- Blockbench
- Calibre
- Chromium（包括非谷歌浏览器Chromium）
- Citra
- Commander Wars
- Cygwin
- Dasel
- Discord Canary
- ElectronMail
- Firefox
- GIMP（2.99.18）
- GitHub Desktop
- HandBrake
- Kodi
- Life is Strange: True Colors 4.25
- MKVToolNix
- MongoDB
- MPC-Qt
- MPV
- MPV网
- 好歌
- osu!激光
- Python  
- qBittorrent  
- QMMP  
- Qt Creator  
- Rufus  
- Steel Bank Common Lisp  
- Spotify  
- Steinberg SpectraLayers  
- TeamTalk  
- VSCode 和 VSCodium  
- WinDbg（Windows 11 SDK 中的经典版本及预览版）  
- Yuzu（游戏玩法未测试）  
- Zig  

更多信息，请参见随 VxKex 一同安装的 **Application Compatibility List.docx** 文件。
大多数 Qt6 应用程序都能正常运行，许多 Electron 应用程序也同样适用。
*问：VxKex 是否会修改系统文件？会不会导致系统不稳定？****
*答：** VxKex 不会修改任何系统文件，对整个系统的整体影响极小。它不使用任何后台服务，也不会安装全局钩子，所加载的 shell 扩展和 DLL 也仅产生最小影响，必要时可将其禁用。您可以放心，您的 Windows 7 将保持一如既往的稳定。
*问：我是否需要安装特定的更新？****
*答：** VxKex 仅适用于已安装 Service Pack 1 的系统。Windows 7 RTM 用户可以尝试使用，但不确定是否能成功安装或运行。许多程序在运行时需要 KB2533623 和 KB2670838 更新，因此建议安装这两个补丁。
*问：如果我已安装扩展安全更新（ESUs），还能使用 VxKex 吗？****
*答：** 是的，ESU 没有问题。
*问：控制台应用程序能与 VxKex 共同工作吗？****
*答：** 是的。在为某个程序启用 VxKex 后，您就可以像平常一样通过命令提示符使用它。
*问：** 我可以使用这个功能吗？Windows 8 或 8.1 是否支持？**
*答：** VxKex 仅适用于 Windows 7。如果您使用的是 Windows 8 或 8.1，VxKex 很可能无法正常工作，但您可以尝试安装它，看看会发生什么。
*问：VxKex 是如何工作的？****
*答：** VxKex 的工作原理是将一个 DLL 加载到每个启用 VxKex 的程序中。这个
通过使用IFEO（图像文件执行选项）注册表键来实现。  
具体来说，将“VerifierDlls”值设置为指向一个VxKex DLL，该DLL随后加载到进程中。  
API扩展是通过编辑程序的DLL导入表来实现的，使其不再从Windows 8/8.1/10的DLL中导入，而是转而导入VxKex DLL。这些VxKex DLL包含了在较新版本Windows中引入的Windows API函数的实现。
捐赠
=========

如果您希望支持开发，可以考虑进行捐赠。  
- https://paypal.me/vxiiduu
