---
title: 関数呼び出し
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
ms.openlocfilehash: 2402f3fef77b19c0420f0c4a52407a730b53b1d5
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148206"
---
# <a name="function-calls"></a>関数呼び出し

*関数呼び出し*は、制御と引数 (存在する場合) を関数に渡す式であり、形式は以下の通りです。

*expression* (*expression-list*<sub>opt</sub>)

ここで、*expression* は関数名または評価して関数アドレスになる式で、*expression-list* は式のリストです (コンマ区切り)。 これらの式の値は、関数に渡された引数です。 関数が値を返さない場合は、`void` を返す関数として宣言します。

関数呼び出しの前に宣言が存在していて、パラメーターに関する情報が何もない場合は、宣言されていない引数に対して単純に通常の算術変換が実行されます。

> [!NOTE]
>  関数の引数リストの式は、任意の順序で評価できるため、別の引数の副作用によって値が変化する可能性のある引数は値が未定義になります。 関数呼び出し演算子で定義されたシーケンス ポイントは、呼び出された関数に制御が渡される前に引数リストのすべての副作用が評価されることだけを保証します  (引数をスタックにプッシュする順序は別の問題です)。詳細については、「[シーケンス ポイント](../c-language/c-sequence-points.md)」を参照してください。

関数呼び出しの唯一の要件は、かっこの前の式を評価すると関数アドレスになることです。 これは、関数を任意の関数ポインター式を使用して呼び出せることを意味します。

## <a name="example"></a>例

この例では `switch` ステートメントから呼び出された関数呼び出しを示しています。

```
int main()
{
    /* Function prototypes */

    long lift( int ), step( int ), drop( int );
    void work( int number, long (*function)(int i) );

    int select, count;
    .
    .
    .
    select = 1;
    switch( select )
    {
        case 1: work( count, lift );
                break;

        case 2: work( count, step );
                break;

        case 3: work( count, drop );
                /* Fall through to next case */
        default:
                break;
    }
}

/* Function definition */

void work( int number, long (*function)(int i) )
{
    int i;
    long j;

    for ( i = j = 0; i < number; i++ )
            j += ( *function )( i );
}
```

この例では、`main` 内の関数呼び出しである

```
work( count, lift );
```

は整数変数 `count` と関数 `lift` のアドレスを関数 `work` に渡します。 関数識別子を評価するとポインター式になるため、関数識別子を指定するだけで関数アドレスが渡されることに注意してください。 関数識別子をこのように使用するには、識別子を使用する前に関数を宣言または定義している必要があります。それ以外の場合、識別子は認識されません。 この場合、`work` のプロトタイプは `main` 関数の先頭で与えられています。

`function` のパラメーター `work` は、`int` の引数を 1 つ受け取り、**long** 値を返す関数へのポインターとして宣言されます。 パラメーター名を囲むかっこは必須です。かっこがないと、この宣言では **long** 値へのポインターを返す関数が指定されます。

関数 `work` は、次の関数呼び出しを使用して **for** ループ内から選択した関数を呼び出します。

```
( *function )( i );
```

1 つの引数 `i` は、呼び出された関数に渡されます。

## <a name="see-also"></a>関連項目

[関数](../c-language/functions-c.md)
