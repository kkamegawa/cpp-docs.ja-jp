---
title: EnvironmentVariable クラス
description: C++ BUILD Insights SDK EnvironmentVariable クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 19e9278e76fb2116dac30a0e790fba86c6c56484
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334926"
---
# <a name="environmentvariable-class"></a>EnvironmentVariable クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`EnvironmentVariable` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class EnvironmentVariable : public SimpleEvent
{
public:
    EnvironmentVariable(const RawEvent& event);

    const wchar_t* Name() const;
    const wchar_t* Value() const;
};
```

## <a name="members"></a>メンバー

[Simpleevent](simple-event.md)基本クラスから継承されたメンバーと共に、`EnvironmentVariable` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[EnvironmentVariable](#environment-variable)

### <a name="functions"></a>関数

[Name](#name)
[Value](#value)

## <a name="environment-variable"></a>EnvironmentVariable

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)イベントです。

## <a name="name"></a> Name

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>戻り値

環境変数の名前。

## <a name="value"></a>数値

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>戻り値

環境変数の値。

::: moniker-end
