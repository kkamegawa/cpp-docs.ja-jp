---
title: 引数
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- functions [C], parameters
- function parameters, about function parameters
- function arguments
- function calls, arguments
ms.assetid: 14cf0389-2265-41f0-9a96-f2223eb406ca
ms.openlocfilehash: e60a7935cdddc116848b64461b064c5fd5cdd00a
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148726"
---
# <a name="arguments"></a>引数

関数呼び出しの引数は次の形式です。

> *expression* **(** *expression-list*<SUB>opt</SUB> **)**  /* 関数呼び出し */

関数呼び出しでは、*expression-list* は式のリストです (コンマで区切られます)。 これらの式の値は、関数に渡された引数です。 関数に引数がない場合は、*expression-list* に `void` キーワードを含める必要があります。

引数は、基本型、構造体型、共用体型、またはポインター型の任意の値を指定できます。 すべての引数は値渡しされます。 つまり、引数のコピーが、該当するパラメーターに代入されます。 関数に渡される引数の実際のメモリ位置は特定できません。 関数はこのコピーを使用し、元の変数には影響を与えません。

配列または関数を引数として渡すことはできませんが、これらの項目へのポインターは渡すことができます。 関数は、ポインターを介して参照によって値にアクセスできます。 変数へのポインターは変数のアドレスを保持するため、関数はこのアドレスを使用して変数の値にアクセスできます。 配列と関数を引数として渡すことはできませんが、ポインター引数により関数は配列および関数にアクセスできます。

引数の評価順序は、コンパイラごとに、最適化レベルことに異なる場合があります。 ただし、関数に入る前に、引数と副作用は完全に評価されます。 副作用の詳細については、「[副作用](../c-language/side-effects.md)」を参照してください。

関数呼び出しの *expression-list* が評価され、通常の算術変換が関数呼び出しの各引数に対して実行されます。 プロトタイプを使用できる場合は、結果の引数の型がプロトタイプの対応するパラメーターと比較されます。 一致しない場合は、変換が実行されるか、診断メッセージが発行されます。 パラメーターには、通常の算術変換も実行されます。

*expression-list* の式の数は、パラメーターの数と一致する必要があります。ただし、関数のプロトタイプまたは定義で明示的に可変個の引数を指定している場合は除きます。 この場合、コンパイラはパラメーター リストの型名の数だけ引数をチェックし、必要に応じて、それを上記のように変換します。 詳細については、「[可変数の引数を使用した呼び出し](../c-language/calls-with-a-variable-number-of-arguments.md)」をご覧ください。

プロトタイプのパラメーター リストが `void` キーワードのみを含む場合、コンパイラは関数呼び出しの引数はゼロで、関数定義のパラメーターはゼロであると想定します。 引数が存在する場合は、診断メッセージが発行されます。

## <a name="example"></a>例

この例では、引数としてポインターを使っています。

```C
int main()
{
    /* Function prototype */

    void swap( int *num1, int *num2 );
    int x, y;
    .
    .
    .
    swap( &x, &y );  /* Function call */
}

/* Function definition */

void swap( int *num1, int *num2 )
{
    int t;

    t = *num1;
    *num1 = *num2;
    *num2 = t;
}
```

この例では、`swap` で、`main` 関数が引数を 2 つ持ち、それぞれが識別子 `num1` と `num2` で表され、どちらも `int` 値へのポインターであることが宣言されています。 プロトタイプ式の定義のパラメーター `num1` と `num2` も、`int` 型の値へのポインターとして宣言されます。

次の関数呼び出しでは

```C
swap( &x, &y )
```

`x` のアドレスが `num1` に格納され、`y` のアドレスが `num2` に格納されます。 ここでは同じ場所に 2 つの名前、つまり "エイリアス" が存在しています。 `*num1` での `*num2` と `swap` への参照は、実質的に `x` の `y` と `main` への参照です。 `swap` 内での代入は、実際に `x` と `y` の内容を交換します。 したがって、`return` ステートメントは不要です。

コンパイラは、`swap` のプロトタイプに各パラメーターの引数型が含まれるため、`swap` の引数の型チェックを実行します。 プロトタイプと定義のかっこ内の識別子は、同じでも異なっていてもかまいません。 重要なのは、プロトタイプと定義の両方で引数の型がパラメーター リストの型と一致することです。

## <a name="see-also"></a>関連項目

[関数呼び出し](../c-language/function-calls.md)
