---
title: MakeDynamicAnalyzerGroup
description: C++ BUILD Insights SDK MakeDynamicAnalyzerGroup 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f409d685c6af6514b73cd837d668a962c1a0d01a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334404"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeDynamicAnalyzerGroup` 関数は、dynamic analyzer グループを作成するために使用されます。 アナライザーグループのメンバーは、トレース内のすべてのイベントが分析されるまで、イベントを左から右に1つずつ受け取ります。

## <a name="syntax"></a>構文

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>パラメーター

*アナライザー*の\
Dynamic analyzer グループに含まれる[Ianalyzer](../other-types/ianalyzer-class.md)ポインターのベクター。 これらのポインターは、raw、`std::unique_ptr`、または `std::shared_ptr`にすることができます。

### <a name="return-value"></a>戻り値

動的アナライザーグループ。 戻り値を取得するには、 **auto**キーワードを使用します。

## <a name="remarks"></a>解説

静的アナライザーグループとは異なり、動的アナライザーグループのメンバーはコンパイル時に既知である必要はありません。 アナライザーグループメンバーは、プログラム入力に基づいて実行時に選択することも、コンパイル時に不明な他の値に基づいて選択することもできます。 静的アナライザーグループとは異なり、dynamic analyzer グループ内の[Ianalyzer](../other-types/ianalyzer-class.md)ポインターにはポリモーフィックな動作があり、仮想関数呼び出しは正しくディスパッチされます。 この柔軟性により、イベント処理時間が遅くなる可能性があります。 すべてのアナライザーグループメンバーがコンパイル時に認識され、ポリモーフィックな動作が必要ない場合は、静的なアナライザーグループの使用を検討してください。 静的なアナライザーグループを使用するには、代わりに[MakeStaticAnalyzerGroup](make-static-analyzer-group.md)を呼び出します。

動的アナライザーグループは、静的なアナライザーグループ内にカプセル化できます。 これは、そのアドレスを[MakeStaticAnalyzerGroup](make-static-analyzer-group.md)に渡すことによって行われます。 この手法は、静的アナライザーグループのみを受け入れる[Analyze](analyze.md)などの関数に動的アナライザーグループを渡す場合に使用します。

::: moniker-end
