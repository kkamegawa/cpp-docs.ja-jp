---
title: コンパイラ エラー C2004
ms.date: 11/04/2016
f1_keywords:
- C2004
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
ms.openlocfilehash: b781e9f81342f35d66eca222bd338252b739096c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737492"
---
# <a name="compiler-error-c2004"></a>コンパイラ エラー C2004

'defined (id)' の形式にしてください。

プリプロセッサのキーワードに続く識別子は、かっこで囲む必要があります。

このエラーは、Visual Studio .NET 2003 でコンパイラ準拠作業が実施された結果、生成されることもあります。プリプロセッサ ディレクティブにかっこがありません。 プリプロセッサ ディレクティブに閉じかっこがない場合は、コンパイラによってエラーが生成されます。

## <a name="example"></a>使用例

次の例では C2004 が生成されます。

```cpp
// C2004.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG   // C2004
        printf_s("DEBUG defined\n");
    #endif
}
```

## <a name="example"></a>使用例

解決方法:

```cpp
// C2004b.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG)
        printf_s("DEBUG defined\n");
    #endif
}
```
