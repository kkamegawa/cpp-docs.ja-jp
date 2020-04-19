---
title: LibOutput クラス
description: C++ビルドインサイト SDK liboutput クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9ec0d8de5302d9893aedd28661b2234150e82e08
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334734"
---
# <a name="liboutput-class"></a>LibOutput クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`LibOutput` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [LIB_OUTPUT](../event-table.md#lib-output)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class LibOutput : public FileOutput
{
public:
    LibOutput(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

[Fileoutput](file-output.md)基本クラスから継承されたメンバーと共に、`LibOutput` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[LibOutput](#lib-output)

## <a name="lib-output"></a>LibOutput

```cpp
LibOutput(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[LIB_OUTPUT](../event-table.md#lib-output)イベントです。

::: moniker-end
