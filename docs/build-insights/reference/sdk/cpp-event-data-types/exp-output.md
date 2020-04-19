---
title: 出力クラス
description: Build C++ Insights SDK の出力クラスの参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ExpOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bc108096bf2fffba876231bbf522295d0d0dcc0d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334854"
---
# <a name="expoutput-class"></a>出力クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`ExpOutput` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [EXP_OUTPUT](../event-table.md#exp-output)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class ExpOutput : public FileOutput
{
public:
    ExpOutput(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

[Fileoutput](file-output.md)基本クラスから継承されたメンバーと共に、`ExpOutput` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[出力の出力](#exp-output)

## <a name="exp-output"></a>出力の出力

```cpp
ExpOutput(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[EXP_OUTPUT](../event-table.md#exp-output)イベントです。

::: moniker-end
