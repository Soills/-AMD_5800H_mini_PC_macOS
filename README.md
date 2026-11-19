# MoreFine S500+ AMD Cezanne Hackintosh

适用于 **MoreFine S500+ AMD 迷你主机** 的 OpenCore EFI，当前验证系统为 **macOS Sequoia 15.6 (24G84)**。

这个仓库不是万能 EFI，而是针对下面这台机器的实际配置整理：

## 硬件配置

| 项目 | 配置 |
| --- | --- |
| 主机 | MoreFine S500+ / DEFAULT MOREFINE S500+ |
| BIOS | S013_V1.2_P3C3M43_MoreFine / UEFI / Secure Boot Disabled |
| CPU | AMD Ryzen 7 5800H（ES OPN 100-000000295-40_Y）/ Cezanne / 8 核 16 线程 |
| 核显 | AMD Radeon Graphics / 1002:1638 / Cezanne |
| 硬盘 | KINGSTON SNV2S500G / NVMe / 控制器 2646:5019 |
| 有线网卡 1 | Realtek RTL8125 2.5GbE / 10EC:8125 |
| 有线网卡 2 | Realtek RTL8111 GbE / 10EC:8168 |
| 无线网卡 | Intel AC 8265 / 8086:24FD |
| 蓝牙 | Intel Bluetooth / 8087:0A2B |
| 声卡 | Realtek ALC269 / 10EC:0269 / AMD HDA 1022:15E3 |
| 显示器 | S-2450QPC / DP / 2560x1440 |
| SMBIOS | iMacPro1,1 / -no_compat_check |

> 原始 Windows 硬件报告见 docs/Report.json。

## 当前状态

| 功能 | 状态 |
| --- | --- |
| 核显 / Metal | ✅ NootedRed 0.8.10，Metal 3 |
| 有线网络 | ✅ RTL8111 + RTL8125 |
| Wi-Fi | ✅ AirportItlwm 2.4.0，接口 en2 |
| 蓝牙 | ✅ IntelBluetoothFirmware / IntelBTPatcher / BlueToolFixup |
| 音频 | ✅ AppleALC，layout-id=58 |
| NVMe | ✅ NVMeFix |
| USB | ✅ MyDevicesFake 端口映射 |
| 图形启动菜单 | ✅ OpenCanopy + Acidanthera GoldenGate |
| 自动启动 | ✅ 5 秒超时，Ctrl+Enter 设置默认项 |
| 外接显示器亮度 | ⚠️ 用 MonitorControl / 显示器 OSD |
| 睡眠 / 唤醒 | ⚠️ 未做长期验证 |
| ARM64 应用 | ❌ x86_64 平台无法运行 arm64 macOS 应用 |

## EFI 版本

- OpenCore 1.0.8 RELEASE
- macOS Sequoia 15.6 / Darwin 24.6.0
- SMBIOS：iMacPro1,1
- 启动参数：`-v debug=0x100 keepsyms=1 -NRedDPDelay alcid=58`
- 详细 kext 版本见 [docs/KEXTS.md](docs/KEXTS.md)

## 目录结构

```text
EFI/
  BOOT/BOOTx64.efi
  OC/
    OpenCore.efi
    config.plist
    config-debug.plist
    ACPI/
    Drivers/
    Kexts/
    Resources/
docs/
  Report.json
  HARDWARE.md
  INSTALL.md
  WIFI.md
  TROUBLESHOOTING.md
  KEXTS.md
  CHANGELOG.md
tools/
  MonitorControl.4.4.0.dmg
checksums.txt
```

## 快速使用

1. 准备 GPT + FAT32 U 盘。
2. 把本仓库的 `EFI` 文件夹放到 U 盘根目录。
3. BIOS 关闭 Secure Boot、CSM，打开 Above 4G Decoding，关闭 Resizable BAR。
4. UEFI 启动 U 盘，进入 OpenCore。
5. 安装 macOS Sequoia 15.6 或启动已有系统。

内置硬盘方案：

- 先把 macOS 系统恢复到内置硬盘，或从安装 U 盘安装。
- 再把 `EFI` 文件夹复制到内置硬盘的 ESP 根目录。
- BIOS 选择内置硬盘的 UEFI 启动项。

## 重要：SMBIOS 三码

仓库中的 `EFI/OC/config.plist` 已经清空：

```text
SystemSerialNumber
MLB
SystemUUID
ROM
```

发布到 GitHub 前不要把个人三码写回去。使用者需要自己生成：

- 使用 GenSMBIOS 选择 `iMacPro1,1`
- 生成 Serial / MLB / UUID
- `ROM` 填有线网卡 en0 的 6 字节 MAC
- 填回 `PlatformInfo -> Generic`

没有三码时系统一般仍可启动，但 iMessage、FaceTime、App Store 等服务不要依赖。

## Wi-Fi 说明

本机使用：

- AirportItlwm 2.4.0（Ersiter/Eric-AirportItlwm，Sequoia 构建）
- SSDT-AXPWR.aml
- GPP4 `_PS0/_PS3` 与 `D00C _ADR` 的 DSDT 补丁

这三项缺一不可。只放 AirportItlwm 会出现驱动已加载但没有 `en2` 接口的情况。

正常状态：

```text
Hardware Port: Wi-Fi
Device: en2
```

不需要 HeliPort。

## 外接显示器亮度

外接显示器亮度不一定能由 macOS 直接控制。仓库提供：

```text
tools/MonitorControl.4.4.0.dmg
```

安装后用菜单栏滑块调 DDC/CI 亮度；如果显示器不支持 DDC，使用显示器自己的 OSD。

## ARM64 应用

本机是 AMD x86_64，不能运行 arm64 macOS 应用。Rosetta 只解决 Apple Silicon 运行 x86_64，不能反向运行 ARM。

## 参考与来源

- [htmambo/morefine-S500-Hackintosh](https://github.com/htmambo/morefine-S500-Hackintosh)
- [AfterYuWei/Morefine-S500-Hackintosh](https://github.com/AfterYuWei/Morefine-S500-Hackintosh)
- [acidanthera/OpenCorePkg](https://github.com/acidanthera/OpenCorePkg)
- [acidanthera/Lilu](https://github.com/acidanthera/Lilu)、[VirtualSMC](https://github.com/acidanthera/VirtualSMC)、[AppleALC](https://github.com/acidanthera/AppleALC)
- [ChefKissInc/NootedRed](https://github.com/ChefKissInc/NootedRed)
- [Ersiter/Eric-AirportItlwm](https://github.com/Ersiter/Eric-AirportItlwm)
- [USBToolBox/kext](https://github.com/USBToolBox/kext)
- [Mieze/RTL8111_driver_for_OS_X](https://github.com/Mieze/RTL8111_driver_for_OS_X)、[LucyRTL8125Ethernet](https://github.com/Mieze/LucyRTL8125Ethernet)
- [MonitorControl/MonitorControl](https://github.com/MonitorControl/MonitorControl)
- [Dortania OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/)

各 kext 和二进制保留其原始许可证；仓库只对本文档和配置整理部分使用 MIT。

## 备注

- 仓库不包含 macOS BaseSystem、R-Drive 镜像或商业恢复软件。
- 发布前请再次确认 `config.plist` 没有个人序列号。
- 配置已通过 OpenCore 1.0.8 `ocvalidate` 检查。

