---
title: コンパイラ エラー C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: 7c3f9f05bf04c9a1c20fff7910836e7b50468a8e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742458"
---
# <a name="compiler-error-c3642"></a>コンパイラ エラー C3642

' return_type/args ': ネイティブコードから __clrcall 呼び出し規約を持つ関数を呼び出すことはできません

[__Clrcall](../../cpp/clrcall.md)呼び出し規約でマークされた関数は、ネイティブ (アンマネージ) コードから呼び出すことができません。

*return_type/args*は、関数の名前か、呼び出そうとしている `__clrcall` 関数の型です。  型は、関数ポインターを使用してを呼び出しているときに使用されます。

ネイティブコンテキストからマネージ関数を呼び出すには、`__clrcall` 関数を呼び出す "ラッパー" 関数を追加します。 または、CLR マーシャリング機構を使用することもできます。詳細については、「[方法: PInvoke を使用して関数ポインターをマーシャリングする](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)」を参照してください。

次の例では、C3642 が生成されます。

```cpp
// C3642.cpp
// compile with: /clr
using namespace System;
struct S {
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall
      Console::WriteLine(s);
   }
   void Test2(char * s) {
      Test(gcnew String(s));
   }
};

#pragma unmanaged
int main() {
   S s;
   s.Test("abc");   // C3642
   s.Test2("abc");   // OK
}
```
