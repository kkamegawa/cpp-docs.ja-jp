---
title: INVOCATION_VERSION_DATA 構造体
description: C++ BUILD Insights SDK INVOCATION_VERSION_DATA 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 040b0f90b14133ec2b25f7a12d35b88d382c4f7a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335130"
---
# <a name="invocation_version_data-structure"></a>INVOCATION_VERSION_DATA 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`INVOCATION_VERSION_DATA` 構造体は、バージョン番号を整数値のグループとして記述します。

## <a name="syntax"></a>構文

```cpp
typedef struct INVOCATION_VERSION_DATA_TAG
{
    unsigned short VersionMajor;
    unsigned short VersionMinor;
    unsigned short BuildNumberMajor;
    unsigned short BuildNumberMinor;

} INVOCATION_VERSION_DATA;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `VersionMajor` | バージョンのメジャー番号。 |
| `VersionMinor` | バージョンのマイナー番号。 |
| `BuildNumberMajor` | ビルドのメジャー番号。 |
| `BuildNumberMinor` | ビルドのマイナー番号。 |

::: moniker-end
