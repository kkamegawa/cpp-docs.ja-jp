---
title: コンパイラエラー C2017
ms.date: 11/04/2016
f1_keywords:
- C2017
helpviewer_keywords:
- C2017
ms.assetid: 1083eed9-9906-4a97-883c-54e52d7e82cd
ms.openlocfilehash: 3911ef9af2eb0fab7d0f9296ddce8a0f9b32ae0d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751054"
---
# <a name="compiler-error-c2017"></a>コンパイラエラー C2017

無効なエスケープシーケンスです。

\T などのエスケープシーケンスは、文字または文字列定数の外側に出現します。

次の例では、C2017 が生成されます。

```cpp
// C2017.cpp
int main() {
   char test1='a'\n;   // C2017
   char test2='a\n';   // ok
}
```

C2017 は、エスケープシーケンスを含む文字列で stringize 演算子が使用されている場合に発生する可能性があります。

次の例では、C2017 が生成されます。

```cpp
// C2017b.cpp
#define TestDfn(x) AfxMessageBox(#x)
TestDfn(CString("\\") + CString(".h\"\n\n"));   // C2017
```
