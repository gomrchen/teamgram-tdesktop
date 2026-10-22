# Desktop 客户端技术文档

`teamgram-tdesktop` 基于 Telegram Desktop（CMake + Qt），对接自建 **Teamgram** 服务端。

## 工程结构

| 路径 | 说明 |
|------|------|
| `Telegram/` | 主工程：源码、`configure.sh`、`build/` |
| `Telegram/SourceFiles/` | 应用逻辑与 MTProto |
| `Telegram/SourceFiles/mtproto/` | 网络层（含 Teamgram DC patch） |
| `Telegram/cmake/telegram_options.cmake` | API ID/Hash 默认值 |
| `Telegram/build/version` | 应用版本号 |
| `Telegram/build/prepare/` | 各平台依赖准备脚本 |
| `out/` | configure 后生成的构建输出（勿提交） |
| `docs/building-*.md` | 上游英文分平台编译说明 |

## 关键配置

| 用途 | 文件 / 参数 |
|------|-------------|
| 服务器 IP / 端口 / RSA | `Telegram/SourceFiles/mtproto/mtproto_dc_options.cpp` |
| API ID / Hash | `-D TDESKTOP_API_ID` / `-D TDESKTOP_API_HASH` |
| 版本 | `Telegram/build/version` |
| 关闭自动更新 | `-D DESKTOP_APP_DISABLE_AUTOUPDATE=ON` |
| 默认主 DC | `Telegram/SourceFiles/mtproto/mtp_instance.h` → `kDefaultMainDc = 1` |

## 工具链（参考 upstream）

| 平台 | 要求 |
|------|------|
| macOS | Xcode、CMake、Ninja、Homebrew 依赖（见 `prepare/mac.sh`） |
| Windows | VS 2022、Python 3.10、CMake（见 `prepare/win.bat`） |
| Linux | Docker `tdesktop:centos_env`（见 `prepare/linux.sh`） |

## 编译场景

| 场景 | 文档 |
|------|------|
| 改配置并打包 | [修改配置与打包.md](修改配置与打包.md) |
| 服务端 IP、RSA、API | [服务端对接配置.md](服务端对接配置.md) |
| 分平台环境准备 | [building-mac.md](building-mac.md) 等 |

## 快速命令（macOS 示例）

```bash
cd teamgram-tdesktop/Telegram
./configure.sh -D TDESKTOP_API_ID=xxx -D TDESKTOP_API_HASH=xxx \
  -D DESKTOP_APP_DISABLE_AUTOUPDATE=ON
# 用 Xcode 打开 ../out/Telegram.xcodeproj
```

## 关联文档

| 路径 | 说明 |
|------|------|
| `../teamgram/docs/文档索引.md` | 后端部署与编译 |
| `../teamgram-ios/docs/文档索引.md` | iOS 客户端 |
| `../teamgram-android/docs/文档索引.md` | Android 客户端 |
| `../teamgram.io/enterprise/docs/企业版技术文档.md` | 企业版架构 §17 客户端对齐 |

---

上游 README（英文）：`../README.md`。
