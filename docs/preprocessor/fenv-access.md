---
title: fenv_access プラグマ
description: Fenv_access プラグマディレクティブの使用法と効果について説明します。 Fenv_access ディレクティブは、実行時に浮動小数点環境へのアクセスを制御します。
ms.date: 11/19/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: e03eb404f2805a4f7c96509600c063c1b1acf629
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305848"
---
# <a name="fenv_access-pragma"></a>fenv_access プラグマ

浮動小数点環境フラグのテストおよびモードの変更を変更できる最適化を無効 (**on**) または有効 (**オフ**) にします。

## <a name="syntax"></a>構文

> **#pragma fenv_access (** { **on** |  **}** **)**

## <a name="remarks"></a>コメント

既定では、 **fenv_access**は**オフ**になっています。 コンパイラは、コードが浮動小数点環境にアクセスしたり操作したりしないことを前提としています。 環境へのアクセスが必要ない場合、コンパイラは浮動小数点コードを最適化するためにさらに多くのことを行うことができます。

コードが浮動小数点の状態フラグ、例外、または制御モードフラグを設定する場合は、 **fenv_access**を有効にします。 コンパイラは、浮動小数点の最適化を無効にして、コードが常に浮動小数点環境にアクセスできるようにします。

[/Fp: strict] コマンドラインオプションを使用すると、 **fenv_access**が自動的に有効になります。 このとその他の浮動小数点動作の詳細については、「 [/fp (浮動小数点の動作の指定)](../build/reference/fp-specify-floating-point-behavior.md)」を参照してください。

**Fenv_access**プラグマを他の浮動小数点の設定と組み合わせて使用する方法には、次のような制限があります。

- 正確なセマンティクスが有効になっていない限り、 **fenv_access**を有効にすることはできません。 正確なセマンティクスを有効にするには、 [float_control](float-control.md)プラグマを使用するか、 [/fp: 精密](../build/reference/fp-specify-floating-point-behavior.md)または[/fp: strict](../build/reference/fp-specify-floating-point-behavior.md)コンパイラオプションを使用します。 他の浮動小数点コマンドラインオプションが指定されていない場合、コンパイラは既定で **/fp: 精密**になります。

- **Fenv_access (on)** が設定されている場合、 **float_control**を使用して正確なセマンティクスを無効にすることはできません。

**Fenv_access**の対象となる最適化の種類は次のとおりです。

- グローバルの共通部分式の削除

- コードの移動

- 定数の折りたたみ

その他の浮動小数点プラグマには以下があります。

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>使用例

この例では、 **fenv_access**を**on**に設定して、24ビット精度の浮動小数点制御レジスタを設定します。

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2 /arch:IA32
// processor: x86
#include <stdio.h>
#include <float.h>
#include <errno.h>
#pragma fenv_access (on)

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=9.999999776482582e-03
```

前のサンプルの `#pragma fenv_access (on)` をコメントアウトすると、出力は異なります。 これは、コンパイラがコンパイル時の評価を行うためです。この評価では、制御モードは使用されません。

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2 /arch:IA32
#include <stdio.h>
#include <float.h>

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=1.000000000000000e-02
```

## <a name="see-also"></a>参照

[プラグマディレクティブと __pragma キーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
