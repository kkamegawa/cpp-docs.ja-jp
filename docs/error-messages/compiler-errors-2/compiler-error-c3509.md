---
title: コンパイラ エラー C3509
ms.date: 11/04/2016
f1_keywords:
- C3509
helpviewer_keywords:
- C3509
ms.assetid: cc2db39a-2f98-4e40-b803-496e585494e6
ms.openlocfilehash: d91bbdf67b49e5722491f562b5eced2c5af10837
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753745"
---
# <a name="compiler-error-c3509"></a>コンパイラ エラー C3509

' type ': オートメーションの戻り値の型が無効です。パラメーターが ' retval ' とマークされている場合、戻り値の型は ' void '、' HRESULT ' または ' SCODE ' である必要があります

COM インターフェイスのメソッドは、void または HRESULT を返す必要があります。

次の例では、C3509 が生成されます。

```cpp
// C3509.cpp
#define _ATL_DEBUG_QI

#define WIN32_LEAN_AND_MEAN   // Exclude rarely-used stuff from Windows headers
#define STRICT
#ifndef _WIN32_WINNT
#define _WIN32_WINNT 0x0400
#endif

#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
extern CComModule _Module;
#include <atlcom.h>
#include <atlctl.h>
#include <atlstr.h>

[module(name=oso)];

[dispinterface, uuid(00000000-0000-0000-0000-000000000001)]
__interface I {
   [id(1)] int f([out, retval] int*);   // C3509
   // try the following line instead
   // [id(1)] void f([out, retval] int*);
};

[coclass, uuid(00000000-0000-0000-0000-000000000002)]
struct C : I {
   int f(int*) {
   // try the following line instead, and delete return statement
   // void f(int*) {
      return 0;
   }
};

int main() {
}
```
