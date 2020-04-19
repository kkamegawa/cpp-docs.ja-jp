---
title: FUNCTION_DATA 構造体
description: C++ BUILD Insights SDK FUNCTION_DATA 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 718e93bed798786a4596ccb3e724b2b54d4fe79d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335178"
---
# <a name="function_data-structure"></a>FUNCTION_DATA 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`FUNCTION_DATA` 構造体は、関数を記述します。

## <a name="syntax"></a>構文

```cpp
typedef struct FUNCTION_DATA_TAG
{
    const char*         Name;

} FUNCTION_DATA;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `Name` | UTF-8 でエンコードされた関数の名前。 |

::: moniker-end
