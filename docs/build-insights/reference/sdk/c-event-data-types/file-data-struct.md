---
title: FILE_DATA 構造体
description: C++ BUILD Insights SDK FILE_DATA 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72cae8c8eb81bdb8d94897c46c5af90c89e92ab4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335196"
---
# <a name="file_data-structure"></a>FILE_DATA 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`FILE_DATA` 構造体は、ファイルの入力または出力を記述します。

## <a name="syntax"></a>構文

```cpp
typedef struct FILE_DATA_TAG
{
    const wchar_t*      Path;
    int                 TypeCode;

} FILE_DATA;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `Path` | ファイルの絶対パス |
| `TypeCode` | ファイルの種類を記述するコード。 詳細については、「 [FILE_TYPE_CODE](file-type-code-enum.md)」を参照してください。 |

::: moniker-end
