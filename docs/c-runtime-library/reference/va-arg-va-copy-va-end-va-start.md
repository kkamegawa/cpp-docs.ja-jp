---
title: va_arg、va_copy、va_end、va_start
ms.date: 11/04/2016
api_name:
- va_arg
- va_end
- va_copy
- va_start
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- va_arg
- va_start
- va_list
- va_alist
- va_dcl
- va_copy
- va_end
helpviewer_keywords:
- variable argument lists, accessing
- va_start macro
- va_arg macro
- va_end macro
- arguments [C++], argument lists
- va_list macro
- va_dcl macro
- va_alist macro
- va_copy macro
ms.assetid: a700dbbd-bfe5-4077-87b6-3a07af74a907
ms.openlocfilehash: 47bd9e3913c6664a52c970dd8a190636683d214e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957359"
---
# <a name="va_arg-va_copy-va_end-va_start"></a>va_arg、va_copy、va_end、va_start

可変個引数リストにアクセスする。

## <a name="syntax"></a>構文

```C
type va_arg(
   va_list arg_ptr,
   type
);
void va_copy(
   va_list dest,
   va_list src
); // (ISO C99 and later)
void va_end(
   va_list arg_ptr
);
void va_start(
   va_list arg_ptr,
   prev_param
); // (ANSI C89 and later)
void va_start(
   arg_ptr
);  // (deprecated Pre-ANSI C89 standardization version)
```

### <a name="parameters"></a>パラメーター

*type*<br/>
取得される引数の型。

*arg_ptr*<br/>
引数リストへのポインター。

*dest*<br/>
*Src*から初期化される引数のリストへのポインター

*src*<br/>
*Dest*にコピーする引数の初期化されたリストへのポインター。

*prev_param*<br/>
最初の省略可能な引数に先行するパラメーター。

## <a name="return-value"></a>戻り値

**va_arg**は、現在の引数を返します。 **va_copy**、 **va_start** 、および**va_end**は値を返しません。

## <a name="remarks"></a>Remarks

**Va_arg**、 **va_copy**、 **va_end**、および**va_start**マクロは、関数が可変個の引数を受け取る場合に、関数の引数に移植可能な方法でアクセスできます。 マクロには、次の2つのバージョンがあります。STDARG.H で定義されているマクロ。H は、ISO C99 標準に準拠しています。VARARGS で定義されているマクロ。H は非推奨とされますが、ANSI C89 標準より前に記述されたコードとの下位互換性のために残されています。

これらのマクロは、関数が固定の個数の必須の引数の後に、省略可能な引数を可変個数受け取るものと想定します。 必須の引数は、関数の通常のパラメーターのように宣言され、パラメーター名でアクセスできます。 省略可能な引数は、STDARG.H (または、ANSI C89 標準以前に書かれたコードの場合は VARARGS.H) のマクロを使用してアクセスします。これらのマクロは、ポインターを引数リストの最初の省略可能な引数へセットし、リストから引数を取得し引数の処理が終了するとポインターをリセットします。

STDARG.H で定義されている C 標準マクロは次のように使用されます。

- **va_start**は、関数に渡される引数のリストの最初の省略可能な引数に*arg_ptr*を設定します。 引数*arg_ptr*には**va_list**型を指定する必要があります。 引数*prev_param*は、引数リストの最初の省略可能な引数の直前にある必須パラメーターの名前です。 *Prev_param*が register ストレージクラスを使用して宣言されている場合、マクロの動作は定義されていません。 **va_arg**を初めて使用する場合は、 **va_start**を使用する必要があります。

- **va_arg**は、 *arg_ptr*によって指定された場所から*型*の値を取得し、 *arg_ptr*をインクリメントして、次の引数の開始位置を決定するために*型*のサイズを使用して、リスト内の次の引数を指すようにします。 **va_arg**は、関数内で任意の回数だけ使用して、リストから引数を取得できます。

