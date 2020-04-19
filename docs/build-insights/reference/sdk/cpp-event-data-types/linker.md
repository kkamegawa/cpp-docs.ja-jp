---
title: リンカークラス
description: C++ビルドインサイト SDK リンカークラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Linker
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bb8948d7772046e18d5db5002deed48d0dd88375
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334710"
---
# <a name="linker-class"></a>リンカークラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`Linker` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [リンカー](../event-table.md#linker)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class Linker : public Invocation
{
public:
    Linker(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

`Linker` クラスには、[呼び出し](invocation.md)元の基底クラスから継承されたメンバーと共に、次のメンバーが含まれています。

### <a name="constructors"></a>コンストラクター

[リンカー](#linker)

## <a name="linker"></a>リンカ

```cpp
Linker(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[リンカー](../event-table.md#linker)イベント。

::: moniker-end
