---
title: コンパイラの警告 (レベル 3) C4839
ms.date: 09/13/2018
f1_keywords:
- C4839
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
ms.openlocfilehash: 09b6e5b8dc984b35df7de96f5cf8610f2b0f16af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401528"
---
# <a name="compiler-warning-level-3-c4839"></a>コンパイラの警告 (レベル 3) C4839

> クラスの標準でない使用*型*' 可変個引数関数に引数として

クラスまたは構造体などの可変個引数関数に渡される`printf`普通にコピー可能である必要があります。 このようなオブジェクトを渡すときには、コンパイラは単にビットごとのコピーを作成し、コンストラクターまたはデストラクターを呼び出しません。

この警告は、Visual Studio 2017 以降を使用できます。

## <a name="example"></a>例

次の例では、C4839 が生成されます。

```cpp
// C4839.cpp
// compile by using: cl /EHsc /W3 C4839.cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function
}
```

エラーを解決するために、普通にコピー可能な型を返すメンバー関数を呼び出すことができます。

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

構築および管理を使用して文字列`CStringW`、提供された`operator LPCWSTR()`にキャストするために使用する必要があります、`CStringW`オブジェクトを書式設定文字列によって予期されている C ポインターにします。

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```