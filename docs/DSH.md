# 可选：在本机安装 DeepSeek Harness (dsh)

本机是 AMD x86_64，不能运行 ARM64 桌面版。下面记录已验证的 x86_64 CLI + Web UI 方案。

## 安装 Node.js x86_64

官方 DSH 当前要求 Node.js >= 24.9.0。已验证版本：Node.js 26.13.1 darwin-x64。

## 安装 dsh

```bash
sudo npm install -g --prefix /usr/local @deepseek-ai/dsh
dsh --version
```

## 启动

```bash
dsh web
```

默认 Web UI：`http://127.0.0.1:3080`。

## 本机快捷方式

- `/Applications/DeepSeek Harness.app`
- `/Users/<user>/Desktop/DeepSeek Harness.app`
- `/usr/local/bin/dsh-web-launcher`

启动日志：`~/Library/Logs/DeepSeekHarness.log`。

DSH 是官方 developer preview，API Key 和模型配置请在 Web UI 里填写。

