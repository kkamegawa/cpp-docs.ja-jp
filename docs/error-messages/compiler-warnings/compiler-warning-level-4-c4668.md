---
title: コンパイラの警告 (レベル 4) C4668
ms.date: 11/04/2016
f1_keywords:
- C4668
helpviewer_keywords:
- C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
ms.openlocfilehash: 84834ce0f980502e16a8398d35da85d1a005c9cb
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990548"
---
# <a name="compiler-warning-level-4-c4668"></a>コンパイラの警告 (レベル 4) C4668

'symbol' は、'directives' を '0' に置換するプリプロセッサ マクロとして定義されていません。

定義されていないシンボルがプリプロセッサディレクティブで使用されました。 シンボルは false に評価されます。 シンボルを定義するには、 [#define ディレクティブ](../../preprocessor/hash-define-directive-c-cpp.md)または[/d](../../build/reference/d-preprocessor-definitions.md)コンパイラオプションのいずれかを使用できます。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

## <a name="example"></a>使用例

次の例では、C4668 が生成されます。

```cpp
// C4668.cpp
// compile with: /W4
#include <stdio.h>

#pragma warning (default : 4668)   // turn warning on

int main()
{
    #if q   // C4668, q is not defined
        printf_s("defined");
    #else
        printf_s("undefined");
    #endif
}
```
