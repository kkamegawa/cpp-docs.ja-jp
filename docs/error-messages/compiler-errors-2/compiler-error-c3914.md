---
title: コンパイラ エラー C3914
ms.date: 11/04/2016
f1_keywords:
- C3914
helpviewer_keywords:
- C3914
ms.assetid: 8f3190e6-ee50-4916-9ecc-3b8748b2e1e7
ms.openlocfilehash: 6f7da67871b5e6b9d7da9a9aa4eebeb761f8cc50
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737999"
---
# <a name="compiler-error-c3914"></a>コンパイラ エラー C3914

既定のプロパティを静的にすることはできません

既定のプロパティが正しく宣言されていません。  詳細については、「[方法:/cli でC++プロパティを使用](../../dotnet/how-to-use-properties-in-cpp-cli.md)する」を参照してください。

## <a name="example"></a>使用例

次の例では、C3914 を生成し、その修正方法を示しています。

```cpp
// C3914.cpp
// compile with: /clr /c
ref struct X {
   static property int default[int] {   // C3914
   // try the following line instead
   // property int default[int] {
      int get(int) { return 0; }
      void set(int, int) {}
   }
};
```
