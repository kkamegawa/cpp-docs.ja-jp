---
title: fp_contract プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
ms.openlocfilehash: 833d8e7f4b8c9da18901610e52afed619468c5c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218566"
---
# <a name="fp_contract-pragma"></a>fp_contract プラグマ

浮動小数点省略形を実行するかどうかを決定します。 浮動小数点省略形は、2つの独立した浮動小数点演算を1つの命令に結合する FMA () などの命令です。 これらの命令を使用すると、浮動小数点の精度に影響を与える可能性があります。これは、各操作の後に丸め処理を行うのではなく、両方の操作の後に1回だけラウンドを実行するため

## <a name="syntax"></a>構文

> **#pragma fp_contract (** { **on** | **off** } **)**

## <a name="remarks"></a>Remarks

既定では、 **fp_contract**は**オンに**なっています。 これは、可能であれば、浮動小数点の省略形命令を使用するようにコンパイラに指示します。 個々の浮動小数点命令を保持するには、 **fp_contract**を**off**に設定します。

浮動小数点の動作の詳細については、「 [/fp (浮動小数点の動作の指定)](../build/reference/fp-specify-floating-point-behavior.md)」を参照してください。

その他の浮動小数点プラグマには以下があります。

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>例

このサンプルから生成されたコードでは、ターゲットプロセッサで使用可能な場合でも、追加命令が使用されません。 コメントアウト`#pragma fp_contract (off)`した場合、生成されたコードは、使用可能な場合は、追加された非表示命令を使用することがあります。

```cpp
// pragma_directive_fp_contract.cpp
// on x86 and x64 compile with: /O2 /fp:fast /arch:AVX2
// other platforms compile with: /O2

#include <stdio.h>

// remove the following line to enable FP contractions
#pragma fp_contract (off)

int main() {
   double z, b, t;

   for (int i = 0; i < 10; i++) {
      b = i * 5.5;
      t = i * 56.025;

      z = t * i + b;
      printf("out = %.15e\n", z);
   }
}
```

```Output
out = 0.000000000000000e+00
out = 6.152500000000000e+01
out = 2.351000000000000e+02
out = 5.207249999999999e+02
out = 9.184000000000000e+02
out = 1.428125000000000e+03
out = 2.049900000000000e+03
out = 2.783725000000000e+03
out = 3.629600000000000e+03
out = 4.587525000000000e+03
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
