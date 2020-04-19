---
title: _onexit、_onexit_m
ms.date: 11/04/2016
api_name:
- _onexit
- _onexit_m
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
- _onexit
- onexit_m
- onexit
- _onexit_m
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
ms.openlocfilehash: 9afcd729f19f11b82e8f24c2b7fcf9ec40990deb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951344"
---
# <a name="_onexit-_onexit_m"></a>_onexit、_onexit_m

終了時に呼び出されるルーチンを登録します。

## <a name="syntax"></a>構文

```C
_onexit_t _onexit(
   _onexit_t function
);
_onexit_t_m _onexit_m(
   _onexit_t_m function
);
```

### <a name="parameters"></a>パラメーター

*function*<br/>
終了時に呼び出される関数へのポインター。

## <a name="return-value"></a>戻り値

**_onexit**は、成功した場合は関数へのポインターを返し、関数ポインターを格納する領域がない場合は**NULL**を返します。

## <a name="remarks"></a>Remarks

**_Onexit**関数には、プログラムが正常に終了したときに呼び出される関数 (*関数*) のアドレスが渡されます。 **_Onexit**を連続して呼び出すと、LIFO (後入れ先出し) の順序で実行される関数のレジスタが作成されます。 **_Onexit**に渡される関数は、パラメーターを受け取ることができません。

DLL 内から **_onexit**が呼び出された場合、 **_onexit**に登録されているルーチンは、DLL_PROCESS_DETACH を使用して**DllMain**が呼び出された後に dll のアンロード時に実行されます。

**_onexit**は Microsoft の拡張機能です。 ANSI の移植性のためには、[atexit](atexit.md) を使用します。 関数のバージョン **(_s)** は混合モードで使用されます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_onexit**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_onexit.c

#include <stdlib.h>
#include <stdio.h>

/* Prototypes */
int fn1(void), fn2(void), fn3(void), fn4 (void);

int main( void )
{
   _onexit( fn1 );
   _onexit( fn2 );
   _onexit( fn3 );
   _onexit( fn4 );
   printf( "This is executed first.\n" );
}

int fn1()
{
   printf( "next.\n" );
   return 0;
}

int fn2()
{
   printf( "executed " );
   return 0;
}

int fn3()
{
   printf( "is " );
   return 0;
}

int fn4()
{
   printf( "This " );
   return 0;
}
```

### <a name="output"></a>Output

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[atexit](atexit.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[__dllonexit](../../c-runtime-library/dllonexit.md)<br/>
