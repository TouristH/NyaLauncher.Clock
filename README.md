# NyaLauncher 电子时钟示例插件

这是一个严格使用 `NyaLauncher.Plugin.Abstractions` API v1 的电子时钟组件示例，稳定插件 ID 为
`io.github.touristh.example-clock`。它不引用 Avalonia 或启动器内部类型，只通过声明式 Polygon
组件和宿主管理的设置运行。

## 功能

- 时和分占据组件绝大部分面积。
- 可切换 24 小时制或 12 小时制。
- 时区位于顶端的小区域，可单独隐藏。
- 秒位于右下角的小区域，可单独隐藏。
- 组件大小可在 65%–160% 之间调整，并即时更新已放置实例。
- 首次启用只加入组件库，不会自动创建工作区。

设置键为 `time.format`、`display.scale`、`display.timezone` 和 `display.seconds`；组件 ID 为
`io.github.touristh.example-clock/digital-clock`。

## 构建和测试

需要 .NET 10 SDK。仓库中的 `sdk/NyaLauncher.Plugin.Abstractions.dll` 仅用于编译，发布包不会包含它。

```powershell
dotnet build .\NyaLauncher.Clock.slnx -c Release
dotnet run --project .\tests\NyaLauncher.Clock.Tests.csproj -c Release
powershell -NoProfile -ExecutionPolicy Bypass -File .\package.ps1
```

`package.ps1` 生成 `artifacts/io.github.touristh.example-clock-1.0.0.zip`，并输出精确字节数与
小写 SHA-256。ZIP 根目录直接包含 `plugin.json`、`NyaLauncher.Clock.dll`、`README.md` 和
`LICENSE`。

## 生命周期

每个组件实例持有自己的刷新任务和设置事件订阅。`DisposeAsync` 会解除订阅、取消并等待刷新任务，
插件禁用或工作区关闭后不会遗留定时器或静态引用。

## 许可证

MIT，见 [LICENSE](LICENSE)。
