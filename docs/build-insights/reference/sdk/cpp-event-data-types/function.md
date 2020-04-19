---
title: Function クラス
description: C++ビルドインサイト SDK 関数クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3ff66119007ed7172fed7e824287ab8617c70973
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334770"
---
# <a name="function-class"></a>Function クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`Function` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [関数](../event-table.md#function)のイベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class Function : public Activity
{
public:
    Function(const RawEvent& event);

    const char* Name() const;
};
```

## <a name="members"></a>メンバー

[アクティビティ](activity.md)基本クラスから継承されたメンバーと共に、`Function` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[Function](#function)

### <a name="functions"></a>関数

[名前](#name)

## <a name="function"></a>プロシージャ

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[関数](../event-table.md#function)イベント。

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>戻り値

UTF-8 でエンコードされた関数の名前。

::: moniker-end
