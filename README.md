# Teamgram Desktop 客户端

基于 [Telegram Desktop](https://github.com/telegramdesktop/tdesktop) 的 Teamgram 自建服桌面端（CMake + Qt）。

**文档** → [docs/文档索引.md](docs/文档索引.md) · 改配置打包 [docs/修改配置与打包.md](docs/修改配置与打包.md)

## 快速开始（macOS）

```bash
# 1. 改服务器 IP（两处）
#    Telegram/SourceFiles/mtproto/mtproto_dc_options.cpp
#    kBuiltInDcs / kBuiltInDcsTest → { 1, "你的IP", 10443 }

# 2. 首次准备依赖（一次性，耗时较长）
./Telegram/build/prepare/mac.sh

# 3. 生成工程
cd Telegram
./configure.sh -D TDESKTOP_API_ID=你的API_ID -D TDESKTOP_API_HASH=你的API_HASH \
  -D DESKTOP_APP_DISABLE_AUTOUPDATE=ON

# 4. Xcode 打开 ../out/Telegram.xcodeproj → Build
```

Windows / Linux 见 [docs/修改配置与打包.md](docs/修改配置与打包.md) 与 [docs/building-win-x64.md](docs/building-win-x64.md)、[docs/building-linux.md](docs/building-linux.md)。

## 合规提醒

1. 在 [my.telegram.org](https://my.telegram.org) 申请自己的 `api_id` / `api_hash`
2. **不要**使用官方 Telegram 名称与 logo 作为你的应用品牌
3. 遵守 GPLv3 + OpenSSL exception 开源义务

## 上游说明

英文原版说明见 [Telegram Desktop 官方仓库](https://github.com/telegramdesktop/tdesktop)。Teamgram 网络与打包细节以 `docs/` 中文文档为准。