- **va_copy**は、現在の状態で引数のリストのコピーを作成します。 *Src*パラメーターは、 **va_start**を使用して既に初期化されている必要があります。**va_arg**の呼び出しで更新されている可能性がありますが、 **va_end**でリセットされていない必要があります。 *Dest*から**va_arg**によって取得される次の引数は、 *src*から取得される次の引数と同じです。

- すべての引数を取得した後、 **va_end**はポインターを**NULL**にリセットします。 関数が返される前に、 **va_start**または**va_copy**で初期化された各引数リストで**va_end**を呼び出す必要があります。

> [!NOTE]
> VARARGS.H のマクロは非推奨とされており、C89 ANSI 規格以前に作成されたコードとの下位互換性のためだけに残されています。 それ以外の場合は、STDARGS.H のマクロを使用します。

これらのマクロを使用するプログラムを [/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md) でコンパイルすると、ネイティブ言語ランタイムと共通言語ランタイム (CLR) の型システムの違いにために予期しない結果が発生することがあります。 次のプログラムを検討します。

```C
#include <stdio.h>
#include <stdarg.h>

void testit (int i, ...)
{
    va_list argptr;
    va_start(argptr, i);

    if (i == 0)
    {
        int n = va_arg(argptr, int);
        printf("%d\n", n);
    }
    else
    {
        char *s = va_arg(argptr, char*);
        printf("%s\n", s);
    }

    va_end(argptr);
}

int main()
{
    testit(0, 0xFFFFFFFF); // 1st problem: 0xffffffff is not an int
    testit(1, NULL);       // 2nd problem: NULL is not a char*
}
```

**Testit**は、2番目のパラメーターを**int**または**char**<strong>\*</strong>にする必要があることに注意してください。 渡される引数は、0xffffffff ( **int**ではなく**符号なし** **整数**) および**NULL** (実際には**char**<strong>\*</strong>ではなく**int**) です。 ネイティブ コードの場合にプログラムをコンパイルすると、次の出力が生成されます。

```Output
-1

(null)
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<stdio.h> および \<stdarg.h>

**非推奨のヘッダー:** \<varargs.h&gt;

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_va.c
// Compile with: cl /W3 /Tc crt_va.c
// The program below illustrates passing a variable
// number of arguments using the following macros:
//      va_start            va_arg              va_copy
//      va_end              va_list

#include <stdio.h>
#include <stdarg.h>
#include <math.h>

double deviation(int first, ...);

int main( void )
{
    /* Call with 3 integers (-1 is used as terminator). */
    printf("Deviation is: %f\n", deviation(2, 3, 4, -1 ));

    /* Call with 4 integers. */
    printf("Deviation is: %f\n", deviation(5, 7, 9, 11, -1));

    /* Call with just -1 terminator. */
    printf("Deviation is: %f\n", deviation(-1));
}

/* Returns the standard deviation of a variable list of integers. */
double deviation(int first, ...)
{
    int count = 0, i = first;
    double mean = 0.0, sum = 0.0;
    va_list marker;
    va_list copy;

    va_start(marker, first);     /* Initialize variable arguments. */
    va_copy(copy, marker);       /* Copy list for the second pass */
    while (i != -1)
    {
        sum += i;
        count++;
        i = va_arg(marker, int);
    }
    va_end(marker);              /* Reset variable argument list. */
    mean = sum ? (sum / count) : 0.0;

    i = first;                  /* reset to calculate deviation */
    sum = 0.0;
    while (i != -1)
    {
        sum += (i - mean)*(i - mean);
        i = va_arg(copy, int);
    }
    va_end(copy);               /* Reset copy of argument list. */
    return count ? sqrt(sum / count) : 0.0;
}
```

```Output
Deviation is: 0.816497
Deviation is: 2.236068
Deviation is: 0.000000
```

## <a name="see-also"></a>関連項目

[引数へのアクセス](../../c-runtime-library/argument-access.md)<br/>
[vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)<br/>
