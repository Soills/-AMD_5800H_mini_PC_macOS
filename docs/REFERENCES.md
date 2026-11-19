# 参考项目与 GitHub

本仓库的 EFI、ACPI、USB 映射和配置参考了以下项目。

## 同机型/近似机型

- https://github.com/htmambo/morefine-S500-Hackintosh
  - MoreFine S500+ AMD R9-5900HX、RTL8111+RTL8125、ALC269
  - ACPI 和 USB 映射的重要参考
- https://github.com/AfterYuWei/Morefine-S500-Hackintosh
  - MoreFine S500+ macOS Tahoe EFI
  - GPP4 Wi-Fi 电源处理、SSDT-AXPWR 和 DSDT 补丁参考
- https://github.com/daliansky/morefine-S500-Hackintosh
  - 注意：这是 Intel i9-10880H 版本，不适用于本机 AMD 平台，仅作资料参考

## OpenCore / 基础 Kext

- https://github.com/acidanthera/OpenCorePkg
- https://github.com/acidanthera/Lilu
- https://github.com/acidanthera/VirtualSMC
- https://github.com/acidanthera/AppleALC
- https://github.com/acidanthera/NVMeFix
- https://github.com/acidanthera/RestrictEvents
- https://github.com/acidanthera/BrcmPatchRAM

## AMD CPU / GPU

- https://github.com/AMD-OSX/AMD_Vanilla
  - AMD CPU 内核补丁
- https://github.com/ChefKissInc/NootedRed
  - Cezanne/Renoir/Raven 核显
- https://github.com/trulyspinach/SMCAMDProcessor
  - AMDRyzenCPUPowerManagement / SMCAMDProcessor

## Wi-Fi / 蓝牙

- https://github.com/Ersiter/Eric-AirportItlwm
  - 本仓库使用的 Sequoia AirportItlwm 2.4.0 来源
- https://github.com/OpenIntelWireless/itlwm
  - Intel Wi-Fi 项目上游
- https://github.com/OpenIntelWireless/IntelBluetoothFirmware
  - Intel 蓝牙固件和补丁

## 有线网卡 / USB

- https://github.com/Mieze/RTL8111_driver_for_OS_X
- https://github.com/Mieze/LucyRTL8125Ethernet
- https://github.com/USBToolBox/kext

## 资源与其他

- https://github.com/acidanthera/OcBinaryData
  - OpenCanopy 的 Font / Image / Label 资源
- https://github.com/MonitorControl/MonitorControl
  - 外接显示器 DDC/CI 亮度控制
- https://github.com/corpnewt/GenSMBIOS
  - 生成 SMBIOS 三码
- https://github.com/dortania/OpenCore-Install-Guide
  - OpenCore 安装和排错指南
- https://github.com/dortania/Getting-Started-With-ACPI
  - ACPI / SSDT 参考资料
