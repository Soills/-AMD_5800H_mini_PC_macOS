# Intel AC 8265 Wi-Fi

本机 Wi-Fi 使用：

- `AirportItlwm.kext` 2.4.0（Ersiter/Eric-AirportItlwm 的 Sequoia 构建）
- `SSDT-AXPWR.aml`
- DSDT 中的 GPP4 `_PS0` / `_PS3` 重命名补丁
- DSDT 中 `GPP4.D00C _ADR` FF -> 00 补丁

## 为什么需要 ACPI 电源补丁

MoreFine S500+ 的 Intel Wi-Fi 插槽在 GPP4。只加载 AirportItlwm 时，驱动可以加载，但不会生成 `en2` 接口。加入 GPP4 电源方法后，接口才正常出现。

正常状态：

```text
Hardware Port: Wi-Fi
Device: en2
```

## 不要做的事

- 不要同时启用 `itlwm.kext` 和 `AirportItlwm.kext`。
- 不要套用 Broadcom 的 `IO80211FamilyLegacy` / `AirPortBrcmNIC`。
- 不需要 HeliPort。
- 不要删除 `SSDT-AXPWR.aml` 或三条 GPP4 ACPI 补丁。

