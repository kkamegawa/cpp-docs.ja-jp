---
title: コンパイラの警告 (レベル 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 3a8f2093e90f8a681d171e19e2b8a066546f8684
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990661"
---
# <a name="compiler-warning-level-4-c4571"></a>コンパイラの警告 (レベル 4) C4571

情報: キャッチ (...) のセマンティクスが Visual C++ 7.1 以降に変更されました。構造化例外 (SEH) はキャッチされなくなりました。

C4571 は、 **/ehs**を使用してコンパイルするときに、すべての catch (...) ブロックに対して生成されます。

**/Ehs**を使用してコンパイルする場合、catch (...) ブロックは構造化例外をキャッチしません (0 による除算、null ポインターなど)。catch (...) ブロックは、明示的にスローされC++た例外のみをキャッチします。  詳細については、「[例外処理](../../cpp/exception-handling-in-visual-cpp.md)」を参照してください。

既定では、この警告はオフに設定されています。  この警告をオンにすると、 **/ehs**を使用してコンパイルするときに、catch (...) ブロックが構造化例外をキャッチしないようにします。  詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

C4571 は、次のいずれかの方法で解決できます。

- 引き続き catch (...) ブロックを使用して構造化例外をキャッチする場合は、 **/eha**を使用してコンパイルします。

- Catch (...) ブロックで構造化例外をキャッチしない場合でも、catch (...) ブロックを使用する場合は、C4571 を有効にしないでください。  構造化例外処理キーワードを使用して構造化例外をキャッチすることもできます ( **__try**、 **__except**、および **__finally**)。  ただし、コンパイルされた **/ehs**デストラクターは、SEH 例外がC++発生したときではなく、例外がスローされたときにのみ呼び出されることに注意してください。

- Catch (...) ブロックを特定の catch ブロックに置き換えますC++例外、必要に応じて、構造化例外処理の周囲に追加し、C++例外処理 ( **__try**、 **__except**と **__finally**)。  詳細については、「[構造化例外処理 (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) 」を参照してください。

詳細については、「 [/EH (例外処理モデル)](../../build/reference/eh-exception-handling-model.md) 」を参照してください。

## <a name="example"></a>使用例

次の例では、C4571 が生成されます。

```cpp
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```
