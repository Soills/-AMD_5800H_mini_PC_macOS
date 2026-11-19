# 常见问题

## 开机停在 OpenCore 菜单

选中 macOS 后按 `Ctrl+Enter` 设为默认启动项。

相关配置：

- `Misc -> Boot -> Timeout = 5`
- `Misc -> Boot -> ShowPicker = true`
- `Misc -> Security -> AllowSetDefault = true`

## 图形启动菜单消失

检查：

- `EFI/OC/Drivers/OpenCanopy.efi` 存在并启用
- `EFI/OC/Resources/Image/Acidanthera/GoldenGate` 存在
- `Misc -> Boot -> PickerMode = External`
- `Misc -> Boot -> PickerVariant = Acidanthera\\GoldenGate`

## 外接显示器偏暗

外接亮度通常由显示器 OSD 控制。

可安装 `tools/MonitorControl.4.4.0.dmg`，用 DDC/CI 调亮度。也可在系统设置里尝试 sRGB 颜色描述文件，并关闭 HDR。

## Wi-Fi 没有 en2

检查：

```bash
/usr/sbin/kextstat -b com.zxystd.AirportItlwm
networksetup -listallhardwareports
```

并确认 GPP4 电源补丁和 `SSDT-AXPWR.aml` 已启用。

## 无法运行 ARM 软件

AMD/Intel x86_64 无法运行 arm64 macOS 应用。Rosetta 是 Apple Silicon 运行 x86_64，不是反向。请使用 x86_64 / Universal 版本或换 Apple Silicon Mac。

## 查看启动日志

- 屏幕：`-v debug=0x100 keepsyms=1`
- OpenCore 日志：`EFI/OC/opencore-*.txt`
- 可改名使用 `config-debug.plist`（`Misc -> Debug -> Target = 67`）

