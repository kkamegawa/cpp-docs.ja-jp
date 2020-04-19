---
title: TEMPLATE_INSTANTIATION_KIND_CODE 列挙型
description: C++ビルドインサイト SDK TEMPLATE_INSTANTIATION_KIND_CODE 列挙型参照です。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_KIND_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 21547b1db997cb755e6836f27efc512e1388d274
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335070"
---
# <a name="template_instantiation_kind_code-enum"></a>TEMPLATE_INSTANTIATION_KIND_CODE 列挙型

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`TEMPLATE_INSTANTIATION_KIND_CODE` 列挙型。

## <a name="members"></a>メンバー

| Name | 値 | Description |
|--|--|--|
| `TEMPLATE_INSTANTIATION_KIND_CODE_CLASS` | 0 (0x00000000) | クラステンプレートのインスタンス化。 |
| `TEMPLATE_INSTANTIATION_KIND_CODE_FUNCTION` | 1 (0x00000001) | 関数テンプレートのインスタンス化。 |
| `TEMPLATE_INSTANTIATION_KIND_CODE_VARIABLE` | 2 (0x00000002) | Constexpr 変数のインスタンス化。 |
| `TEMPLATE_INSTANTIATION_KIND_CODE_CONCEPT` | 3 (0x00000003) | 概念テンプレートのインスタンス化。 |

## <a name="remarks"></a>解説

::: moniker-end
