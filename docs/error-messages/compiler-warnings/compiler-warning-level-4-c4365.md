---
title: コンパイラの警告 (レベル 4) C4365
ms.date: 11/04/2016
f1_keywords:
- C4365
helpviewer_keywords:
- C4365
ms.assetid: af4b4191-bdfd-4dbb-8229-3ba4405df257
ms.openlocfilehash: a9be67c8148b85167d10cd53318f5ef3b41b1340
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990925"
---
# <a name="compiler-warning-level-4-c4365"></a>コンパイラの警告 (レベル 4) C4365

' action ': ' type_1 ' から ' type_2 ' への変換、符号付き/符号なしの不一致

たとえば、符号なしの値を符号付きの値に変換しようとしたとします。

C4365 は既定ではオフになっています。  詳細については、「 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C4365 が生成されます。

```cpp
// C4365.cpp
// compile with: /W4
#pragma warning(default:4365)

int f(int) { return 0; }
void Test(size_t i) {}

int main() {
   unsigned int n = 10;
   int o = 10;
   n++;
   f(n);   // C4365
   f(o);   // OK

   Test( -19 );   // C4365
}
```
