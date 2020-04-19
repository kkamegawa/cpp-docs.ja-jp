---
title: 分析
description: C++ BUILD Insights SDK 分析関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 49161641d1cff1c64261d95bb2caace2f802543a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334434"
---
# <a name="analyze"></a>分析

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`Analyze` 関数は、ビルドのC++トレース中に MSVC から取得した WINDOWS イベントトレーシング (ETW) トレースを分析するために使用されます。 ETW トレース内のイベントは、呼び出し元によって提供されるアナライザーグループに順次転送されます。 この関数では、イベントストリームを1行に複数回転送できる、複数パスの分析をサポートしています。

## <a name="syntax"></a>構文

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const char*                                   inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const wchar_t*                                inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>パラメーター

*TAnalyzerGroupMembers*\
このパラメーターは常に推測されます。

*Inputlogfile*\
イベントの読み取り元の入力 ETW トレース。

*numberofpasses*\
入力トレースで実行する分析パスの数。 トレースは、分析パスごとに1回、指定されたアナライザーグループを通じて渡されます。

*analyzerGroup*\
分析に使用するアナライザーグループ。 [MakeStaticAnalyzerGroup](make-static-analyzer-group.md)を呼び出して、analyzer グループを作成します。 [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)から取得した動的アナライザーグループを使用するには、まず、そのアドレスを `MakeStaticAnalyzerGroup`に渡すことによって、静的なアナライザーグループ内にカプセル化します。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md)列挙型の結果コード。

::: moniker-end
