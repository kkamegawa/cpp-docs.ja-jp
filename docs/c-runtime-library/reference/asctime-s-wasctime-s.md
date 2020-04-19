---
title: asctime_s、_wasctime_s
ms.date: 11/04/2016
api_name:
- _wasctime_s
- asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
ms.openlocfilehash: 1cd2a15db0a27dedd88b9abf24b98d338515c949
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624782"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s、_wasctime_s

**Tm**時間構造体を文字列に変換します。 これらの関数は、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、[asctime、_wasctime](asctime-wasctime.md) のセキュリティが強化されたバージョンです。

## <a name="syntax"></a>構文

```C
errno_t asctime_s(
   char* buffer,
   size_t numberOfElements,
   const struct tm *tmSource
);
errno_t _wasctime_s(
   wchar_t* buffer,
   size_t numberOfElements
   const struct tm *tmSource
);
template <size_t size>
errno_t asctime_s(
   char (&buffer)[size],
   const struct tm *tmSource
); // C++ only
template <size_t size>
errno_t _wasctime_s(
   wchar_t (&buffer)[size],
   const struct tm *tmSource
); // C++ only
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
文字列の結果を格納するバッファーへのポインター。 この関数は、 *Numberofelements*によって指定されたサイズの有効なメモリ位置を指すポインターを想定しています。

*numberOfElements*<br/>
結果を格納するために使用されるバッファーのサイズ。

*tmSource*<br/>
時刻/日付の構造体。 この関数は、有効な**struct** **tm**オブジェクトへのポインターを想定しています。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。 障害が発生した場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているとおり、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、戻り値はエラー コードになります。 エラー コードは、ERRNO.H で定義されています。 詳細については、「[errno 定数](../../c-runtime-library/errno-constants.md)」を参照してください。 各エラー条件に対して返される実際のエラー コードを、次の表に示します。

### <a name="error-conditions"></a>エラー条件

|*バッファー*|*numberOfElements*|*tmSource*|Return|*バッファー*内の値|
|--------------|------------------------|----------|------------|-----------------------|
|**NULL**|どれでも可|どれでも可|**EINVAL**|変更されない|
|Not **NULL** (有効なメモリを指す)|0|どれでも可|**EINVAL**|変更されない|
|**NULL**以外|0< size < 26|どれでも可|**EINVAL**|空の文字列|
|**NULL**以外|>= 26|**NULL**|**EINVAL**|空の文字列|
|**NULL**以外|>= 26|無効な時間構造体または時間のコンポーネントの値が範囲外|**EINVAL**|空の文字列|

> [!NOTE]
> **Wasctime_s**のエラー条件は**asctime_s**に似ていますが、サイズ制限は単語単位で測定されます。

## <a name="remarks"></a>Remarks

**Asctime**関数は、構造体として格納されている時刻を文字列に変換します。 *Tmsource*値は通常、 **gmtime**または**localtime**の呼び出しから取得されます。 これらの関数を使用すると、TIME で定義されているように、 **tm**構造体を入力できます。始め.

|timeptr メンバー|[値]|
|--------------------|-----------|
|**tm_hour**|深夜からの時間 (0-23)|
|**tm_isdst**|夏時間が有効な場合は正、夏時間が無効な場合は 0、夏時間かどうかが不明な場合は負。 C ランタイム ライブラリでは、アメリカ合衆国の規則を前提に夏時間 (DST) を計算します。|
|**tm_mday**|月の通算日 (1-31)|
|**tm_min**|分後 (分) (0-59)|
|**tm_mon**|月 (0-11;1月 = 0)|
|**tm_sec**|秒後の秒数 (0-59)|
|**tm_wday**|曜日 (0-6;日曜日 = 0)|
|**tm_yday**|年の通算日 (0-365;1月1日 = 0)|
|**tm_year**|年 (実際の西暦から 1900 を引いた数)|

変換された文字列も、ローカル タイム ゾーンの設定に従って調整されます。 ローカル タイムの設定の詳細については、[time、_time32、_time64](time-time32-time64.md)、[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)、および [localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md) の関数を参照してください。また、タイム ゾーン環境とグローバル変数の定義の詳細については、[_tzset](tzset.md) 関数を参照してください。

**Asctime_s**によって生成される文字列の結果には、26文字が含まれており、`Wed Jan 02 02:03:55 1980\n\0`という形式になっています。 24 時間制が使用されます。 すべてのフィールドには一定の幅があります。 文字列の最後の 2 つの位置には、改行文字と null 文字が入ります。 2 番目のパラメーターとして渡される値は、この大きさ以上にする必要があります。 小さい場合は、エラーコード**EINVAL**が返されます。

**_wasctime_s**は、 **asctime_s**のワイド文字バージョンです。 それ以外では、 **_wasctime_s**と**asctime_s**は同じように動作します。

これらの関数のデバッグライブラリバージョンは、最初にバッファーを0xFE で埋めます。 この動作を無効にするには、[_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md) を使用します。

### <a name="generic-text-routine-mapping"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

C++ では、テンプレートのオーバーロードによってこれらの関数を簡単に使用できます。オーバーロードでは、バッファー長を自動的に推論できるため、サイズ引数を指定する必要がなくなります。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> または \<wchar.h>|

## <a name="security"></a>セキュリティ

バッファーポインターが**NULL**ではなく、ポインターが有効なバッファーを指していない場合、関数はその位置にあるものをすべて上書きします。 これによりアクセス違反が発生することもあります。

渡されるサイズ引数がバッファーの実際のサイズより大きい場合、[バッファー オーバーラン](/windows/win32/SecBP/avoiding-buffer-overruns)が発生する場合があります。

## <a name="example"></a>例

このプログラムは、システム時刻を長整数の**aclock**に配置し、それを構造体の**newtime**に変換した後、 **asctime_s**関数を使用して出力用の文字列形式に変換します。

```C
// crt_asctime_s.c
#include <time.h>
#include <stdio.h>

struct tm newtime;
__time32_t aclock;

int main( void )
{
   char buffer[32];
   errno_t errNum;
   _time32( &aclock );   // Get time in seconds.
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.

   // Print local time as a string.

   errNum = asctime_s(buffer, 32, &newtime);
   if (errNum)
   {
       printf("Error code: %d", (int)errNum);
       return 1;
   }
   printf( "Current date and time: %s", buffer );
   return 0;
}
```

```Output
Current date and time: Wed May 14 15:30:17 2003
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
