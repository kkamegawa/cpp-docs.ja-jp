---
title: FrontEndFile クラス
description: C++ BUILD Insights SDK FrontEndFile クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 094b1326765e0e8edb00534ecb3d94c46702d4ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334794"
---
# <a name="frontendfile-class"></a>FrontEndFile クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`FrontEndFile` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [FRONT_END_FILE](../event-table.md#front-end-file)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class FrontEndFile : public Activity
{
public:
    FrontEndFile(const RawEvent& event);

    const char* Path() const;
};
```

## <a name="members"></a>メンバー

[アクティビティ](activity.md)基本クラスから継承されたメンバーと共に、`FrontEndFile` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[FrontEndFile](#front-end-file)

### <a name="functions"></a>関数

[[パス]](#path)

## <a name="front-end-file"></a>FrontEndFile

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[FRONT_END_FILE](../event-table.md#front-end-file)イベントです。

## <a name="path"></a> Path

```cpp
const char* Path() const;
```

### <a name="return-value"></a>戻り値

UTF-8 でエンコードされたファイルへの絶対パス。

::: moniker-end
