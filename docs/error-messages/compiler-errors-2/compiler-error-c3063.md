---
title: コンパイラ エラー C3063
ms.date: 11/04/2016
f1_keywords:
- C3063
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
ms.openlocfilehash: c52a0a4c4255eeed5f49a7e6c1e86a1f64b8ad77
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755656"
---
# <a name="compiler-error-c3063"></a>コンパイラ エラー C3063

演算子 ' operator ': すべてのオペランドには、同じ列挙型を指定しなければなりません

列挙子に対して演算子を使用する場合、両方のオペランドが列挙型である必要があります。 詳細については、「[方法:/cli でC++列挙型を定義および使用する](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3063 を生成し、その修正方法を示しています。

```cpp
// C3063.cpp
// compile with: /clr
enum class E { a, b } e, mask;
int main() {
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)

   if ( ( e & mask ) != E() )   // OK
      ;
}
```
