---
title: コンパイラの警告 (レベル 1) C4627
ms.date: 09/09/2018
f1_keywords:
- C4627
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
ms.openlocfilehash: 06db3d7e585dfe49b2e0854973f63834648613b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221379"
---
# <a name="compiler-warning-level-1-c4627"></a>コンパイラの警告 (レベル 1) C4627

> '*header_file*': プリコンパイル済みヘッダーの使用を検索するときにスキップ

現在のソース ファイルがある場合、 [/Yu\(プリコンパイル済みヘッダー ファイルを使用して)](../../build/reference/yu-use-precompiled-header-file.md)コンパイラでは、ファイル内のすべてが無視されるプリコンパイル済みヘッダーが含まれる前に、セット オプションします。 警告**C4627**場合に、Visual Studio 2015 と以前のバージョンで生成された*header_file*前、プリコンパイル済みヘッダー ファイルに含まれていることも、プリコンパイル済みヘッダーにが含まれていない場合、*header_file*します。

## <a name="example"></a>例

このサンプルでは、エラーの発生する可能性が、その修正方法を示しています。

```cpp
// c4627.cpp
#include <iostream>       // C4627 - iostream not included by pch.h
#include "pch.h"          // precompiled header file that does not include iostream
// #include <iostream>    // To fix, move the iostream header include here from above
int main()
{
    std::cout << "std::cout is defined!\n";
}
```

## <a name="see-also"></a>関連項目

[プリコンパイル済みヘッダー ファイルの作成](../../build/creating-precompiled-header-files.md)
