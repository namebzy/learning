# WinDbg调试工具使用

## 参考链接

[Windows 调试工具（WinDbg、KD、CDB、NTSD）](https://docs.microsoft.com/zh-cn/windows-hardware/drivers/debugger/)

[安装与配置windbg的symbol(符号)](https://blog.csdn.net/whatday/article/details/7290164)

## WinDbg下载与配置

- 下载

  直接登录[微软WinDbg官网](https://docs.microsoft.com/zh-cn/windows-hardware/drivers/debugger/debugger-download-tools)下载 [WinDbg Preview](https://www.microsoft.com/store/p/windbg/9pgjgd53tn86)或者[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)

- 配置

## 使用WinDbg分析dmp文件

- 步骤1：打开对应版本的WinDbg程序
- 步骤2：File-Symbol File Path设置为`srv*c:\MyServerSymbols*https://msdl.microsoft.com/download/symbols`
- 步骤3：File-Source File Path设置为代码目录
- 步骤4：File-Open Crash Dump
- 步骤5：运行相应命令分析dmp文件

## WinDbg常用命令

|    命令     |         作用         |
| :---------: | :------------------: |
| !analyze -v |       一键分析       |
|    .excr    |    定位到崩溃位置    |
|     kp      | 查看崩溃时的堆栈信息 |
|             |                      |