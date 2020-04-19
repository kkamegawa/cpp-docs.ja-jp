---
title: ObjOutput クラス
description: C++ビルドインサイト SDK objoutput クラス参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ObjOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 26cf110bcd086ab051174ebf0017a73370c0aa5e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334662"
---
# <a name="objoutput-class"></a>ObjOutput クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`ObjOutput` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [OBJ_OUTPUT](../event-table.md#obj-output)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class ObjOutput : public FileOutput
{
public:
    ObjOutput(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

[Fileoutput](file-output.md)基本クラスから継承されたメンバーと共に、`ObjOutput` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[ObjOutput](#obj-output)

## <a name="obj-output"></a>ObjOutput

```cpp
ObjOutput(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[OBJ_OUTPUT](../event-table.md#obj-output)イベントです。

::: moniker-end
