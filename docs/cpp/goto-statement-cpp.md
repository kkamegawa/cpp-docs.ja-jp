---
title: goto ステートメント (C++)
ms.date: 11/04/2016
f1_keywords:
- goto_cpp
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
ms.openlocfilehash: aac308905a01a52a4ce5ee0fa3be03f2f33ac1cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153698"
---
# <a name="goto-statement-c"></a>goto ステートメント (C++)

**Goto**ステートメントは無条件で指定した識別子によってラベル付けステートメントに制御を転送します。

## <a name="syntax"></a>構文

```
goto identifier;
```

## <a name="remarks"></a>Remarks

`identifier` で指定されたラベル付きステートメントは、現在の関数内にある必要があります。 すべての `identifier` 名は内部の名前空間のメンバーであるため、他の識別子と干渉することはありません。

ステートメント ラベルにのみ意味のある、 **goto**ステートメントです。 それ以外の場合、ステートメント ラベルは無視されます。 ラベルは再宣言できません。

A **goto**コントロールをその場所にスコープ内の任意の変数の初期化をスキップする場所に移動するステートメントが許可されていません。 次の例では、C2362 が発生します。

```cpp
int goto_fn(bool b)
{
    if (!b)
    {
        goto exit;  // C2362
    }
    else
    { /*...*/ }

    int error_code = 42;

exit:
    return error_code;
}
```

使用するスタイルのプログラミングをお勧め、 **break**、**continue**と**return**ステートメントの代わりに、 **goto**ステートメントたびに考えられる。 ただし、ため、 **break**ステートメント、ループの 1 つだけのレベルから抜けるを使用する必要があります、 **goto**深く入れ子になったループを終了するステートメント。

ラベルの詳細については、 **goto**ステートメントを参照してください[ラベル付きステートメント](../cpp/labeled-statements.md)します。

## <a name="example"></a>例

この例で、 **goto**ステートメントに制御というラベルの位置を転送`stop`とき`i`が 3 に等しい。

```cpp
// goto_statement.cpp
#include <stdio.h>
int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 2; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 3 )
                goto stop;
        }
    }

    // This message does not print:
    printf_s( "Loop exited. i = %d\n", i );

    stop:
    printf_s( "Jumped to stop. i = %d\n", i );
}
```

```Output
Outer loop executing. i = 0
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 1
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 2
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 3
Inner loop executing. j = 0
Jumped to stop. i = 3
```

## <a name="see-also"></a>関連項目

[ジャンプ ステートメント](../cpp/jump-statements-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)
