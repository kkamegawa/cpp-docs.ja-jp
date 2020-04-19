---
title: while ステートメント (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 669618e9807109be18117968b1f5b6f49ec15e07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325417"
---
# <a name="while-statement-c"></a>while ステートメント (C++)

実行*ステートメント*まで繰り返し*式*0 に評価します。

## <a name="syntax"></a>構文

```
while ( expression )
   statement
```

## <a name="remarks"></a>Remarks

テスト*式*ループの各実行前に、の処理を行うのため、**while**ループは 0 回以上を実行します。 *式*の整数型、ポインター型、または整数への明確な変換を持つクラス型またはポインター型である必要があります。

**while**ループがときに終了することできますも、 [break](../cpp/break-statement-cpp.md)、 [goto](../cpp/goto-statement-cpp.md)、または[を返す](../cpp/return-statement-cpp.md)ステートメント本体が実行されます。 使用[続行](../cpp/continue-statement-cpp.md)を終了する前に、現在のイテレーションを終了する、**while**ループします。 **continue**の次のイテレーションに制御を渡します、**while**ループします。

次のコードでは、**while**文字列から末尾をトリミングするループがアンダー スコアします。

```cpp
// while_statement.cpp

#include <string.h>
#include <stdio.h>
char *trim( char *szSource )
{
    char *pszEOS = 0;

    //  Set pointer to character before terminating NULL
    pszEOS = szSource + strlen( szSource ) - 1;

    //  iterate backwards until non '_' is found
    while( (pszEOS >= szSource) && (*pszEOS == '_') )
        *pszEOS-- = '\0';

    return szSource;
}
int main()
{
    char szbuf[] = "12345_____";

    printf_s("\nBefore trim: %s", szbuf);
    printf_s("\nAfter trim: %s\n", trim(szbuf));
}
```

終了条件はループの先頭で評価されます。 末尾のアンダースコアがない場合、ループは実行されません。

## <a name="see-also"></a>関連項目

[繰り返しステートメント](../cpp/iteration-statements-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)<br/>
[do-while ステートメント (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for ステートメント (C++)](../cpp/for-statement-cpp.md)<br/>
[範囲ベースの for ステートメント (C++)](../cpp/range-based-for-statement-cpp.md)