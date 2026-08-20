# NyaLauncher Plugin SDK

`NyaLauncher.Plugin.Abstractions.dll` 是插件编译时使用的 API v1 引用，来源于
[`redstore-noob/NyaLauncher`](https://github.com/redstore-noob/NyaLauncher) 的 `testplug`
分支，SDK 版本为 `0.1.1-gp3`。

- 文件大小：`121344` 字节
- SHA-256：`b104f6b39ec506c2d656c171753a49c829df20fcd3c28392c7d7399849722dc9`

它仅用于编译和测试。NyaLauncher 在运行时提供同一 API 程序集，`package.ps1` 会确保发布 ZIP
中不包含这个 DLL。
