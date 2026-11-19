# Changelog

## 2026-11-19

- 更新 OpenCore 1.0.8 EFI。
- 恢复 OpenCanopy + GoldenGate 图形启动菜单。
- 自动启动超时设为 5 秒。
- 修复 Intel AC 8265 Wi-Fi：AirportItlwm 2.4.0 + SSDT-AXPWR + GPP4 DSDT 补丁。
- 安装 MonitorControl 4.4.0 作为外接显示器亮度工具。
- 清空仓库中的个人 SMBIOS 三码。
- 增加 config-debug.plist。

## 已知限制

- x86_64 无法运行 arm64 应用。
- 睡眠/唤醒未做长期验证。
- 外接显示器 DDC 亮度取决于显示器。

