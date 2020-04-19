---
title: _malloca
ms.date: 11/04/2016
api_name:
- _malloca
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
- malloca
- _malloca
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
ms.openlocfilehash: 0b12b4adde710f2fc46b3a3790519006fabbb1fc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952775"
---
# <a name="_malloca"></a>_malloca

スタックにメモリを割り当てます。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [_alloca](alloca.md) です。

## <a name="syntax"></a>構文

```C
void *_malloca(
   size_t size
);
```

### <a name="parameters"></a>パラメーター

*size*<br/>
スタックから割り当てられるバイト数。

## <a name="return-value"></a>戻り値

**_Malloca**ルーチンは、割り当てられた領域への**void**ポインターを返します。これは、どの型のオブジェクトの格納にも適切にアラインメントされていることが保証されています。 *Size*が0の場合、 **_malloca**は長さが0のアイテムを割り当て、そのアイテムへの有効なポインターを返します。

*Size*が **_ALLOCA_S_THRESHOLD**より大きい場合、 **_malloca**はヒープに割り当てを試み、スペースを割り当てることができない場合は null ポインターを返します。 *Size*が **_ALLOCA_S_THRESHOLD**以下の場合、 **_malloca**はスタックに割り当てを試行し、領域を割り当てることができない場合はスタックオーバーフロー例外が生成されます。 スタックオーバーフロー例外は例外でC++はありません。構造化された例外です。 例外処理をC++使用する代わりに、[構造化例外処理](../../cpp/structured-exception-handling-c-cpp.md)(SEH) を使用してこの例外をキャッチする必要があります。

## <a name="remarks"></a>Remarks

**_malloca**は、要求が **_ALLOCA_S_THRESHOLD**によって指定された特定のサイズ (バイト単位) を超えた場合に、プログラムスタックまたはヒープから*サイズ*バイトを割り当てます。 **_Malloca**と **_alloca**の違いは、 **_alloca**はサイズに関係なく常にスタックに割り当てられるという点です。 メモリを解放して割り当てられるように解放するために**無料**の呼び出しを必要としない、または許可しない **_alloca**とは異なり、 **_malloca**ではメモリを解放するために[_freea](freea.md)を使用する必要があります。 デバッグモードでは、 **_malloca**は常にヒープからメモリを割り当てます。

例外ハンドラー (EH) で **_malloca**を明示的に呼び出すには、制限があります。 X86 クラスのプロセッサで実行される EH ルーチンは、独自のメモリフレームで動作します。これらのタスクは、外側の関数のスタックポインターの現在の位置に基づいていないメモリ空間で実行されます。 最も一般的な実装には、Windows NT 構造化例外処理 (SEH) や C++ catch 句の式などがあります。 したがって、次のいずれかのシナリオで明示的に **_malloca**を呼び出すと、呼び出し元の EH ルーチンに戻るときにプログラムエラーが発生します。

- Windows NT SEH 例外フィルター式: **__except** (`_malloca ()` )

- Windows NT SEH 最終例外ハンドラー: **__finally** {`_malloca ()` }

- C++ EH catch 句の式

ただし、 **_malloca**は、eh ルーチン内から直接呼び出すことも、前述の eh シナリオのいずれかで呼び出されるアプリケーション提供のコールバックから呼び出すこともできます。

> [!IMPORTANT]
> Windows XP では、 **_malloca**が try/catch ブロック内で呼び出される場合は、catch ブロックで[_resetstkoflw](resetstkoflw.md)を呼び出す必要があります。

上記の制限に加え、 [/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)オプションを使用する場合、 **_malloca**を **__except**ブロックで使用することはできません。 詳細については、「 [/clr Restrictions](../../build/reference/clr-restrictions.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_malloca**|\<malloc.h>|

## <a name="example"></a>例

```C
// crt_malloca_simple.c
#include <stdio.h>
#include <malloc.h>

void Fn()
{
   char * buf = (char *)_malloca( 100 );
   // do something with buf
   _freea( buf );
}

int main()
{
   Fn();
}
```

## <a name="example"></a>例

```C
// crt_malloca_exception.c
// This program demonstrates the use of
// _malloca and trapping any exceptions
// that may occur.

#include <windows.h>
#include <stdio.h>
#include <malloc.h>

int main()
{
    int     size;
    int     numberRead = 0;
    int     errcode = 0;
    void    *p = NULL;
    void    *pMarker = NULL;

    while (numberRead == 0)
    {
        printf_s("Enter the number of bytes to allocate "
                 "using _malloca: ");
        numberRead = scanf_s("%d", &size);
    }

    // Do not use try/catch for _malloca,
    // use __try/__except, since _malloca throws
    // Structured Exceptions, not C++ exceptions.

    __try
    {
        if (size > 0)
        {
            p =  _malloca( size );
        }
        else
        {
            printf_s("Size must be a positive number.");
        }
        _freea( p );
    }

    // Catch any exceptions that may occur.
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )
    {
        printf_s("_malloca failed!\n");

        // If the stack overflows, use this function to restore.
        errcode = _resetstkoflw();
        if (errcode)
        {
            printf("Could not reset the stack!");
            _exit(1);
        }
    };
}
```

### <a name="input"></a>入力

```Input
1000
```

### <a name="sample-output"></a>出力例

```Output
Enter the number of bytes to allocate using _malloca: 1000
```

## <a name="see-also"></a>関連項目

[メモリ割り当て](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
