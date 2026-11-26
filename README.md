# Surge 共享模块

这个仓库维护 Apple Intelligence、抖音直连和金融服务模块。Apple Intelligence 和抖音直连供 iPhone 与 Mac 使用，金融服务供 iPhone 使用。

## Apple Intelligence & English Siri

文件：`AppleIntelligence.sgmodule`

它把英文 Siri、Apple Intelligence、Private Cloud Compute、OHTTP 中继和照片高质量消除需要的域名送到同一个代理策略。

安装时只声明一个参数 `Policy`。默认值是 `TW-UrlTest`，也就是你现在使用的手动选择组。这个组需要支持 TCP 和 UDP/QUIC。如果 PCC 或照片消除持续报错，建议改成一个固定的节点，避免会话中途更换出口 IP。

模块不包含 MITM，也不需要安装证书。

## 抖音 / 字节跳动直连

文件：`Douyin-Direct.sgmodule`

它把抖音、豆包、西瓜视频、今日头条和常见的字节跳动域名固定为 `DIRECT`。主配置里不再需要 `DouYin` 策略组和 `DouYin.list`。

## 金融服务 · 美国（GitHub 版）

iPhone 使用 `Finance-US.sgmodule`。Bybit 走土耳其固定节点，`okx.com` 和 `okex.com` 走 `US`，其余收录的 OKX 域名走 `Proxies`。

在 iPhone 的 Surge 中启用 GitHub 版后，即可移除旧的本地模块。

## 安装

在 iPhone 或 Mac 上直接点下面的链接：

- [安装 Apple Intelligence & English Siri](surge:///install-module?url=https%3A%2F%2Fraw.githubusercontent.com%2Fsummer87279149%2Fsurge-shared-modules%2Fmain%2FAppleIntelligence.sgmodule)
- [安装抖音 / 字节跳动直连](surge:///install-module?url=https%3A%2F%2Fraw.githubusercontent.com%2Fsummer87279149%2Fsurge-shared-modules%2Fmain%2FDouyin-Direct.sgmodule)

- [在 iPhone 安装金融服务 · 美国](surge:///install-module?url=https%3A%2F%2Fraw.githubusercontent.com%2Fsummer87279149%2Fsurge-shared-modules%2Fmain%2FFinance-US.sgmodule)

也可以在 Surge 的模块页面里选择从 URL 安装：

```text
https://raw.githubusercontent.com/summer87279149/surge-shared-modules/main/AppleIntelligence.sgmodule
https://raw.githubusercontent.com/summer87279149/surge-shared-modules/main/Douyin-Direct.sgmodule
https://raw.githubusercontent.com/summer87279149/surge-shared-modules/main/Finance-US.sgmodule
```

## 注意事项

普通 Apple 流量仍由主配置里的 `Apple_All.list` 处理。Apple Intelligence 模块要在它之前匹配，否则 `apple.com` 的宽泛规则会先命中。

这个仓库只放模块。不要提交 Surge 配置、节点密码、Surge CA 证书或私钥。
