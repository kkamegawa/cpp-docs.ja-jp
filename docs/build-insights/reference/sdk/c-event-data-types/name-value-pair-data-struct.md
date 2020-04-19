---
title: NAME_VALUE_PAIR_DATA 構造体
description: C++ BUILD Insights SDK NAME_VALUE_PAIR_DATA 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- NAME_VALUE_PAIR_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f6c4f6fef11e6365bdc930d5df1f48f72186ebdb
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335100"
---
# <a name="name_value_pair_data-structure"></a>NAME_VALUE_PAIR_DATA 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`NAME_VALUE_PAIR_DATA` 構造体は、名前と値のペアを記述します。

## <a name="syntax"></a>構文

```cpp
typedef struct NAME_VALUE_PAIR_DATA_TAG
{
    const wchar_t*      Name;
    const wchar_t*      Value;
} NAME_VALUE_PAIR_DATA;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `Name` | 名前です。 |
| `Value` | 値。 |

::: moniker-end
