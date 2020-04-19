---
title: _heapchk
ms.date: 11/04/2016
api_name:
- _heapchk
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _heapchk
- heapchk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
ms.openlocfilehash: 857feb66d89d5dc406042478156483ecb86a2474
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954819"
---
# <a name="_heapchk"></a>_heapchk

ヒープに対して整合性チェックを実行します。

## <a name="syntax"></a>構文

```C
int _heapchk( void );
```

## <a name="return-value"></a>戻り値

**_heapchk**は、次のいずれかの整数マニフェスト定数を返します Malloc. h です。

|戻り値|条件|
|-|-|
| **_HEAPBADBEGIN** | 初期ヘッダー情報が無効であるか見つかりません。 |
| **_HEAPBADNODE** | 不適切なノードが検出されたか、ヒープが破損しています。 |
| **_HEAPBADPTR** | ヒープへのポインターが無効です。 |
| **_HEAPEMPTY** | ヒープが初期化されていません。 |
| **_HEAPOK** | ヒープは一貫性があると思われます。 |

さらに、エラーが発生した場合、 **_heapchk**は**errno**をに設定**します。**

## <a name="remarks"></a>Remarks

**_Heapchk**関数は、ヒープの最小限の一貫性をチェックすることにより、ヒープ関連の問題をデバッグするのに役立ちます。 オペレーティングシステムが **_heapchk**(Windows 98 など) をサポートしていない場合、関数は **_HEAPOK**を返し、 **errno**を**に設定**します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_heapchk**|\<malloc.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_heapchk.c
// This program checks the heap for
// consistency and prints an appropriate message.

#include <malloc.h>
#include <stdio.h>

int main( void )
{
   int  heapstatus;
   char *buffer;

   // Allocate and deallocate some memory
   if( (buffer = (char *)malloc( 100 )) != NULL )
      free( buffer );

   // Check heap status
   heapstatus = _heapchk();
   switch( heapstatus )
   {
   case _HEAPOK:
      printf(" OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf(" OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>関連項目

[メモリ割り当て](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
