# Diplay Geely · 吉利星越L 2025款揽星 CarPlay 投屏适配

[English](README.en.md) · **简体中文** · [繁體中文](README.zh-TW.md)

✔ **星越L 25款揽星 · KX11 实车验证** · v0.2.22.5 · GPL-3.0 开源 · 免越狱 · 免改装

把有线 / 无线 CarPlay 带进吉利星越L（KX11）车机：方向盘按键直控、车速续航温度实时显示、导航投进仪表 HUD。

**在线网站**：[tianwenbro.github.io/DiPlay-GeeLy](https://tianwenbro.github.io/DiPlay-GeeLy/) · **下载**：[Releases](https://github.com/tianwenbro/DiPlay-GeeLy/releases/latest) · **问题反馈**：[Issues](https://github.com/tianwenbro/DiPlay-GeeLy/issues/new/choose)

![DiPlay home](site/assets/home.png)

## 01 安装到星越L（三步上车）

1. **下载并安装两个 APK**：点击下方下载链接，或到 [Releases](https://github.com/tianwenbro/DiPlay-GeeLy/releases) 页；用 **U 盘**或 `adb install` 装进车机（车机浏览器无法安装）。**先装车桥，再装主应用，两包必须配套安装、缺一不可**——车桥负责读取车速 / 续航 / 温度等车况，只装主应用会缺车况数据，只装车桥无法投屏。
2. **配置车辆**：打开主应用，授予蓝牙 / 位置 / 麦克风权限；先在**设置 → 关于**连点版本号 7 次解锁开发者选项，再进入**设置 → 左侧「车辆」→ 车辆属性 → 车型属性配置**，选择车辆 **星越 L · KX11（25 揽星）**并**保存配置**；进入**「车辆扫描」**页点**右上角设置**，车桥连接状态显示 READY 即正常。
3. **连接 iPhone**：USB 数据线连接即插即用（首次 USB 连接前需按下方说明用 ADB 放行一次 VPN）。普通安卓会弹「VPN 连接请求」，星越L（OneOS 车机）通常不弹这个框；无线方式先连车机内置热点，完成一次蓝牙配对，再按设置里的连接引导操作，**无线连接无需 ADB 授权**。

> ⚠ **星越L 用 USB 连接 CarPlay 必做：先用 ADB 放行 VPN（否则 USB 连不上 CarPlay）。**此操作**仅 USB 连接需要**，蓝牙/无线连接不需要这一步。首次 USB 连接之前，车机连电脑开启 ADB 调试并执行：
>
> ```
> adb shell appops set com.shihab.diplay ACTIVATE_VPN allow
> ```
>
> 如果用的是 ATV Tools 等**无线 ADB**（手机连车机），在其终端里执行（无需 adb shell 前缀）：`appops set com.shihab.diplay ACTIVATE_VPN allow`
>
> 执行一次即可长期生效。应用内连接帮助页也会显示这条命令，车桥若有车机 ADB 权限也会尝试自动授权；换装不同包名的版本后需对新包名再执行一次。

> **装过其他 DiPlay / 车桥？请先卸载再装。**本仓库主应用与上游原版 DiPlay 等改编版共用包名（`com.shihab.diplay`），签名不同，未卸载旧版会提示「应用未安装」；即使包名不同、能并存的其他版本，也会抢占 USB / 音频 / 无线连接导致冲突。卸载方法：车机「设置 → 应用管理」找到旧版逐个卸载，或用 `adb uninstall com.shihab.diplay` / `adb uninstall com.geely.desktop.vehicle.bridge`（其他版本以实际包名为准）。卸载会清除旧版配置，装好后按上面步骤重新配置一次即可；本仓库自己的版本之间可直接覆盖升级（签名一致）。

📘 **详细安装请看这里**：方控按键、车况数据与 HUD 投屏在连接成功后自动生效；完整图文教程（含排障表）见 **[吉利安装说明（简体中文）](docs/GEELY-INSTALL.zh-CN.md)**。

## 02 下载与更新

| 文件 | 说明 |
|---|---|
| [Diplay-Geely-25-XingYue-L-v0.2.22.5.apk](https://github.com/tianwenbro/DiPlay-GeeLy/releases/download/v0.2.22.5/Diplay-Geely-25-XingYue-L-v0.2.22.5.apk) | 主应用（CarPlay 投屏） |
| [Geely-25-XingYue-L-Vehicle-Bridge-v0.2.22.5.apk](https://github.com/tianwenbro/DiPlay-GeeLy/releases/download/v0.2.22.5/Geely-25-XingYue-L-Vehicle-Bridge-v0.2.22.5.apk) | 车辆数据车桥（只读车速 / 续航 / 温度） |
| [SHA256SUMS.txt](https://github.com/tianwenbro/DiPlay-GeeLy/releases/download/v0.2.22.5/SHA256SUMS.txt) | 发布包校验和 |

升级直接覆盖安装即可保留配置（两包签名一致），**请勿卸载重装**（会丢配置）。历史版本与校验文件见 [Releases](https://github.com/tianwenbro/DiPlay-GeeLy/releases)。

## 03 适用范围

- 本项目面向**吉利星越L 2025 款 揽星**（车机 KX11_A2 · ECARX / OneOS · Android 11），已在实车完成安装与验证。
- 其他吉利 / ECARX 车机可以尝试安装，但未做完整验证；**非吉利车型请使用[上游原版 DiPlay](https://github.com/shihabal3amri/DiPlay)**。

## 免责声明

本项目为非官方第三方项目，与吉利汽车、亿咖通（ECARX）、苹果（Apple）无关联、未获其官方认可或授权。CarPlay 是 Apple Inc. 的商标。向车机侧载第三方应用可能影响车机稳定性、OTA 与整车质保，请自行评估。**请停车操作，行车安全第一**；应用显示的信息仅供参考，以车辆仪表与交通信号为准。软件按「现状」提供，不附带任何担保。

## 文档

吉利适配文档（简体中文）：

- [吉利安装说明（简体中文）](docs/GEELY-INSTALL.zh-CN.md) — 详细图文教程，含 KX11 可读字段与排障表
- [参与贡献](CONTRIBUTING.md)

通用文档（继承自上游，英文，面向上游通用场景、含比亚迪车型内容）：

- [安装与连接](docs/INSTALL.md) · [兼容性与排障](docs/COMPATIBILITY.md) · [隐私说明](docs/PRIVACY.md) · [从源码构建](docs/BUILD.md) · [第三方声明](docs/THIRD_PARTY_NOTICES.md) · [发布记录](CHANGELOG.md)

## 来源与致谢

本项目基于 [shihabal3amri/DiPlay](https://github.com/shihabal3amri/DiPlay)（GPL-3.0），其上游源于 [xcertplay](https://github.com/shilapi/xcertplay)；主界面/设置与网站改编自 [DiAuto](https://github.com/shihabal3amri/DiAuto)（AGPL-3.0，许可见 `docs/licenses`）。

来源声明：吉利适配中的 `vehicle-probe` 模块、车辆地图投屏与吉利方控支持（`common`）、ECARX 热点读取与音频协调（`shared`）及方向盘配置服务端，代码取自 [carlito12345/DiPlay](https://github.com/carlito12345/DiPlay) fork（GPL-3.0，同样基于 shihabal3amri/DiPlay），源码中的 `carlito |` 注释与车辆 profile 作者标记按许可要求予以保留。单独安装的 `vehicle-bridge` APK 为独立实现，不含该 fork 代码。

吉利相关新增：ECARX 原厂热点处理、吉利方向盘按键映射与按键识别、HUD／仪表导航投屏及可编辑布局、全屏地图投至仪表、吉利音频路由，以及用于读取原厂车辆属性的 `vehicle-probe` 桥接。

## 构建

- 版本号统一来自 [gradle.properties](gradle.properties) 的 `GEELY_VERSION_NAME`，主应用与车桥共用。
- 产物：`Diplay-Geely-25-XingYue-L-v<版本>.apk`（debug 为 `…-hud-test.apk`）与 `Geely-25-XingYue-L-Vehicle-Bridge-v<版本>.apk`。
- CarPlay 配件身份文件（`offline-mfi/identity.pk8`、`certificate.p7b`）与 release 签名密钥**不在仓库内**，需要本地自备；普通源码 / CI 构建默认不配置身份。构建细节见 [BUILD.md](docs/BUILD.md)。
- 同步上游：`git fetch upstream && git merge upstream/main`。

本项目仍非 Apple 认证产品，APK 内置从公开 Carlinkit 固件提取的实验性配件身份，详见[第三方声明](docs/THIRD_PARTY_NOTICES.md)。
