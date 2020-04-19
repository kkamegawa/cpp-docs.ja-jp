---
title: コンパイラの警告 (レベル 1) C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: 617cb2cc3774b288581a3868125ced19b28ba45a
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966507"
---
# <a name="compiler-warning-level-1-c4369"></a>コンパイラの警告 (レベル 1) C4369

' enumerator ': 列挙子の値 ' value ' を ' type ' として表すことはできません。値は ' new_value ' です

列挙子が、指定された基になる型の最大値を超えていることが計算されました。  これによりオーバーフローが発生し、コンパイラが列挙子の値をその型の可能な最小値にラップしました。

## <a name="example"></a>例

次の例では、C4369 が生成されます。

```cpp
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```