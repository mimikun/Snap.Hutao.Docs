---
category: [FAQ, 依存, インストール]
icon: iconfont icon-structure
order: 6
comment: false
---

# 依存関係を手動でインストールする

Snap Hutao は依存関係として Windows App Runtime に依存しており、ユーザーのシステムにこの環境がない場合、Windows は Snap Hutao のインストール前にこのフレームワークをインストールします。

![](https://img.alicdn.com/imgextra/i3/1797064093/O1CN01RJFPnY1g6dye2b8Uy_!!1797064093.png_.webp)

ネットワークが貧弱な場合、フレームワークのインストール段階で速度が低下したり、停止したりする可能性があります。 このようなシナリオでは、Microsoft Web サイトからフレームワークをダウンロードし、手動でインストールできます。

1. Microsoft ドキュメント ページにアクセス：[Windows App SDK 用の最新のダウンロード](https://learn.microsoft.com/ja-jp/windows/apps/windows-app-sdk/downloads)
2. 「最新のx64安定版インストーラー(x.y.z)をダウンロードする」をクリックして、オフライン インストーラーをダウンロードします。
3. ダウンロードした Windows アプリ ランタイム インストーラーを実行してから、Snap Hutao をインストールします。
