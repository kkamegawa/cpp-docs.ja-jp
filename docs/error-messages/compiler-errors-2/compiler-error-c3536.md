---
title: コンパイラ エラー C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: a140847b642ac2437b67aa957328c3b8fbfc592d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761570"
---
# <a name="compiler-error-c3536"></a>コンパイラ エラー C3536

' symbol ': 初期化する前に使用することはできません

指定されたシンボルを初期化する前に使用することはできません。 実際には、変数はその変数自体を初期化するために使用できないことを意味します。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. 変数をそれ自体で初期化しないでください。

## <a name="example"></a>使用例

次の例では、各変数がそれ自体で初期化されるため、C3536 が生成されます。

```cpp
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>参照

[auto キーワード](../../cpp/auto-keyword.md)
