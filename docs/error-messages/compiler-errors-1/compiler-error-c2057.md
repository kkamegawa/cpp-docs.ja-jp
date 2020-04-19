---
title: コンパイラエラー C2057
ms.date: 11/04/2016
f1_keywords:
- C2057
helpviewer_keywords:
- C2057
ms.assetid: 038a99d6-1f5a-42fa-8449-03b4ff11ee0b
ms.openlocfilehash: 1c873a0ba956adedea3311ac8e1844a629caa44b
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302030"
---
# <a name="compiler-error-c2057"></a>コンパイラエラー C2057

定数式が必要です。

コンテキストには、コンパイル時に値が認識される定数式が必要です。

コンパイラは、型のインスタンスに領域を割り当てるため、コンパイル時にその型のサイズを認識する必要があります。

## <a name="example"></a>使用例

次の例では、C2057 を生成し、その修正方法を示しています。

```cpp
// C2057.cpp
int i;
int b[i];   // C2057 - value of i is unknown at compile time
int main() {
   const int i = 8;
   int b[i]; // OK - value of i is fixed and known to compiler
}
```

## <a name="example"></a>使用例

C 言語の定数式には、より制限の厳しい規則があります。  次の例では、C2057 を生成し、その修正方法を示しています。

```c
// C2057b.c
#define ArraySize1 10
int main() {
   const int ArraySize2 = 10;
   int h[ArraySize2];   // C2057 - C does not allow variables here
   int h[ArraySize1];   // OK - uses preprocessor constant
}
```
