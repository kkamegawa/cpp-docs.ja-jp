---
title: return ステートメント (C)
ms.date: 11/04/2016
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
ms.openlocfilehash: c3975076ee65d267f3d278e20a7770e6750c06d3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148986"
---
# <a name="return-statement-c"></a>return ステートメント (C)

`return` ステートメントは、関数の実行を終了し、コントロールを呼び出し元の関数に戻します。 呼び出し直後の位置から、呼び出し元の関数で実行が再開します。 `return` ステートメントは、呼び出し元の関数に値を返すこともできます。 詳細については、「[戻り値の型](../c-language/return-type.md)」をご覧ください。

## <a name="syntax"></a>構文

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**return** *expression*<sub>opt</sub> **;**

*expression* の値 (存在する場合) が呼び出し元の関数に返されます。 *expression* が省略されている場合、関数の戻り値は未定義です。 式が存在する場合は、評価され、関数が返した型に変換されます。 関数が戻り値の型 `void` で宣言されている場合、式を含む `return` ステートメントで警告が生成され、式は評価されません。

`return` ステートメントが関数定義に表示されない場合、呼び出された関数の最後のステートメントが実行された後に、制御が自動的に呼び出し元の関数に戻ります。 この場合、呼び出される関数の戻り値は未定義です。 戻り値が必要ない場合は、`void` の戻り値の型を持つように関数を宣言します。それ以外の場合は、既定の戻り値の型は `int` です。

多くのプログラマはかっこを使用して `return` ステートメントの *expression* 引数を囲みます。 ただし、C では角かっこは必要ありません。

`return` ステートメントの例を次に示します。

```C
#include <limits.h>
#include <stdio.h>

void draw( int i, long long ll );
long long sq( int s );

int main()
{
    long long y;
    int x = INT_MAX;

    y = sq( x );
    draw( x, y );
    return x;
}

long long sq( int s )
{
    // Note that parentheses around the return expression
    // are allowed but not required here.
    return( s * (long long)s );
}

void draw( int i, long long ll )
{
    printf( "i = %d, ll = %lld\n", i, ll );
    return;
}
```

この例では、`main` 関数は、2 つの関数 `sq` と `draw` を呼び出します。 `sq` 関数は `x * x` の値を `main` に返します。戻り値は `y` に割り当てられます。 `sq` の return 式を囲むかっこは、式の一部として評価され、return ステートメントでは必要ありません。 return 式は戻り値の型に変換される前に評価されるため、`sq` は、予期しない結果を招く可能性がある整数オーバーフローを防ぐために、キャストを使用して戻り値の型となるように式の型を強制します。 `draw` 関数は `void` 関数として宣言されています。 これはパラメーターの値を出力し、その後に空の return ステートメントによって関数が終了し、値は返されません。 `draw` の戻り値を割り当てる試みにより、診断メッセージが出力されます。 その後、`main` 関数は、オペレーティング システムに `x` の値を返します。

この例の出力は次のようになります。

```Output
i = 2147483647, ll = 4611686014132420609
```

## <a name="see-also"></a>関連項目

[ステートメント](../c-language/statements-c.md)
