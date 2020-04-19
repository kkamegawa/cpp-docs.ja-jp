---
title: 加法演算子の使用
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 0e2d802a77c56b8f458b614b29e86e2e1d30a55e
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151430"
---
# <a name="using-the-additive-operators"></a>加法演算子の使用

加算演算子と減算演算子を示す次の例は、これらの宣言を使用します。

```
int i = 4, j;
float x[10];
float *px;
```

これらのステートメントは等価です。

```
px = &x[4 + i];
px = &x[4] + i;
```

`i` の値は **float** の長さで乗算され、`&x[4]` に加算されます。 結果のポインター値は `x[8]` のアドレスです。

```
j = &x[i] - &x[i-2];
```

この例では、`x` の 3 番目の要素のアドレス (`x[i-2]` で指定) は、`x` の 5 番目の要素のアドレス (`x[i]` で指定) から減算されます。 違いを **float** の長さで割ります。結果は、整数値 2 です。

## <a name="see-also"></a>関連項目

[C 加法演算子](../c-language/c-additive-operators.md)
