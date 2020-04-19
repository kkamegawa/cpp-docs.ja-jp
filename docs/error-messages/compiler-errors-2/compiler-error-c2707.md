---
title: コンパイラエラー C2707
ms.date: 11/04/2016
f1_keywords:
- C2707
helpviewer_keywords:
- C2707
ms.assetid: 3deaf45c-74da-4c9d-acc6-b82412720b74
ms.openlocfilehash: e29812563ef1d4d7f6612ea2516f2f6327e90e1b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760440"
---
# <a name="compiler-error-c2707"></a>コンパイラエラー C2707

' identifier ': 組み込み関数のコンテキストが正しくありません

構造化例外処理の組み込みは、特定のコンテキストでは無効です。

- 例外フィルターまたは `__except` ブロックの外部 `_exception_code()`

- 例外フィルターの外部 `_exception_info()`

- `__finally` ブロックの外側 `_abnormal_termination()`

このエラーを解決するには、例外処理の組み込みが適切なコンテキストに配置されていることを確認してください。

## <a name="example"></a>使用例

次の例では、C2707 が生成されます。

```cpp
// C2707.cpp
#include <windows.h>
#include <stdio.h>

LONG MyFilter(LONG excode)
{
    return (excode == EXCEPTION_ACCESS_VIOLATION ?
        EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);   // OK
}

LONG func(void)
{
    int x, y;
    return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ?  // C2707
             EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);

    __try
    {
        y = 0;
        x = 4 / y;
        return 0;
     }

    __except(MyFilter(GetExceptionCode()))
    {
        return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ? // ok
               EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);
    }
}

int main()
{
    __try
    {
        func();
    } __except(EXCEPTION_EXECUTE_HANDLER)
    {
        printf_s("Caught exception\n");
    }
}
```
