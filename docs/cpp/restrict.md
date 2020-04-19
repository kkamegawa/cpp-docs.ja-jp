---
title: restrict
ms.date: 02/09/2018
f1_keywords:
- restrict_cpp
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
ms.openlocfilehash: 40c1c05ca72f639829f2d3658497b0e9f3199640
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403374"
---
# <a name="restrict"></a>restrict

**Microsoft 固有の仕様**

関数宣言または定義を返す、ポインター型に適用すると**制限**関数によって返されるオブジェクトでないことをコンパイラに指示*別名*、によってその他の参照は、ポインター。 これにより、コンパイラがその他の最適化を実行できます。

## <a name="syntax"></a>構文

> **__declspec(restrict)** *pointer_return_type* *function*();

## <a name="remarks"></a>Remarks

コンパイラの伝達 **__declspec(restrict)** します。 たとえば、CRT`malloc`関数を **__declspec(restrict)** 装飾、およびそのため、コンパイラは、メモリの場所にポインターが初期化されることを想定しています`malloc`されてもいないエイリアスになって以前既存のポインター。

コンパイラでは、返されたポインターが実際には別名ではありませんはチェックしません。 プログラムにエイリアスがないとマークされているポインターの開発者の責任は、 **_ _declspec を制限する**修飾子。

変数によく似たセマンティクスは、次を参照してください。 [_ _restrict](../cpp/extension-restrict.md)します。

関数内のエイリアスに適用される別の注釈を参照してください。[内](../cpp/noalias.md)します。

については、**制限**キーワードは C++ AMP の一部であるを参照してください[制限 (C++ AMP)](../cpp/restrict-cpp-amp.md)します。

## <a name="example"></a>例

次の例では、使用 **__declspec(restrict)** します。

ときに **__declspec(restrict)** いるポインターを返す、これにより、コンパイラ、戻り値が指すメモリがエイリアス化されないことを関数に適用されます。 この例では、ポインターで`mempool`と`memptr`、グローバルには、コンパイラを参照しているメモリがエイリアス化されないことを確認することはできません。 ただし、内で使用された`ma`とその呼び出し元`init`をそれ以外の場合から参照されていない、プログラムでは、そのためメモリを返す方法で **__decslpec(restrict)** オプティマイザーに使用されます。 これは、どの割り当て関数の装飾、CRT ヘッダーなどのような`malloc`を使用して **__declspec(restrict)** を既存のポインターによって別名を設定できませんメモリを返す常にします。

```C
// declspec_restrict.c
// Compile with: cl /W4 declspec_restrict.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

__declspec(restrict) float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

__declspec(restrict) float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1f/k++;
    return a;
}

void multiply(float * a, float * b, float * c)
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

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)<br/>
[__declspec](../cpp/declspec.md)<br/>
[__declspec(noalias)](../cpp/noalias.md)
