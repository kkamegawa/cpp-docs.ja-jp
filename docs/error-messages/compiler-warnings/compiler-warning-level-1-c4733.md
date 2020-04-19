---
title: コンパイラの警告 (レベル 1) C4733
ms.date: 11/04/2016
f1_keywords:
- C4733
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
ms.openlocfilehash: fbecdda481748aa77eefdab8d61e50350804e09f
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051318"
---
# <a name="compiler-warning-level-1-c4733"></a>コンパイラの警告 (レベル 1) C4733

インライン asm が ' FS: 0 ' に割り当てられています: ハンドラーがセーフハンドラーとして登録されていません

FS で値を変更する関数: 0新しい例外ハンドラーを追加するには、ハンドラーが有効な例外ハンドラーとして登録されていない可能性があるため、安全な例外では機能しない可能性があります (「 [/safeseh](../../build/reference/safeseh-image-has-safe-exception-handlers.md)」を参照してください)。

この警告を解決するには、FS: 0 を削除します。この警告を無効にして、を使用し[ます。SAFESEH](../../assembler/masm/dot-safeseh.md) 。安全な例外ハンドラーを指定します。

次の例では、C4733 が生成されます。

```cpp
// C4733.cpp
// compile with: /W1 /c
// processor: x86
#include "stdlib.h"
#include "stdio.h"
void my_handler()
{
   printf("Hello from my_handler\n");
   exit(1);
}

int main()
{
   _asm {
      push    my_handler
      mov     eax, DWORD PTR fs:0
      push    eax
      mov     DWORD PTR fs:0, esp   // C4733
   }

   *(int*)0 = 0;
}
```