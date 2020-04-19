---
title: ExecutableImageOutput クラス
description: C++ビルドインサイト SDK ExecutableImageOutput クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ExecutableImageOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5a2e417a7dd976f257b4dd5a3aabfdf440c604fc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334878"
---
# <a name="executableimageoutput-class"></a>ExecutableImageOutput クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`ExecutableImageOutput` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class ExecutableImageOutput : public FileOutput
{
public:
    ExecutableImageOutput(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

[Fileoutput](file-output.md)基本クラスから継承されたメンバーと共に、`ExecutableImageOutput` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[ExecutableImageOutput](#executable-image-output)

## <a name="executable-image-output"></a>ExecutableImageOutput

```cpp
ExecutableImageOutput(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output)イベントです。

::: moniker-end
