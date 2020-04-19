---
title: 関数インライン展開の問題
ms.date: 11/04/2016
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
ms.openlocfilehash: f088b0f3ec94ad59c9c5576e6090a895bb88c3ad
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856887"
---
# <a name="function-inlining-problems"></a>関数インライン展開の問題

関数のインライン化を使用している場合は、次の操作を行う必要があります。

- 含めるヘッダー ファイルで実装されたインライン関数があります。

- インライン化、ヘッダー ファイルで ON になっています。

```cpp
// LNK2019_function_inline.cpp
// compile with: /c
// post-build command: lib LNK2019_function_inline.obj
#include <stdio.h>
struct _load_config_used {
   void Test();
   void Test2() { printf("in Test2\n"); }
};

void _load_config_used::Test() { printf("in Test\n"); }
```

この場合、次のようになります。

```cpp
// LNK2019_function_inline_2.cpp
// compile with: LNK2019_function_inline.lib
struct _load_config_used {
   void Test();
   void Test2();
};

int main() {
   _load_config_used x;
   x.Test();
   x.Test2();   // LNK2019
}
```

使用する場合、`#pragma inline_depth`設定値が 2 以上があるコンパイラ ディレクティブを確認してください。 ゼロの値がオフにインライン化します。 使用しているかどうかを確認も、 **/Ob1**または **/Ob2**コンパイラ オプション。

モジュールごとに異なるコンパイル オプションをインラインと非インラインを混在させると、問題が発生することができる場合があります。 関数のインライン化がオンで C++ のライブラリが作成されたかどうか ([/Ob1](../../build/reference/ob-inline-function-expansion.md)または[/Ob2](../../build/reference/ob-inline-function-expansion.md)) が、対応するヘッダー ファイルが、機能の説明 (オプションではありません) を無効になっているインライン展開が、エラー LNK2001 が発生します。 関数は取得できませんインライン コードに、ヘッダー ファイルからがライブラリ ファイルではないためには、参照を解決するのにはアドレスがありません。

同様に、関数のインライン化を使用するプロジェクトがまだ関数を定義、.cpp ファイルにファイルが LNK2019 をやはりヘッダーではなく。 ヘッダー ファイルが含まれるすべての場所で、適切なと見なされますが、関数にのみインライン .cpp ファイルは、コンパイラを通過するときそのため、リンカーでは、他のモジュールで使用すると未解決の外部項目として、関数が表示されます。

```cpp
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

それから

```cpp
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

それから

```cpp
// LNK2019_FIP_2.cpp
// compile with: LNK2019_FIP.cpp
// LNK2019 expected
#include "LNK2019_FIP.h"
int main() {
   testclass testclsObject;

   // module cannot see the implementation of PublicStatMemFunc1
   testclsObject.PublicStatMemFunc1();
}
```

## <a name="see-also"></a>関連項目

[リンカー ツール エラー LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)