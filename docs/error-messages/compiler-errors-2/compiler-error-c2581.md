---
title: コンパイラ エラー C2581
ms.date: 11/04/2016
f1_keywords:
- C2581
helpviewer_keywords:
- C2581
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
ms.openlocfilehash: 03fc7e9da8a9b3a2e2c445f5b06395c2616f0d98
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755435"
---
# <a name="compiler-error-c2581"></a>コンパイラ エラー C2581

' type ': 静的 ' operator = ' 関数は無効です

代入 (`=`) 演算子が `static`として正しく宣言されていません。 代入演算子を `static`にすることはできません。 詳細については、「[ユーザー定義のC++演算子 (/cli)](../../dotnet/user-defined-operators-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C2581 が生成されます。

```cpp
// C2581.cpp
// compile with: /clr /c
ref struct Y {
   static Y ^ operator = (Y^ me, int i);   // C2581
   Y^ operator =(int i);   // OK
};
```
