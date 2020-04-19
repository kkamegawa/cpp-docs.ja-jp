---
title: コンパイラの警告 (レベル 1) C4288
ms.date: 11/04/2016
f1_keywords:
- C4288
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
ms.openlocfilehash: 81094bf019060b56337347f7d364ead7c78c8128
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626657"
---
# <a name="compiler-warning-level-1-c4288"></a>コンパイラの警告 (レベル 1) C4288

非標準の拡張が使用されています: ' var ': for ループで宣言されたループコントロール変数が for ループスコープの外側で使用されています。外側のスコープの宣言と競合します。

[/Ze](../../build/reference/za-ze-disable-language-extensions.md)および **/zc: forscope-** を使用してコンパイルする場合、for**ループで**宣言された変数は[、for ループスコープの後](../../cpp/for-statement-cpp.md)に使用されていました。 C++言語に対する Microsoft の拡張機能を使用すると、この変数をスコープ内に維持し、変数の最初の宣言が使用されないことを C4288 に通知できます。

/Ze を使用して**for ループの**Microsoft 拡張機能を指定する方法については、「 [/zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 」を参照してください。

次の例では、C4288 が生成されます。

```cpp
// C4288.cpp
// compile with: /W1 /c /Zc:forScope-
int main() {
   int i = 0;    // not used in this program
   for (int i = 0 ; ; ) ;
   i++;   // C4288 using for-loop declaration of i
}
```