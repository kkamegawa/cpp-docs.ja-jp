---
title: コンパイラエラー C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: 83b78336d74037b9f9f52da8327479f506db1ffc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751072"
---
# <a name="compiler-error-c2015"></a>コンパイラエラー C2015

定数に文字が多すぎます

文字定数に3文字以上が含まれています。 制限は、標準文字定数の場合は1文字、長い文字定数の場合は2文字です。

エスケープシーケンス (\t など) は、1つの文字に変換されます。

## <a name="example"></a>使用例

次の例では、C2015 が生成されます。

```cpp
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

## <a name="example"></a>使用例

C2015 は、Microsoft 拡張機能、文字定数を整数に変換して使用する場合にも発生します。  次の例では、C2015 が生成されます。

```cpp
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```
