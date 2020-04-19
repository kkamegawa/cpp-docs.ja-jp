---
title: FRONT_END_FILE_DATA 構造体
description: C++ BUILD Insights SDK FRONT_END_FILE_DATA 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FRONT_END_FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 33232a0f83566e58e64964e84961a7ade2de7b7c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335184"
---
# <a name="front_end_file_data-structure"></a>FRONT_END_FILE_DATA 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`FRONT_END_FILE_DATA` 構造体は、コンパイラのフロントエンドによるファイルの処理を記述します。

## <a name="syntax"></a>構文

```cpp
typedef struct FRONT_END_FILE_DATA_TAG
{
    const char*         Path;

} FRONT_END_FILE_DATA;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `Path` | UTF-8 でエンコードされたファイルの絶対パス。 |

::: moniker-end
