---
title: MakeDynamicReloggerGroup
description: C++ BUILD Insights SDK MakeDynamicReloggerGroup 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4ad394d3ba2982e7ee4f2a497fef2ea65a3c1769
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334398"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeDynamicReloggerGroup` 関数は、動的 relogger グループを作成するために使用されます。 Relogger グループのメンバーは、トレース内のすべてのイベントが処理されるまで、左から右に1つずつイベントを受信します。

## <a name="syntax"></a>構文

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>パラメーター

*reloggers*\
動的 relogger グループに含まれる[Irelogger](../other-types/irelogger-class.md)ポインターのベクター。 これらのポインターは、raw、`std::unique_ptr`、または `std::shared_ptr`にすることができます。 [Ianalyzer](../other-types/ianalyzer-class.md)ポインターも、継承関係のため `IRelogger` ポインターと見なされます。

### <a name="return-value"></a>戻り値

動的な relogger グループ。 戻り値を取得するには、 **auto**キーワードを使用します。

## <a name="remarks"></a>解説

静的 relogger グループとは異なり、動的 relogger グループのメンバーはコンパイル時に既知である必要はありません。 実行時には、プログラムの入力に基づいて、またはコンパイル時に不明なその他の値に基づいて、再ロガーグループメンバーを選択できます。 静的 relogger グループとは異なり、動的 relogger グループ内の[irelogger](../other-types/irelogger-class.md)ポインターにはポリモーフィックな動作があり、仮想関数呼び出しは正しくディスパッチされます。 この柔軟性により、イベント処理時間が遅くなる可能性があります。 すべての relogger グループメンバーがコンパイル時に認識され、ポリモーフィックな動作が必要ない場合は、静的 relogger グループの使用を検討してください。 静的 relogger グループを使用するには、代わりに[MakeStaticReloggerGroup](make-static-relogger-group.md)を呼び出します。

動的 relogger グループは、静的 relogger グループ内にカプセル化できます。 そのアドレスを[MakeStaticReloggerGroup](make-static-relogger-group.md)に渡します。 この手法は、静的 relogger グループのみを受け入れる、 [Relog](relog.md)などの関数に動的 relogger グループを渡す場合に使用します。

::: moniker-end
