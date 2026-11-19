# Kext 版本与来源

| Kext | 版本 | 作用 / 来源 |
| --- | --- | --- |
| Lilu.kext | 1.7.2 | 补丁框架 / acidanthera |
| VirtualSMC.kext | 1.3.8 | SMC 模拟 / acidanthera |
| AppleMCEReporterDisabler.kext | 1.2 | 禁用 AppleMCEReporter |
| RestrictEvents.kext | 1.1.6 | CPU 名称 / 事件处理 / acidanthera |
| AMDRyzenCPUPowerManagement.kext | 0.7.2 | AMD CPU 电源管理 / trulyspinach |
| SMCAMDProcessor.kext | 1.0.1 | AMD CPU SMC 传感器 |
| NootedRed.kext | 0.8.10 | Cezanne 核显 / ChefKiss |
| AppleALC.kext | 1.9.8 | 音频 / acidanthera |
| MyDevicesFake.kext | 1.3.12 | USB 端口映射 / 设备注入 |
| NVMeFix.kext | 1.1.3 | NVMe 电源管理 / acidanthera |
| IntelBluetoothFirmware.kext | 2.4.0 | Intel 蓝牙固件 |
| IntelBTPatcher.kext | 2.4.0 | Intel 蓝牙补丁 |
| BlueToolFixup.kext | 2.7.2 | 蓝牙框架修复 / acidanthera |
| RealtekRTL8111.kext | 2.4.2 | RTL8111 有线网卡 / Mieze |
| LucyRTL8125Ethernet.kext | 1.2.2 | RTL8125 有线网卡 / Mieze |
| AirportItlwm.kext | 2.4.0 | Intel Wi-Fi 原生接口 / Ersiter 2.4.0 |

## 加载顺序

1. Lilu
2. VirtualSMC
3. AppleMCEReporterDisabler
4. RestrictEvents
5. AMDRyzenCPUPowerManagement
6. SMCAMDProcessor
7. NootedRed
8. AppleALC
9. MyDevicesFake
10. NVMeFix
11. IntelBluetoothFirmware
12. IntelBTPatcher
13. BlueToolFixup
14. RealtekRTL8111
15. LucyRTL8125Ethernet
16. AirportItlwm

