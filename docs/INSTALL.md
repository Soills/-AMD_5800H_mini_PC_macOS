# 安装说明

## 1. BIOS

- Secure Boot：Disabled
- CSM / Legacy Boot：Disabled，仅 UEFI
- Above 4G Decoding：Enabled
- Resizable BAR：Disabled
- UMA Frame Buffer Size：2GB（有则设置）
- XHCI Hand-off：Enabled
- Fast Boot：Disabled
- Serial Port：Disabled（有则关闭）

## 2. U 盘安装 macOS

推荐使用 Apple 官方 Sequoia Recovery：

1. 准备 16GB U 盘，GPT + FAT32。
2. 把 `EFI` 文件夹放到 U 盘根目录。
3. 把 Apple Recovery 的 `com.apple.recovery.boot` 放到 U 盘根目录。
4. BIOS 选择 UEFI 启动 U 盘。
5. OpenCore 菜单选择 `macOS Base System`。
6. 磁盘工具把内置 NVMe 抹成 APFS / GPT。
7. 安装 macOS Sequoia。
8. 安装过程需要联网，建议插网线。

最终 U 盘结构：

```text
EFI/BOOT/BOOTx64.efi
EFI/OC/config.plist
com.apple.recovery.boot/BaseSystem.dmg
com.apple.recovery.boot/BaseSystem.chunklist
```

## 3. 内建硬盘恢复方案

如果使用 R-Drive Image 的 `.rdr` 恢复版：

1. 目标硬盘必须 GPT。
2. 建立 ESP 约 300MB FAT32 和 MSR，剩余空间保持未分配。
3. 用 R-Drive Image 把 `.rdr` 恢复到未分配空间。
4. APFS 分区由镜像恢复产生，不要手动格式化。
5. 把本仓库 `EFI` 文件夹复制到 ESP 根目录。
6. BIOS 选择内置硬盘 UEFI 启动项。

## 4. 首次启动

- 默认有 `-v`，卡住时拍最后十几行。
- 选中 macOS 后按 `Ctrl+Enter` 可设为默认启动项。
- 默认 5 秒超时后自动进入。

