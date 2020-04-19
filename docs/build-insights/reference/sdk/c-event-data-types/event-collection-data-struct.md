---
title: EVENT_COLLECTION_DATA 構造体
description: C++ BUILD Insights SDK EVENT_COLLECTION_DATA 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1a622a8459b6aa6d9dcbe0faaf90ae545b449466
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335244"
---
# <a name="event_collection_data-structure"></a>EVENT_COLLECTION_DATA 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`EVENT_COLLECTION_DATA` 構造体は、 [EVENT_DATA](event-data-struct.md)要素の配列を記述します。

## <a name="syntax"></a>構文

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `Count` | 配列内の `EVENT_DATA` 要素の数。 |
| `Elements` | 配列内の最初の `EVENT_DATA` 要素へのポインター。 |

::: moniker-end
