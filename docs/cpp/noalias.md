---
title: noalias
ms.date: 02/09/2018
f1_keywords:
- noalias_cpp
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
ms.openlocfilehash: 2eceffd10f97615859918991320ceebf577d094c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377440"
---
# <a name="noalias"></a>noalias

**Microsoft 固有の仕様**

**noalias**関数呼び出しの変更または表示されるグローバル状態の参照はないことを意味のみが指すメモリを変更し、*直接*ポインター パラメーター (第 1 レベルの間接指定)。

関数は、注釈が付けられている場合**noalias**オプティマイザーは、パラメーター自体に加えてポインター パラメーターのだけ最初のレベルの間接指定が参照または変更された関数内で想定できます。 表示されるグローバル状態は、コンパイルのスコープ外では、アドレスは取られません定義または参照されていないすべてのデータの設定です。 コンパイル スコープは、すべてのソース ファイル ([/LTCG (リンク時コード生成)](../build/reference/ltcg-link-time-code-generation.md)ビルド) または 1 つのソース ファイル (非 **/LTCG**ビルド)。

**Noalias**注釈は、注釈付きの関数の本体でのみ適用されます。 関数としてマーク**内**関数によって返されるポインターのエイリアスには影響しません。

エイリアスに影響するもう 1 つの注釈を参照してください。 [__declspec(restrict)](../cpp/restrict.md)します。

## <a name="example"></a>例

次の例では、使用**内**します。

ときに、関数`multiply`アクセスのメモリの注釈が付けられている**内**、この関数がパラメーター リストでポインターを通じてを除くグローバル状態を変更しないことをコンパイラに伝えます。

```C
// declspec_noalias.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1/k++;
    return a;
}

__declspec(noalias) void multiply(float * a, float * b, float * c)
{
    int i, j, k;

    for (j=0; j<P; j++)
        for (i=0; i<M; i++)
            for (k=0; k<N; k++)
                c[i * P + j] =
                          a[i * N + k] *
                          b[k * P + j];
}

int main()
{
    float * a, * b, * c;

    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));

    if (!mempool)
    {
        puts("ERROR: Malloc returned null");
        exit(1);
    }

    memptr = mempool;
    a = init(M, N);
    b = init(N, P);
    c = init(M, P);

    multiply(a, b, c);
}
```

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)<br/>
[__declspec(restrict)](../cpp/restrict.md)
