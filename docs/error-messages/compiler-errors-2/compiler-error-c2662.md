---
title: コンパイラエラー C2662
ms.date: 11/04/2016
f1_keywords:
- C2662
helpviewer_keywords:
- C2662
ms.assetid: e172c2a4-f29e-4034-8232-e7dc6f83689f
ms.openlocfilehash: b2fa2643898fed510aa7cf0f483b538ebb33b033
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760453"
---
# <a name="compiler-error-c2662"></a>コンパイラエラー C2662

' function ': ' type1 ' から ' type1 ' に ' this ' ポインターを変換することはできません

コンパイラは、`this` ポインターを `type1` から `type2`に変換できませんでした。

このエラーは、`const` オブジェクトで非`const` メンバー関数を呼び出すことによって発生することがあります。  考えられる解決策は次のとおりです。

- オブジェクト宣言から `const` を削除します。

- メンバー関数に `const` を追加します。

次の例では、C2662 が生成されます。

```cpp
// C2662.cpp
class C {
public:
   void func1();
   void func2() const{}
} const c;

int main() {
   c.func1();   // C2662
   c.func2();   // OK
}
```

**/Clr**を使用してコンパイルする場合、`const` または `volatile` 修飾マネージ型で関数を呼び出すことはできません。 マネージクラスの const メンバー関数を宣言することはできないため、const マネージオブジェクトのメソッドを呼び出すことはできません。

```cpp
// C2662_b.cpp
// compile with: /c /clr
ref struct M {
   property M^ Type {
      M^ get() { return this; }
   }

   void operator=(const M %m) {
      M ^ prop = m.Type;   // C2662
   }
};

ref struct N {
   property N^ Type {
      N^ get() { return this; }
   }

   void operator=(N % n) {
      N ^ prop = n.Type;   // OK
   }
};
```

次の例では、C2662 が生成されます。

```cpp
// C2662_c.cpp
// compile with: /c
// C2662 expected
typedef int ISXVD;
typedef unsigned char BYTE;

class LXBASE {
protected:
    BYTE *m_rgb;
};

class LXISXVD:LXBASE {
public:
   // Delete the following line to resolve.
   ISXVD *PMin() { return (ISXVD *)m_rgb; }

   ISXVD *PMin2() const { return (ISXVD *)m_rgb; };   // OK
};

void F(const LXISXVD *plxisxvd, int iDim) {
   ISXVD isxvd;
   // Delete the following line to resolve.
   isxvd = plxisxvd->PMin()[iDim];

   isxvd = plxisxvd->PMin2()[iDim];
}
```
