---
title: コンパイラ エラー C3364
ms.date: 11/04/2016
f1_keywords:
- C3364
helpviewer_keywords:
- C3364
ms.assetid: 98654741-60fe-4472-a6af-e580f8c0a6e1
ms.openlocfilehash: eae1e7ddbc34d36b55d7afa424c137db00ef047d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757346"
---
# <a name="compiler-error-c3364"></a>コンパイラ エラー C3364

' delegate ': delegate コンストラクター: 引数はマネージクラスまたはグローバル関数のメンバー関数へのポインターでなければなりません

デリゲートのコンストラクターの2番目のパラメーターは、メンバー関数のアドレス、または任意のクラスの静的メンバー関数のアドレスのいずれかを受け取ります。 どちらも単純なアドレスとして扱われます。

次の例では、C3364 が生成されます。

```cpp
// C3364_2.cpp
// compile with: /clr

delegate int D( int, int );

ref class C {
public:
   int mf( int, int ) {
      return 1;
   }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC,pC->mf( 1, 2 ) ); // C3364

   // try the following line instead
   // System::Delegate^ pD = gcnew D(pC, &C::mf);
}
```
