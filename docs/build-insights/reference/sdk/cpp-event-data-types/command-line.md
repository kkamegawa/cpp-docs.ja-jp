---
title: CommandLine クラス
description: Build C++ Insights SDK コマンドラインクラスのリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff16646920fe77f7f3b4cb8a194a38984c3e6c32
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334986"
---
# <a name="commandline-class"></a>CommandLine クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`CommandLine` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [COMMAND_LINE](../event-table.md#command-line)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class CommandLine : public SimpleEvent
{
public:
    CommandLine(const RawEvent& event);

    const wchar_t* Value() const;
};
```

## <a name="members"></a>メンバー

[Simpleevent](simple-event.md)基本クラスから継承されたメンバーと共に、`CommandLine` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[Ds](#command-line)

### <a name="functions"></a>関数

[Value](#value)

## <a name="command-line"></a>Ds

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[COMMAND_LINE](../event-table.md#command-line)イベントです。

## <a name="value"></a>数値

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>戻り値

コマンドラインを格納している文字列。 この値には、応答ファイルから取得された引数と、CL、\_CL\_、Link、\_リンク\_などの環境変数から取得された引数が含まれます。

::: moniker-end
