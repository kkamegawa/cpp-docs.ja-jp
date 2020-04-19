---
title: コンパイラの警告 (レベル 1) C4674
ms.date: 11/04/2016
f1_keywords:
- C4674
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
ms.openlocfilehash: b9428a593ff59cbdfa6d8eb369413a560b4a5ad2
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052537"
---
# <a name="compiler-warning-level-1-c4674"></a>コンパイラの警告 (レベル 1) C4674

'method' は宣言された 'static' であり、パラメーターを 1 つだけ持たなければなりません。

変換演算子の署名が正しくありません。 メソッドは、ユーザー定義の変換とは見なされません。 演算子の定義の詳細については、「[ユーザー定義C++演算子 (/cli)](../../dotnet/user-defined-operators-cpp-cli.md) 」および「[ユーザーC++定義変換 (/cli)](../../dotnet/user-defined-conversions-cpp-cli.md)」を参照してください。

## <a name="example"></a>例

次の例では C4674 が生成されます。

```cpp
// C4674.cpp
// compile with: /clr /WX /W1 /LD
ref class G {
   int op_Implicit(int i) {   // C4674
      return 0;
   }
};
```
