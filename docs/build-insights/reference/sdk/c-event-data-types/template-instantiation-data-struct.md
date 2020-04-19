---
title: TEMPLATE_INSTANTIATION_DATA 構造体
description: C++ BUILD Insights SDK TEMPLATE_INSTANTIATION_DATA 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa669d715dbe56ce7e889330f46f307f520710f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335082"
---
# <a name="template_instantiation_data-structure"></a>TEMPLATE_INSTANTIATION_DATA 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`TEMPLATE_INSTANTIATION_DATA` 構造体は、テンプレートのインスタンス化を記述します。

## <a name="syntax"></a>構文

```cpp
typedef struct TEMPLATE_INSTANTIATION_DATA_TAG
{
    unsigned long long  SpecializationSymbolKey;
    unsigned long long  PrimaryTemplateSymbolKey;
    int                 KindCode;

} TEMPLATE_INSTANTIATION_DATA;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `SpecializationSymbolKey` | テンプレートの特殊化の型のキー。 この値は、分析されるトレース内で一意です。 |
| `PrimaryTemplateSymbolKey` | 特殊化されたプライマリテンプレート型のキー。 この値は、分析されるトレース内で一意です。 |
| `KindCode` | テンプレートのインスタンス化の型。 詳細については、「 [TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md)」を参照してください。 |

## <a name="remarks"></a>解説

`TEMPLATE_INSTANTIATION_DATA` 構造のキーは、分析されるトレース内で一意です。 ただし、コンパイラのフロントエンドパスが異なる2つの異なるキーは、同一の2つの型を指す場合があります。 複数のコンパイラフロントエンドパスから `TEMPLATE_INSTANTIATION_DATA` 情報を使用する場合は、 [SYMBOL_NAME](../event-table.md#symbol-name)のイベントを使用して、2つの型が等しいかどうかを判断します。 `SymbolName` イベントは、すべてのテンプレートのインスタンス化が行われた後に、コンパイラのフロントエンドパスの最後に生成されます。

::: moniker-end
