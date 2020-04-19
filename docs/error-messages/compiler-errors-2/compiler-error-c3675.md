---
title: コンパイラ エラー C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: 6772572d29765370d6cdbf52ed8470ff2f3f054e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758074"
---
# <a name="compiler-error-c3675"></a>コンパイラ エラー C3675

' function ': ' property ' が定義されているため、予約されています

単純なプロパティを宣言すると、コンパイラは get アクセサーメソッドと set アクセサーメソッドを生成し、これらの名前はプログラムのスコープ内に存在します。  コンパイラによって生成される名前は、get_ を付加し、プロパティ名に set_ することによって形成されます。  そのため、コンパイラによって生成されたアクセサーと同じ名前の関数を宣言することはできません。

詳細については、「 [property](../../extensions/property-cpp-component-extensions.md) 」を参照してください。

## <a name="example"></a>使用例

次の例では、C3675 が生成されます。

```cpp
// C3675.cpp
// compile with: /clr /c
ref struct C {
public:
   property int Size;
   int get_Size() { return 0; }   // C3675
};
```
