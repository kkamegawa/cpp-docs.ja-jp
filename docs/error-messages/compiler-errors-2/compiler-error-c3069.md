---
title: コンパイラ エラー C3069
ms.date: 11/04/2016
f1_keywords:
- C3069
helpviewer_keywords:
- C3069
ms.assetid: ca94291b-2bb4-4e3f-9acf-534234b83513
ms.openlocfilehash: 230d2569ea314bde2ea9ef0c4fc58d1a9743807f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749517"
---
# <a name="compiler-error-c3069"></a>コンパイラ エラー C3069

'operator': 列挙型には使用できません

演算子は CLR 列挙体ではサポートされていません。  詳細については、「[方法:/cli でC++列挙型を定義および使用する](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

次の例では C3069 が生成されます。

```cpp
// C3069.cpp
// compile with: /clr
enum struct E { e1 };
enum F { f1 };

int main() {
   E e = E::e1;
   bool tf;
   tf = !e;   // C3069

   // supported for native enums
   F f = f1;
   tf = !f;
}
```
