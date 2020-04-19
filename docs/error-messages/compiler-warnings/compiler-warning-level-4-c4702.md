---
title: コンパイラの警告 (レベル 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: 5e46bfef925f999ed7f04b5bbe7c88800209ed14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990654"
---
# <a name="compiler-warning-level-4-c4702"></a>コンパイラの警告 (レベル 4) C4702

到達できないコード

この警告は、Visual Studio .NET 2003: 到達できないコードに対して行われたコンパイラ準拠作業の結果です。 コンパイラ (バックエンド) が到達できないコードを検出すると、レベル4の警告 C4702 が生成されます。

Visual Studio .NET 2003 と visual Studio .NET の両方のバージョンの Visual C++で有効なコードの場合は、到達できないコードを削除するか、一部の実行フローですべてのソースコードに到達できることを確認します。

## <a name="example"></a>使用例

次の例では、C4702 が生成されます。

```cpp
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

## <a name="example"></a>使用例

**/Gx**、 **/EHc**、 **/ehsc**、または **/EHac**でコンパイルするときに extern C 関数を使用すると、extern c 関数はスローされないと見なされるため、コードに到達できなくなります。したがって、catch ブロックには到達できません。  関数がスローする可能性があるため、この警告が無効であると思われる場合は、スローされた例外に応じて、 **/eha**または **/ehs**を使用してコンパイルします。

詳細については、「 [/EH (例外処理モデル)](../../build/reference/eh-exception-handling-model.md) 」を参照してください。

次の例では、C4702 が生成されます。

```cpp
// C4702b.cpp
// compile with: /W4 /EHsc
#include <iostream>

using namespace std;
extern "C" __declspec(dllexport) void Function2(){}

int main() {
   try {
      Function2();
   }
   catch (...) {
      cout << "Exp: Function2!" << endl;   // C4702
   }
}
```
