---
title: SYMBOL_NAME_DATA 構造体
description: C++ BUILD Insights SDK SYMBOL_NAME_DATA 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 618e84f198c20aa089dc7e06e1e6c09b96b6d273
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335094"
---
# <a name="symbol_name_data-structure"></a>SYMBOL_NAME_DATA 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`SYMBOL_NAME_DATA` 構造体は、コンパイラのフロントエンドシンボルを記述します。

## <a name="syntax"></a>構文

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `Key` | 記号のキー。 この値は、分析されるトレース内で一意です。 |
| `Name` | 記号の名前。 |

## <a name="remarks"></a>解説

2つの異なるコンパイラフロントエンドパスからのシンボルは、同じ名前でも異なるキーを持つ場合があります。 この場合は、シンボル名を使用して、2つの型が同じであるかどうかを判断します。

::: moniker-end
