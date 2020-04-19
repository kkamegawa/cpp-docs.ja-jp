---
title: コンパイラの警告 (レベル 4) C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: 2f457b5424cbca071e047f4375aaa85962e52210
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991486"
---
# <a name="compiler-warning-level-4-c4242"></a>コンパイラの警告 (レベル 4) C4242

' identifier ': ' type1 ' から ' type1 ' への変換です。データが失われる可能性があります。

型が異なります。 型変換によってデータが失われる可能性があります。 コンパイラは、型変換を行います。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

C4242 の詳細については、「[一般的なコンパイラエラー](/windows/win32/WinProg64/common-compiler-errors)」を参照してください。

次の例では、C4242 が生成されます。

```cpp
// C4242.cpp
// compile with: /W4
#pragma warning(4:4242)
int func() {
   return 0;
}

int main() {
   char a;
   a = func();   // C4242, return type and variable type do not match
}
```
