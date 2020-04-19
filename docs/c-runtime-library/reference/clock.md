---
title: clock
ms.date: 11/04/2016
api_name:
- clock
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
- api-ms-win-crt-time-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- clock
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
ms.openlocfilehash: 836d0c6448adb4c99a251a0e97aa642e30362dcb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939127"
---
# <a name="clock"></a>clock

呼び出しプロセスにかかったウォール クロック時間を計算します。

## <a name="syntax"></a>構文

```C
clock_t clock( void );
```

## <a name="return-value"></a>戻り値

プロセスの開始時の CRT 初期化からの経過時間。1秒あたりの**CLOCKS_PER_SEC**単位で測定されます。 経過時間が使用できない場合、または**clock_t**型として記録できる最大の正の時間を超えた場合、 `(clock_t)(-1)`関数は値を返します。

## <a name="remarks"></a>Remarks

**Clock**関数は、プロセスの開始時に CRT の初期化が行われてから経過したウォールクロックの時間を示します。 この関数は、厳密には ISO C (正味の CPU 時間を戻り値にすることが規定されている) に準拠していないことに注意してください。 CPU 時間を取得するには、Win32 の [GetProcessTimes](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getprocesstimes) 関数を使用します。 経過時間を秒単位で確認するには、 **clock**関数によって返された値をマクロ**CLOCKS_PER_SEC**で除算します。

十分な時間があれば、 **clock**によって返される値は、 **clock_t**の最大正の値を超える可能性があります。 プロセスの実行時間が長い場合、 **clock**によって返される`(clock_t)(-1)`値は、iso C99 標準 (7.23.2.1) および iso C11 standard (7.27.2.1) で指定されているように、常にになります。 Microsoft は**clock_t** **を、符号**付き32ビット整数として実装し、 **CLOCKS_PER_SEC**マクロは1000として定義されています。 これにより、最大**クロック**関数の戻り値として2147483.647 秒 (約24.8 日) が返されます。 この時間を超えて実行されたプロセスでは、**クロック**によって返される値に依存しないでください。 64ビット[時刻](time-time32-time64.md)関数または Windows [queryperformancecounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter)関数を使用すると、多数の年のプロセス経過時間を記録できます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**clock**|\<time.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_clock.c
// This sample uses clock() to 'sleep' for three
// seconds, then determines how long it takes
// to execute an empty loop 600000000 times.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Pauses for a specified number of milliseconds.
void do_sleep( clock_t wait )
{
   clock_t goal;
   goal = wait + clock();
   while( goal > clock() )
      ;
}

const long num_loops = 600000000L;

int main( void )
{
   long    i = num_loops;
   clock_t start, finish;
   double  duration;

   // Delay for a specified time.
   printf( "Delay for three seconds\n" );
   do_sleep( (clock_t)3 * CLOCKS_PER_SEC );
   printf( "Done!\n" );

   // Measure the duration of an event.
   start = clock();
   while( i-- )
      ;
   finish = clock();
   duration = (double)(finish - start) / CLOCKS_PER_SEC;
   printf( "Time to do %ld empty loops is ", num_loops );
   printf( "%2.3f seconds\n", duration );
}
```

```Output
Delay for three seconds
Done!
Time to do 600000000 empty loops is 1.354 seconds
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[difftime、_difftime32、_difftime64](difftime-difftime32-difftime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
