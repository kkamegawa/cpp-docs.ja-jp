---
title: MakeStaticReloggerGroup
description: C++ BUILD Insights SDK MakeStaticReloggerGroup 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 06927af89b16d9de1148e555868dd2022c59b171
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334386"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeStaticReloggerGroup` 関数は、 [Relog](relog.md)などの関数に渡すことができる静的 relogger グループを作成するために使用されます。 Relogger グループのメンバーは、トレース内のすべてのイベントが処理されるまで、左から右に1つずつイベントを受信します。

## <a name="syntax"></a>構文

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>パラメーター

*TReloggerPtrs*\
このパラメーターは常に推測されます。

*reloggers*\
静的 relogger グループに含まれる[irelogger](../other-types/irelogger-class.md)ポインターのパラメーターパック。 これらのポインターは、raw、`std::unique_ptr`、または `std::shared_ptr`にすることができます。 [Ianalyzer](../other-types/ianalyzer-class.md)ポインターも、継承関係のため `IRelogger` ポインターと見なされます。

### <a name="return-value"></a>戻り値

静的 relogger グループ。 戻り値を取得するには、 **auto**キーワードを使用します。

## <a name="remarks"></a>解説

動的な relogger グループとは異なり、静的 relogger グループのメンバーは、コンパイル時に既知である必要があります。 また、静的 relogger グループには、ポリモーフィックな動作を持たない[Irelogger](../other-types/irelogger-class.md)ポインターが含まれています。 静的 relogger グループを使用して Windows イベントトレーシング (ETW) トレースを分析する場合、`IRelogger` インターフェイスへの呼び出しは、常に relogger グループメンバーによって直接指されているオブジェクトに解決されます。 この柔軟性が失われるのは、イベント処理時間が短縮される可能性があるためです。 コンパイル時に relogger グループのメンバーを認識できない場合、または `IRelogger` ポインターにポリモーフィックな動作が必要な場合は、動的 relogger グループの使用を検討してください。 代わりに[MakeDynamicReloggerGroup](make-dynamic-relogger-group.md)を呼び出して、動的 relogger グループを使用できます。

::: moniker-end
