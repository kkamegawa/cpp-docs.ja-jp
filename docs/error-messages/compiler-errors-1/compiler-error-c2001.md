---
title: コンパイラエラー C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 2bf9bd322812764b2f63493d4b22b58d853a25fa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756839"
---
# <a name="compiler-error-c2001"></a>コンパイラエラー C2001

定数の改行

次の操作を行わない限り、文字列定数は2行目で続けることはできません。

- 最初の行の末尾に円記号を付けます。

- 最初の行で二重引用符で囲まれた文字列を閉じ、次の行の文字列をもう1つの二重引用符で開きます。

\N で最初の行を終了するだけでは十分ではありません。

## <a name="example"></a>使用例

次の例では、C2001 が生成されます。

```cpp
// C2001.cpp
// C2001 expected
#include <stdio.h>

int main()
{
    printf_s("Hello,
             world");
    printf_s("Hello,\n
             world");
}
```

## <a name="example"></a>使用例

文字列定数には、行連結文字の後の次の行の先頭にあるスペースが含まれます。 上の例では、文字列定数に改行文字が埋め込まれていません。 次に示すように、改行文字を埋め込むことができます。

```cpp
// C2001b.cpp
#include <stdio.h>

int main()
{
    printf_s("Hello,\n\
             world");

    printf_s("Hello,\
             \nworld");

    printf_s("Hello,\n"
             "world");

    printf_s("Hello,"
             "\nworld");

    printf_s("Hello,"
             " world");

    printf_s("Hello,\
             world");
}
```
