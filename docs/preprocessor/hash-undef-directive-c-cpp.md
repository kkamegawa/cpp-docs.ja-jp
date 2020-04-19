---
title: '#undef ディレクティブ (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
ms.openlocfilehash: 1a69bc568579e7da7c7e3816cb67c8153b8f1a27
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220219"
---
# <a name="undef-directive-cc"></a>#undef ディレクティブ (C/C++)

`#define` で作成された名前を削除 (定義解除) します。

## <a name="syntax"></a>構文

> **#undef** *識別子*

## <a name="remarks"></a>Remarks

**#Undef**ディレクティブにより、*識別子*の現在の定義が削除されます。 その結果、プリプロセッサでは後続の*識別子*が無視されます。 **#Undef**を使用してマクロ定義を削除するには、パラメーターリストではなく、マクロ*識別子*だけを指定します。

また、以前の定義がない識別子に **#undef**ディレクティブを適用することもできます。 これにより、その識別子が未定義であることが保証されます。 マクロ置換は **#undef**ステートメント内では実行されません。

通常、 **#undef**ディレクティブは、識別子が`#define`特別な意味を持つソースプログラムで領域を作成するためのディレクティブと組み合わせて使用されます。 たとえば、ソース プログラムの特定の関数でマニフェスト定数を使用すると、プログラムの残り部分に影響を与えない環境固有の値を定義できます。 また、 **#undef**ディレクティブは、 `#if`ディレクティブを使用して、ソースプログラムの条件付きコンパイルを制御します。 詳細については、「 [#if、#elif、#else、および #endif ディレクティブ](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)」を参照してください。

次の例では、 **#undef**ディレクティブによって、シンボリック定数とマクロの定義が削除されます。 マクロの識別子のみが指定されていることに注意してください。

```C
#define WIDTH 80
#define ADD( X, Y ) ((X) + (Y))
.
.
.
#undef WIDTH
#undef ADD
```

**Microsoft 固有の仕様**

マクロは、 `/U`オプションを使用してコマンドラインから未定義にすることができます。その後、マクロ名を未定義にすることができます。 このコマンドを発行した場合の効果は、ファイル`#undef`の先頭にある一連の*マクロ名*ステートメントと同じです。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[プリプロセッサディレクティブ](../preprocessor/preprocessor-directives.md)
