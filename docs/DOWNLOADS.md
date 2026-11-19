# 系统镜像与工具下载

本仓库不包含 macOS 系统镜像、BaseSystem.dmg、R-Drive 恢复镜像或商业恢复软件。

## macOS Sequoia

### 官方方式

- Apple 官网：https://www.apple.com/macos/macos-sequoia/
- 有 Mac 时可用 App Store 或终端：

```bash
softwareupdate --fetch-full-installer --full-installer-version 15.6
```

### OpenCore Recovery 方式

- macrecovery 工具：https://github.com/acidanthera/OpenCorePkg/tree/master/Utilities/macrecovery

```bash
python3 macrecovery.py -b Mac-7BA5B2D9E42DDD94 -m 00000000000000000 download
```

下载后得到：

```text
com.apple.recovery.boot/BaseSystem.dmg
com.apple.recovery.boot/BaseSystem.chunklist
```

## 恢复版镜像（第三方）

下面页面提供 R-Drive Image 恢复版镜像，仅供有需要的人参考；请自行确认版本、来源和完整性：

- macOS Sequoia 15.6 恢复版页面：https://hpglw.com/macOS-Sequoia-15.6.html

使用恢复版时，系统分区由 .rdr 恢复产生，EFI 仍需放到 ESP。

## 工具

- R-Drive Image 官网：https://www.drive-image.com/
- GenSMBIOS：https://github.com/corpnewt/GenSMBIOS
- MonitorControl：https://github.com/MonitorControl/MonitorControl
- OpenCorePkg：https://github.com/acidanthera/OpenCorePkg/releases

## 注意

- 系统镜像不随仓库分发。
- 恢复版镜像的默认密码、分区方式和授权请以镜像提供方说明为准。

