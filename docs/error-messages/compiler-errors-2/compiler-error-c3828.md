---
title: コンパイラ エラー C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: 4b47ddbf0775cab2bd7214f68d1b4ed6e06e6eea
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741704"
---
# <a name="compiler-error-c3828"></a>コンパイラ エラー C3828

' object type ': マネージクラスまたは WinRTclasses のインスタンスの作成中に配置引数を使用することはできません

マネージ型または Windows ランタイム型のオブジェクトを作成するときに、operator [ref new、gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md) 、または[new](../../cpp/new-operator-cpp.md)の配置形式を使用することはできません。

次の例では、C3828 を生成し、その修正方法を示しています。

```cpp
// C3828a.cpp
// compile with: /clr
ref struct M {
};

ref struct N {
   static array<char>^ bytes = gcnew array<char>(256);
};

int main() {
   M ^m1 = new (&N::bytes) M();   // C3828
   // The following line fixes the error.
   // M ^m1 = gcnew M();
}
```
