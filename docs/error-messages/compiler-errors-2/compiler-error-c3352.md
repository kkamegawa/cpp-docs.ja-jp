---
title: コンパイラ エラー C3352
ms.date: 11/04/2016
f1_keywords:
- C3352
helpviewer_keywords:
- C3352
ms.assetid: f233bed7-474e-425f-aad2-7801578169d4
ms.openlocfilehash: b679a89bb768ad7a50d0bbaa7b814c7a72f9f4c5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740430"
---
# <a name="compiler-error-c3352"></a>コンパイラ エラー C3352

' function ': 指定された関数は、デリゲート型 ' type ' と一致しません

`function` のパラメーターリストとデリゲートが一致しません。

詳細については、「 [delegate (C++コンポーネント拡張)](../../extensions/delegate-cpp-component-extensions.md)」を参照してください。

次の例では、C3352 が生成されます。

```cpp
// C3352.cpp
// compile with: /clr
delegate int D( int, int );
ref class C {
public:
   int mf( int ) {
      return 1;
   }

   // Uncomment the following line to resolve.
   // int mf(int, int) { return 1; }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC, &C::mf );   // C3352
}
```
