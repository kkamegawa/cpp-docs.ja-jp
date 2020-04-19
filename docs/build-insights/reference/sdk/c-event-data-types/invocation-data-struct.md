---
title: INVOCATION_DATA 構造体
description: C++ BUILD Insights SDK INVOCATION_DATA 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b2e8ddcf79201d8bcbbb8eb298b96b5c7680f90e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335142"
---
# <a name="invocation_data-structure"></a>INVOCATION_DATA 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`INVOCATION_DATA` 構造体は、コンパイラまたはリンカーの呼び出しを記述します。

## <a name="syntax"></a>構文

```cpp
typedef struct INVOCATION_DATA_TAG
{
    int                         MSVCToolCode;

    INVOCATION_VERSION_DATA     ToolVersion;

    const char*                 ToolVersionString;
    const wchar_t*              WorkingDirectory;
    const wchar_t*              ToolPath;

} INVOCATION_DATA;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `MSVCToolCode` | 呼び出しの型を識別するコード。 詳細については、「 [MSVC_TOOL_CODE](msvc-tool-code-enum.md)」を参照してください。 |
| `ToolVersion` | 呼び出されたツールのバージョンを整数値のグループとして格納するオブジェクト。 |
| `ToolVersionString` | 呼び出されたツールのバージョンをテキスト形式で記述します。 |
| `WorkingDirectory` | 呼び出しが行われたディレクトリ。 |
| `ToolPath` | 呼び出されたツールの絶対パス。 |

::: moniker-end
