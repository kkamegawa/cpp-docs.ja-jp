---
title: WholeProgramAnalysis クラス
description: C++ BUILD Insights SDK WholeProgramAnalysis クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- WholeProgramAnalysis
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6b8e41242acb9e902b250bab960b1c2042dd981a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334494"
---
# <a name="wholeprogramanalysis-class"></a>WholeProgramAnalysis クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`WholeProgramAnalysis` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class WholeProgramAnalysis : public Activity
{
public:
    WholeProgramAnalysis(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

[アクティビティ](activity.md)基本クラスから継承されたメンバーと共に、`WholeProgramAnalysis` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[WholeProgramAnalysis](#whole-program-analysis)

## <a name="whole-program-analysis"></a>WholeProgramAnalysis

```cpp
WholeProgramAnalysis(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis)イベントです。

::: moniker-end
