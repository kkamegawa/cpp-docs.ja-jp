---
title: '呼び出しの例: 関数プロトタイプと呼び出し'
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: cbe9ee16db502c9e27dcbd74da4ef6a85f00960f
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857633"
---
# <a name="calling-example-function-prototype-and-call"></a>呼び出しの例: 関数プロトタイプと呼び出し

**Microsoft 固有の仕様**

次の例では、さまざまな呼び出し規約を使用して関数呼び出しを行った結果を示しています。

この例は、次の関数スケルトンに基づいています。 `calltype` は適切な呼び出し規約に置き換えます。

```cpp
void    calltype MyFunc( char c, short s, int i, double f );
.
.
.
void    MyFunc( char c, short s, int i, double f )
    {
    .
    .
    .
    }
.
.
.
MyFunc ('x', 12, 8192, 2.7183);
```

詳細については、「[呼び出し例の結果](../cpp/results-of-calling-example.md)」を参照してください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[呼び出し規約](../cpp/calling-conventions.md)