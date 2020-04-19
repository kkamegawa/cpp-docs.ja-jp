---
title: CL_PASS_DATA 構造体
description: C++ BUILD Insights SDK CL_PASS_DATA 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3df5b5bc1cddbadc4a4d432ae021dd8b338c532e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335256"
---
# <a name="cl_pass_data-structure"></a>CL_PASS_DATA 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`CL_PASS_DATA` 構造体は、コンパイルパスを記述します。

## <a name="syntax"></a>構文

```cpp
typedef struct CL_PASS_DATA_TAG
{
    int                         TranslationUnitPassCode;
    const wchar_t*              InputSourcePath;
    const wchar_t*              OutputObjectPath;

} CL_PASS_DATA;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `TranslationUnitPassCode` | 実行されているコンパイルパスを識別するコード。 詳細については、「 [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md)」を参照してください。 |
| `InputSourcePath` | このコンパイルパスC++が実行されている C またはソースファイル。 |
| `OutputObjectPath` | コンパイラによって生成されるオブジェクトファイル。 |

::: moniker-end
