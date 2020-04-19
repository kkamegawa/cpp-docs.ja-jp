---
title: CompilerPass クラス
description: C++ BUILD Insights SDK CompilerPass クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c2fa1c2c4be8aaf5bec77b383f93a4b033ca8e3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334956"
---
# <a name="compilerpass-class"></a>CompilerPass クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`CompilerPass` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [BACK_END_PASS](../event-table.md#back-end-pass)または[FRONT_END_PASS](../event-table.md#front-end-pass)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class CompilerPass : public Activity
{
public:
    enum class PassCode
    {
        FRONT_END,
        BACK_END
    };

    CompilerPass(const RawEvent& event);

    PassCode       PassCode() const;
    const wchar_t* InputSourcePath() const;
    const wchar_t* OutputObjectPath() const;
};
```

## <a name="members"></a>メンバー

[アクティビティ](activity.md)基本クラスから継承されたメンバーと共に、`CompilerPass` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[CompilerPass](#compiler-pass)

### <a name="enums"></a>列挙型

#### <a name="passcode"></a>パスコード

|||
|-|-|
|FRONT_END|フロントエンドパス。|
|BACK_END|バックエンドパス。|

### <a name="functions"></a>関数

[Inputsourcepath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
[パスコード](#pass-code)の\

## <a name="compiler-pass"></a>CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[BACK_END_PASS](../event-table.md#back-end-pass)または[FRONT_END_PASS](../event-table.md#front-end-pass)イベント。

## <a name="input-source-path"></a>InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>戻り値

このコンパイラによって処理される入力ソースファイルへの絶対パス。

## <a name="output-object-path"></a>OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>戻り値

このコンパイラによって生成される出力オブジェクトファイルへの絶対パス。

## <a name="pass-code"></a>パスコード

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>戻り値

この CompilerPass オブジェクトによって表されるコンパイラパスを示すコード。

::: moniker-end
