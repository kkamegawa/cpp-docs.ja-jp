---
title: SymbolName クラス
description: C++ BUILD Insights SDK SymbolName クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b5e9a9b22db99c099b9f7dc1813fb335358a83e8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334548"
---
# <a name="symbolname-class"></a>SymbolName クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`SymbolName` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [SYMBOL_NAME](../event-table.md#symbol-name)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class SymbolName : public SimpleEvent
{
public:
    SymbolName(const RawEvent& event);

    const unsigned long long&  Key() const;
    const char*                Name() const;
};
```

## <a name="members"></a>メンバー

[Simpleevent](simple-event.md)基本クラスから継承されたメンバーと共に、`SymbolName` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[SymbolName](#symbol-name)

### <a name="functions"></a>関数

[キー](#key)
[名](#name)

## <a name="key"></a>レジストリ

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>戻り値

この記号によって表される型の数値識別子。 この識別子は、コンパイラのフロントエンドパス内で一意です。

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>戻り値

UTF-8 でエンコードされた、シンボルによって表される型の名前。

## <a name="symbol-name"></a>SymbolName

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[SYMBOL_NAME](../event-table.md#symbol-name)イベントです。

::: moniker-end
