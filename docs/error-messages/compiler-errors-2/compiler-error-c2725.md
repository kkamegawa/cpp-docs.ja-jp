---
title: コンパイラエラー C2725
ms.date: 11/04/2016
f1_keywords:
- C2725
helpviewer_keywords:
- C2725
ms.assetid: 13cd5b1b-e906-4cd8-9b2b-510d587c665a
ms.openlocfilehash: 5df5a94e32e3cb365166fc38c5df10c248138277
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756410"
---
# <a name="compiler-error-c2725"></a>コンパイラエラー C2725

'exception' : 値または参照によってマネージド オブジェクトまたは WinRT オブジェクトをスローまたはキャッチできません

マネージド例外または WinRT 例外の型が正しくありません。

## <a name="example"></a>使用例

次の例では、C2725 を生成し、その修正方法を示しています。

```cpp
// C2725.cpp
// compile with: /clr
ref class R {
public:
   int i;
};

int main() {
   R % r1 = *gcnew R;
   throw r1;   // C2725

   R ^ r2 = gcnew R;
   throw r2;   // OK
}
```

## <a name="example"></a>使用例

次の例では、C2725 を生成し、その修正方法を示しています。

```cpp
// C2725b.cpp
// compile with: /clr
using namespace System;
int main() {
   try {}
   catch( System::Exception%) {}   // C2725
   // try the following line instead
   // catch( System::Exception ^e) {}
}
```
