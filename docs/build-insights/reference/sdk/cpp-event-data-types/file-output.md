---
title: FileOutput クラス
description: C++ビルドインサイト SDK fileoutput クラス参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1c4053d0378ddb9d5dd061bbc9889c454dc9b52c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334842"
---
# <a name="fileoutput-class"></a>FileOutput クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`FileOutput` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output)、 [EXP_OUTPUT](../event-table.md#exp-output)、 [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output)、 [LIB_OUTPUT](../event-table.md#lib-output)、または[OBJ_OUTPUT](../event-table.md#obj-output)イベントと一致させるには、このメソッドを使用します。

## <a name="syntax"></a>構文

```cpp
class FileOutput : public SimpleEvent
{
public:
    enum class Type
    {
        OTHER               = FILE_TYPE_CODE_OTHER,
        OBJ                 = FILE_TYPE_CODE_OBJ,
        EXECUTABLE_IMAGE    = FILE_TYPE_CODE_EXECUTABLE_IMAGE,
        LIB                 = FILE_TYPE_CODE_LIB,
        IMP_LIB             = FILE_TYPE_CODE_IMP_LIB,
        EXP                 = FILE_TYPE_CODE_EXP
    };

    FileOutput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>メンバー

[Simpleevent](simple-event.md)基本クラスから継承されたメンバーと共に、`FileOutput` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[FileOutput](#file-output)

### <a name="functions"></a>関数

[パス](#path)
の[種類](#type)

## <a name="file-output"></a>FileOutput

```cpp
FileOutput(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output)、 [EXP_OUTPUT](../event-table.md#exp-output)、 [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output)、 [LIB_OUTPUT](../event-table.md#lib-output)、または[OBJ_OUTPUT](../event-table.md#obj-output)イベント。

## <a name="path"></a> Path

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>戻り値

出力ファイルへの絶対パス。

## <a name="type"></a>各種

```cpp
Type Type() const;
```

### <a name="return-value"></a>戻り値

出力ファイルの種類を記述するコード。

::: moniker-end
