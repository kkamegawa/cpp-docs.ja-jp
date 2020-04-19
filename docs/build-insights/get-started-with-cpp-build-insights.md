---
title: C++ Build Insights を使ってみる
description: ビルド洞察のC++概要を説明します。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a5799fecc885b96f4278e0f5077662ce5fd7c8f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332008"
---
# <a name="get-started-with-c-build-insights"></a>C++ Build Insights を使ってみる

::: moniker range="<=vs-2017"

Visual C++ Studio 2019 では、Build Insights ツールを使用できます。 そのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range="vs-2019"

C++Build Insights は、Microsoft Visual C++ (MSVC) ツールチェーンの可視性を向上させるツールのコレクションです。 これらのツールは、 C++ビルドに関するデータを収集し、次のような一般的な質問に回答するのに役立つ形式で提示します。

- ビルドは十分に並列化されていますか。
- プリコンパイル済みヘッダー (PCH) には何を含める必要がありますか。
- ビルドの速度を向上させるために、特に注目する必要のあるボトルネックはありますか。

このテクノロジの主要なコンポーネントは次のとおりです。

- *vcperf .exe。* ビルドのトレースを収集するために使用できるコマンドラインユーティリティです。
- WPA でビルドトレースを表示できるようにする Windows パフォーマンスアナライザー (WPA) 拡張機能
- C++ BUILD insights SDK。ビルドインサイトデータを使用C++する独自のツールを作成するためのソフトウェア開発キットです。

これらのコンポーネントの使用をすぐに開始するには、以下のリンクをクリックしてください。

[チュートリアル: vcperf および Windows パフォーマンスアナライザーの](tutorials/vcperf-and-wpa.md)\
C++プロジェクトのビルドトレースを収集する方法と、それらを WPA で表示する方法について説明します。

[チュートリアル: Windows パフォーマンスの基本](tutorials/wpa-basics.md)\
ビルドトレースの分析に役立つ WPA のヒントを紹介します。

Build Insights SDK\ [ C++ ](reference/sdk/overview.md)
C++ BUILD Insights SDK の概要。

::: moniker-end
