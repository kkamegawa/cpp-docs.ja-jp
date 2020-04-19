---
title: MSVC_TOOL_CODE 列挙型
description: C++ビルドインサイト SDK MSVC_TOOL_CODE 列挙型参照です。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MSVC_TOOL_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d88a2227808867b04ef3b0557aee9c869beaead1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335124"
---
# <a name="msvc_tool_code-enum"></a>MSVC_TOOL_CODE 列挙型

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`MSVC_TOOL_CODE` 列挙型。

## <a name="members"></a>メンバー

| Name | 値 | Description |
|--|--|--|
| `MSVC_TOOL_CODE_CL` | 0 (0x00000000) | コンパイラ (cl.exe)。 |
| `MSVC_TOOL_CODE_LINK` | 1 (0x00000001) | リンカー (link .exe)。 |

## <a name="remarks"></a>解説

C SDK 関数によって使用されます。

::: moniker-end
