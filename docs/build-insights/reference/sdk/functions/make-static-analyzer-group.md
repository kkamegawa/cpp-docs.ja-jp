---
title: MakeStaticAnalyzerGroup
description: C++ BUILD Insights SDK MakeStaticAnalyzerGroup 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5eabb0fcbb0a0bb0eea0f4e6bbf27b8e4c53c3ab
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334392"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeStaticAnalyzerGroup` 関数は、 [Analyze](analyze.md)や[Relog](relog.md)などの関数に渡すことができる静的なアナライザーグループを作成するために使用されます。 アナライザーグループのメンバーは、トレース内のすべてのイベントが分析されるまで、イベントを左から右に1つずつ受け取ります。

## <a name="syntax"></a>構文

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>パラメーター

*TAnalyzerPtrs*\
このパラメーターは常に推測されます。

*アナライザー*の\
静的アナライザーグループに含まれる[Ianalyzer](../other-types/ianalyzer-class.md)ポインターのパラメーターパック。 これらのポインターは、raw、`std::unique_ptr`、または `std::shared_ptr`にすることができます。

### <a name="return-value"></a>戻り値

静的なアナライザーグループ。 戻り値を取得するには、 **auto**キーワードを使用します。

## <a name="remarks"></a>解説

動的アナライザーグループとは異なり、静的なアナライザーグループのメンバーはコンパイル時に既知である必要があります。 また、静的なアナライザーグループには、ポリモーフィックな動作を持たない[Ianalyzer](../other-types/ianalyzer-class.md)ポインターが含まれています。 静的なアナライザーグループを使用して Windows イベントトレーシング (ETW) トレースを分析する場合、`IAnalyzer` インターフェイスへの呼び出しは、常に analyzer グループメンバーによって直接指されているオブジェクトに解決されます。 この柔軟性が失われるのは、イベント処理時間が短縮される可能性があるためです。 コンパイル時に analyzer グループのメンバーを認識できない場合、または `IAnalyzer` ポインターにポリモーフィックな動作が必要な場合は、dynamic analyzer グループの使用を検討してください。 動的アナライザーグループを使用するには、代わりに[MakeDynamicAnalyzerGroup](make-static-analyzer-group.md)を呼び出します。

::: moniker-end
