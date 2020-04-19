---
title: TRANSLATION_UNIT_PASS_CODE 列挙型
description: C++ビルドインサイト SDK TRANSLATION_UNIT_PASS_CODE 列挙型参照です。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1219eed98fd01e8c91d8750977e2d8ca4498d649
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335046"
---
# <a name="translation_unit_pass_code-enum"></a>TRANSLATION_UNIT_PASS_CODE 列挙型

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`TRANSLATION_UNIT_PASS_CODE` 列挙型。

## <a name="members"></a>メンバー

| Name | 値 | Description |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0 (0x00000000) | フロントエンドパス。ソースコードを解析して中間言語に変換します。 |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | バックエンドパス。中間言語を最適化し、マシンコードに変換します。 |

## <a name="remarks"></a>解説

C SDK 関数によって使用されます。

::: moniker-end
