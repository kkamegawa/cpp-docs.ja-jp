---
title: 呼び出しクラス
description: ビルドC++インサイト SDK 呼び出しクラスの参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c4698300a3eeaf77210ad74f84b0c0cd219b457
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334746"
---
# <a name="invocation-class"></a>呼び出しクラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`Invocation` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [コンパイラ](../event-table.md#compiler)または[リンカー](../event-table.md#linker)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class Invocation : public Activity
{
    const INVOCATION_DATA* data_;

public:
    enum class Type
    {
        CL      = MSVC_TOOL_CODE_CL,
        LINK    = MSVC_TOOL_CODE_LINK
    };

    Invocation(const RawEvent& event);

    Type             Type() const;
    const char*      ToolVersionString() const;
    const wchar_t*   WorkingDirectory() const;
    const wchar_t*   ToolPath() const;

    const INVOCATION_VERSION_DATA& ToolVersion() const;
};
```

## <a name="members"></a>メンバー

[アクティビティ](activity.md)基本クラスから継承されたメンバーと共に、`Invocation` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[[呼び出し]](#invocation)

### <a name="functions"></a>関数

[ツール](#tool-path)ヒント
[Toolversion](#tool-version)
[toolversionstring](#tool-version-string)
[Type](#type)
[WorkingDirectory](#working-directory)

## <a name="invocation"></a>出せる

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[コンパイラ](../event-table.md#compiler)または[リンカー](../event-table.md#linker)イベント。

## <a name="tool-path"></a>ToolPath

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>戻り値

呼び出されたツールへの絶対パス。

## <a name="tool-version"></a>ToolVersion

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>戻り値

[INVOCATION_VERSION_DATA](../c-event-data-types/invocation-version-data-struct.md)参照として呼び出されたツールのバージョン。

## <a name="tool-version-string"></a>ToolVersionString

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>戻り値

呼び出されたツールのバージョンを ANSI 文字列として指定します。

## <a name="type"></a>各種

```cpp
Type Type() const;
```

### <a name="return-value"></a>戻り値

呼び出されたツールを示すコード。

## <a name="working-directory"></a>WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>戻り値

ツールが呼び出されたディレクトリへの絶対パス。

::: moniker-end
