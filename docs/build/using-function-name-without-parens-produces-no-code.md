---
title: "\"()\" のない関数名とコードの生成"
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
ms.openlocfilehash: 51be77dc8f4fe072ea6cc46dd51e38862649feda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314599"
---
# <a name="using-function-name-without--produces-no-code"></a>"()" のない関数名とコードの生成

かっこを使用せず、プログラムで宣言された関数名を使用する場合、コンパイラはコードを生成しません。 これは、関数は、コンパイラが関数のアドレスを計算するためのパラメーターを受け取るかどうかに関係なくに発生しますただし、関数呼び出し演算子 (「)」が存在しないため、呼び出しは行われません。 この結果は、次のようにします。

```
// compile with /Wall to generate a warning
int a;
a;      // no code generated here either
```

Visual C での警告レベル 4 を使用しても診断出力が生成されます。 警告は発行されません。コードは生成されません。

次のサンプル コード (警告) と共にコンパイルしエラーを発生させずに正しくリンクとに関連してコードの生成`funcn( )`します。 これを正しく機能させるには、関数呼び出し演算子 (「)」を追加します。

```
#include <stdio.h>
void funcn();

int main() {
   funcn;      /* missing function call operator;
                  call will fail.  Use funcn() */
   }

void funcn() {
   printf("\nHello World\n");
}
```

## <a name="see-also"></a>関連項目

[コードの最適化](optimizing-your-code.md)
