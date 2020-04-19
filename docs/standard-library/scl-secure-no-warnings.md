---
title: _SCL_SECURE_NO_WARNINGS
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
ms.openlocfilehash: d19d47fe7120301740e1431765fc6edbeaa48c60
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448193"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

C++標準ライブラリ内の安全でない可能性のあるメソッドを呼び出すと、[コンパイラの警告 (レベル 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)が発生します。 この警告を無効にするには、コードでマクロ _SCL_SECURE_NO_WARNINGS を定義します。

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

プリコンパイル済みヘッダーを使用する場合は、C ランタイムライブラリまたは標準ライブラリヘッダーを含める前に、このディレクティブをプリコンパイル済みヘッダーファイルに配置します。 プリコンパイル済みヘッダーファイルをインクルードする前に個々のソースコードファイルに配置すると、コンパイラによって無視されます。

## <a name="remarks"></a>Remarks

警告 C4996 を無効にするその他の方法は、次のとおりです。

- [/D (プリプロセッサの定義)](../build/reference/d-preprocessor-definitions.md) コンパイラ オプションの使用:

   > cl /D_SCL_SECURE_NO_WARNINGS [other compiler options] myfile.cpp

- [/w](../build/reference/compiler-option-warning-level.md) コンパイラ オプションの使用:

   > cl /wd4996 [other compiler options] myfile.cpp

- [#pragma 警告](../preprocessor/warning.md) ディレクティブの使用:

   ```cpp
   #pragma warning(disable:4996)
   ```

また、 **/w\<l>\<n>** コンパイラ オプションを使用して、警告 C4996 のレベルを手動で変更できます。 たとえば、警告 C4996 をレベル 4 に設定します。

> cl /w44996 [other compiler options] myfile.cpp

詳細については、「[/w、/W0、/W1、/W2、/W3、/W4, /w1, /w2, /w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告レベル)](../build/reference/compiler-option-warning-level.md)」を参照してください。

## <a name="see-also"></a>関連項目

[安全なライブラリ: C++ 標準ライブラリ](../standard-library/safe-libraries-cpp-standard-library.md)
