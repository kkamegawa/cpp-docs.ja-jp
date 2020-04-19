---
title: コンパイラ エラー C3070
ms.date: 11/04/2016
f1_keywords:
- C3070
helpviewer_keywords:
- C3070
ms.assetid: ac88584d-40a6-4176-90f3-2371c3c935f2
ms.openlocfilehash: d97550560e12ef9778553a809e02c1fb0d2d8b19
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758204"
---
# <a name="compiler-error-c3070"></a>コンパイラ エラー C3070

'property': プロパティに 'set' メソッドがありません

プロパティの set アクセサー メソッドが定義されていません。 詳細については、「 [property](../../extensions/property-cpp-component-extensions.md)」を参照してください。

次の例では C3070 が生成されます。

```cpp
// C3070.cpp
// compile with: /clr
ref class R {
public:
   R(int size) {
      m_data = gcnew array<int>(size);
   }

   property int % MyProp[int] {
      int% get(int index) {
         return m_data[index];
      }
   }

   property int % MyProp2[int] {
      int% get(int index) {
         return m_data[index];
      }
      void set(int index, int % value) {}
   }

   property const int % MyProp3[int] {
      const int% get(int index) {
         return m_data[index];
      }
      void set(int index, const int % value) {}
   }

private:
   array<int>^ m_data;
};

int main() {
   R^ r = gcnew R(10);
   r->MyProp[4] = 4;   // C3070

   int value = 4;
   r->MyProp2[4] = value;   // OK
   r->MyProp3[4] = 4;   // OK
}
```
