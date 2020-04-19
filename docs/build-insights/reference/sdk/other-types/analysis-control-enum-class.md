---
title: AnalysisControl enum クラス
description: ビルドC++インサイト SDK AnalysisControl 列挙型の参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cf162c11e0a7109b8d733dab79df80782398e14d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334122"
---
# <a name="analysiscontrol-enum-class"></a>AnalysisControl enum クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`AnalysisControl` 列挙型クラスは、分析または再ログセッションのフローを制御するために使用されます。 [Ianalyzer](ianalyzer-class.md)メンバー関数または[irelogger](irelogger-class.md)メンバー関数から `AnalysisControl` コードを返して、次に何が行われるかを制御します。

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `BLOCK` | 現在のイベントが analyzer または relogger グループにさらに反映されないようにします。 |
| `CANCEL` | 現在の分析をキャンセルするか、セッションを再ログに記録します。 |
| `CONTINUE` | 現在の分析を続行するか、セッションを再ログに記録します。 現在のイベントを次のアナライザーまたは relogger グループメンバーに伝達します。 |
| `FAILURE` | 現在の分析をキャンセルするか、セッションを再ログに記録して、エラーを通知します。 |

::: moniker-end
