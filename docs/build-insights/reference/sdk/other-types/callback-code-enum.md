---
title: CALLBACK_CODE 列挙型
description: C++ビルドインサイト SDK CALLBACK_CODE 列挙型参照です。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 68eaa9aa04d2f0a55ac12fb7dde14a080188a38d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334092"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE 列挙型

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`CALLBACK_CODE` 列挙型は、分析または再ログセッションのフローを制御するために使用されます。 [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)または[RELOG_CALLBACKS](relog-callbacks-struct.md)内の関数から CALLBACK_CODE 値を返して、次に発生する処理を制御します。

## <a name="members"></a>メンバー

| Name | 値 | Description |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | 現在の分析を続行するか、セッションを再ログに記録します。 |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | 現在の分析をキャンセルするか、セッションを再ログに記録して、エラーを通知します。 |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | 現在の分析をキャンセルするか、セッションを再ログに記録します。 |

::: moniker-end
