---
title: 文字定数化演算子 (#@)
ms.date: 08/29/2019
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: cb2a4e07287edf5ed2d0850ec7d870c8ef307879
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218534"
---
# <a name="charizing-operator-"></a>文字定数化演算子 (#@)

**Microsoft 固有の仕様**

文字定数化演算子は、マクロの引数でのみ使用できます。 マクロ`#@`の定義で仮パラメーターの前にがある場合、実際の引数は単一引用符で囲まれ、マクロが展開されるときに文字として扱われます。 例えば:

```cpp
#define makechar(x)  #@x
```

は、次のステートメント

```cpp
a = makechar(b);
```

を次のように展開します

```cpp
a = 'b';
```

単一引用符文字 (`'`) は、文字型の演算子と共に使用することはできません。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[プリプロセッサ演算子](../preprocessor/preprocessor-operators.md)
