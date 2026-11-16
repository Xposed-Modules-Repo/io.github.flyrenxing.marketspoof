# 小米应用商店伪装

LSPosed 模块。只在小米应用商店（`com.xiaomi.market`）进程内，把机型伪装成 **Xiaomi / madrid / 2611FPNFAG**（小米 18 Pro Max）。

它**不会**修改全局 `getprop`。其他应用仍然看到真实机型。

## 解决什么问题

小米应用商店会按机型控制下载管理器是否限速。部分机型打开商店后下载会明显变慢。

本模块只改商店进程里的 `Build` 字段和 `ro.product.*` 系统属性，让商店把自己当成小米 18 Pro Max，从而避开按型号下发的下载限速策略。

- 只作用于 `com.xiaomi.market`
- 不改系统全局机型，不影响其他应用
- 不改指纹、不改 MIUI 版本号
- 不碰商店服务端，也不改下载协议

## 环境要求

- 支持现代 Xposed API 102 的 LSPosed（Zygisk / KernelSU）
- Android 8.0+
- 推荐作用域只勾选 `com.xiaomi.market`

## 安装

1. 从本仓库 Release 安装 APK，或从 [源码仓库 Latest](https://github.com/FlyRenxing/xiaomi-market-spoof/releases/latest) 下载。
2. 打开 LSPosed，启用 **小米应用商店伪装**。
3. 作用域保持为 `com.xiaomi.market`。
4. 强行停止小米应用商店，再打开商店重新下载。

启用后如果限速还在，先强停商店再试；本机若还有其他模块也勾了商店，可先关掉对比。

## 伪装目标

| 项目 | 值 |
| --- | --- |
| 厂商 / 品牌 | `Xiaomi` |
| 设备代号 / 产品名 | `madrid` |
| 型号 | `2611FPNFAG` |

## 源码

https://github.com/FlyRenxing/xiaomi-market-spoof

## 声明

这是个人开源的本机辅助模块，用来处理小米应用商店按机型限制下载管理器速度的问题。它不是小米官方产品。请只在自己的设备上使用。不要用来冒充他人、绕过付费，或攻击商店基础设施。

## 许可证

Apache License 2.0
