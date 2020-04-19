---
title: 数値演算エラー M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 6d3f107de7e45653374036ecafaa864cb3eff5b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393247"
---
# <a name="math-error-m6201"></a>数値演算エラー M6201

'function': (_d) エラー

指定された関数の引数は、その関数の有効な入力値のドメイン外でした。

## <a name="example"></a>例

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

このエラーが、`_matherr`関数、関数名、引数、およびエラーの種類を使用します。 書き直すことができます、`_matherr`特定の実行時の浮動小数点数値演算エラーの処理をカスタマイズする関数。