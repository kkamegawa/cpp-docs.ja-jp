---
title: ANALYSIS_DESCRIPTOR 構造体
description: C++ BUILD Insights SDK ANALYSIS_DESCRIPTOR 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fc11ce11e1faaae02edb36aac447c18ea8107e35
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334104"
---
# <a name="analysis_descriptor-structure"></a>ANALYSIS_DESCRIPTOR 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`ANALYSIS_DESCRIPTOR` 構造体は、 [Analyze ea](../functions/analyze-a.md)と[analyze](../functions/analyze-w.md)の新機能で使用されます。 ここでは、Windows イベントトレーシング (ETW) トレースの分析方法について説明します。

## <a name="syntax"></a>構文

```cpp
typedef struct ANALYSIS_DESCRIPTOR_TAG
{
    unsigned                NumberOfPasses;
    ANALYSIS_CALLBACKS      Callbacks;
    void*                   Context;
} ANALYSIS_DESCRIPTOR;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `NumberOfPasses` | ETW トレースで実行される分析パスの数。 |
| `Callbacks` | 分析セッション中に呼び出す関数を指定する[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)オブジェクト。 |
| `Context` | で指定されたすべてのコールバック関数に引数として渡されるユーザー指定のコンテキスト。 `Callbacks` |

## <a name="remarks"></a>解説

`Callbacks` 構造体は、非メンバー関数へのポインターのみを受け入れます。 この制限を回避するには、オブジェクトポインターに `Context` を設定します。 このオブジェクトポインターは、すべての非メンバーコールバック関数に引数として渡されます。 メンバー関数を非メンバーコールバック関数内から呼び出すには、このポインターを使用します。

::: moniker-end
