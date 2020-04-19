---
title: 基本データ型
ms.date: 11/04/2016
f1_keywords:
- __time64_t
- _diskfree_t
- _CRT_DUMP_CLIENT
- _fsize_t
- __timeb64
- File
- __utimeb64
- jmp_buf
- __finddata64_t
- _wfinddata_t
- _finddata_t
- utimbuf64
- wint_t
- wctrans_t
- wctype_t
- _HFILE
- _secerr_handler_func
- clock_t
- fpos_t
- _dev_t
- time64_t
- wfinddata64_t
- stat64
- ldiv_t
- _EXCEPTION_POINTERS
- terminate_function
- size_t
- timeb64
- tm
- _HEAPINFO
- unexpected_function
- _CrtMemState
- _se_translator_function
- sig_atomic_t
- _CRT_REPORT_HOOK
- _complex
- _w_finddatai64_t
- _timeb
- _onexit_t
- _RTC_ErrorNumber
- lconv
- _PNH
- _off_t
- ptrdiff_t
- time_t
- _FPIEEE_RECORD
- _exception
- __w_finddata64_t
- __stat64
- _utimbuf
- __utimbuf64
- div_t
- _CRT_ALLOC_HOOK
- int8_t
- uint8_t
- int16_t
- uint16_t
- int32_t
- uint32_t
- int64_t
- int_least8_t
- uint_least8_t
- int_least16_t
- uint_least16_t
- int_least32_t
- uint_least32_t
- int_least64_t
- uint_least64_t
- int_fast8_t
- uint_fast8_t
- int_fast16_t
- uint_fast16_t
- int_fast32_t
- uint_fast32_t
- int_fast64_t
- uint_fast64_t
- intmax_t
- uintmax_t
helpviewer_keywords:
- __timeb64 type
- tm type
- clock_t type
- intptr_t type
- diskfree_t type
- wctype_t type
- CRT_DUMP_CLIENT type
- sig_atomic_t type
- _PNH type
- time_t type
- wfinddata_t type
- timeb64
- CRT, standard types
- wint_t type
- _RTC_ErrorNumber type
- _diskfree_t type
- _dev_t type
- _wfinddata_t type
- HFILE type
- __utimbuf64 type
- div_t type
- _onexit_t type
- _secerr_handler_func type
- FPIEEE_RECORD type
- HEAPINFO type
- PNH type
- _CRT_ALLOC_HOOK type
- _se_translater_function type
- va_list type
- wctrans_t type
- secerr_handler_func type
- _locale_t type
- timeb type
- lconv type
- utimbuf type
- dev_t type
- unexpected_function typedef
- _complex type
- _off_t type
- off_t type
- RTC_ErrorNumber type
- _FPIEEE_RECORD type
- exception type
- _CRT_REPORT_HOOK type
- _HEAPINFO type
- ldiv_t type
- terminate_function type
- uintptr_t type
- _CRT_DUMP_CLIENT type
- _utimbuf type
- wfinddatai64_t type
- fpos_t type
- wchar_t type
- CRT_ALLOC_HOOK type
- _HFILE type
- __time64_t type
- _timeb type
- CrtMemState type
- __finddata64_t type
- _exception type
- stat type
- onexit_t type
- FILE constant
- _stat type
- finddata_t type
- __wfinddata64_t type
- ptrdiff_t type
- complex types
- _wfinddatai64_t type
- _EXCEPTION_POINTERS type
- jmp_buf type
- se_translater_function type
- size_t type
- EXCEPTION_POINTERS type
- __stat64 type
- _fsize_t type
- CRT_REPORT_HOOK type
- _finddata_t type
ms.assetid: 23312dd2-4a6a-4d70-9b48-2a5d0d8c9f28
ms.openlocfilehash: c93cf4bf138fc6bc648d33c180edbed0dbe5014e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500640"
---
# <a name="standard-types"></a>基本データ型

Microsoft ランタイム ライブラリには、次の基本データ型および Typedefs が用意されています。

### <a name="fixed-width-integral-types-stdinth"></a>固定長整数型 (stdint.h)

|name|同等の組み込み型|
|----------|-------------------------------|
|int8\_t, uint8\_t|signed char、unsigned char|
|int16\_t, uint16\_t|short、unsigned short|
|int32\_t, uint32\_t|int、unsigned int|
|int64\_t, uint64\_t|long long、unsigned long long|
|int_least8_t、uint_least8_t|signed char、unsigned char|
|int_least16_t、uint_least16_t|short、unsigned short|
|int_least32_t、uint_least32_t|int、unsigned int|
|int_least64_t、uint_least64_t|long long、unsigned long long|
|int_fast8_t、uint_fast8_t|signed char、unsigned char|
|int_fast16_t、uint_fast16_t|int、unsigned int|
|int_fast32_t、uint_fast32_t|int、unsigned int|
|int_fast64_t、uint_fast64_t|long long、unsigned long long|
|intmax_t、uintmax_t|long long、unsigned long long|

|型|説明|ヘッダー ファイル|
|----------|-----------------|-----------------|
|`clock_t` (long 型)|[clock](../c-runtime-library/reference/clock.md) で使用される時刻値を格納します。|TIME.H|
|`_complex` 構造体|[_cabs](../c-runtime-library/reference/cabs.md) で使用される複素数の実数部および虚数部を格納します。|MATH.H|
|`_CRT_ALLOC_HOOK`|ユーザー定義フック関数の型定義。 [_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md) で使用します。|CRTDBG.H|
|`_CRT_DUMP_CLIENT`、<br /><br /> `_CRT_DUMP_CLIENT_M`|[_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md) で呼び出されるコールバック関数の型定義。|CRTDBG.H|
|`_CrtMemState` 構造体|C ランタイム デバッグ ヒープの現在の状態に関する情報を提供します。|CRTDBG.H|
|`_CRT_REPORT_HOOK`、<br /><br /> `_CRT_REPORT_HOOKW`、<br /><br /> `_CRT_REPORT_HOOKW_M`|[_CrtDbgReport](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) で呼び出されるコールバック関数の型定義。<br /><br /> この関数のパラメーターは、レポートの種類、出力メッセージ、およびコールバック関数の戻り値です。|CRTDBG.H|
|`dev_t`、`_dev_t` の短整数または符号なし整数|デバイス ハンドルを表します。|SYS\TYPES.H|
|`_diskfree_t` 構造体|ディスク ドライブに関する情報を格納します。 [_getdiskfree](../c-runtime-library/reference/getdiskfree.md) で使用します **。**|DOS.H および DIRECT.H|
|`div_t`、`ldiv_t`、および `lldiv_t` の各構造体|それぞれ [div](../c-runtime-library/reference/div.md)、[ldiv](../c-runtime-library/reference/ldiv-lldiv.md)、および [lldiv](../c-runtime-library/reference/ldiv-lldiv.md) によって返される値を格納します。|STDLIB.H|
|`errno_t` 整数|`errno` のエラー コードを処理する関数の戻り値の型またはパラメーターに使用されます。|STDDEF.H、<br /><br /> CRTDEFS.H|
|`_exception` 構造体|[_matherr](../c-runtime-library/reference/matherr.md) のエラー情報を格納します。|MATH.H|
|`_EXCEPTION_POINTERS`|例外レコードを格納します。 詳細については、[EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) に関するページをご覧ください。|FPIEEE.H|
|`FILE` 構造体|ストリームの現在の状態に関する情報を格納します。すべてのストリーム I/O 操作で使用します。|STDIO.H|
|`_finddata_t`、`_wfinddata_t`、`_finddata32_t`、`_wfinddata32_t`、`_finddatai64_t`、`_wfinddatai64_t`、`__finddata64_t`、`__wfinddata64_t`、`__finddata32i64_t`、`__wfinddata32i64_t`、`__finddata64i32_t`、`__wfinddata64i32_t` の各構造体|[_findfirst、_wfindfirst および関連する関数](../c-runtime-library/reference/findfirst-functions.md)、[_findnext、_wfindnext および関連する関数](../c-runtime-library/reference/findnext-functions.md)によって返されるファイル属性情報を格納します。 構造体のメンバーについては、「[ファイル名検索関数](../c-runtime-library/filename-search-functions.md)」をご覧ください。|IO.H、WCHAR.H|
|`_FPIEEE_RECORD` 構造体|[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md) によってユーザー定義トラップに渡される、IEEE 浮動小数点例外に関する情報を格納します。|FPIEEE.H|
|`fpos_t` (対象プラットフォームによって、long int、`__int64`、または構造体)|[fgetpos](../c-runtime-library/reference/fgetpos.md) および [fsetpos](../c-runtime-library/reference/fsetpos.md) によって、一意に指定したファイル内の各位置の情報を記録するために使用されます。|STDIO.H|
|`_fsize_t` (符号なし長整数)|ファイルのサイズを表すために使用されます。|IO.H、<br /><br /> WCHAR.H|
|`_HEAPINFO` 構造体|[_heapwalk](../c-runtime-library/reference/heapwalk.md) の次のヒープ エントリに関する情報を格納しています。|MALLOC.H|
|`_HFILE` (void \*)|オペレーティング システムのファイル ハンドル|CRTDBG.H|
|`imaxdiv_t`|[imaxdiv](../c-runtime-library/reference/imaxdiv.md) 関数によって返される、商と剰余の両方を含む値の型。|inttypes.h|
|`ino_t`、`_ino_t` (unsigned short 型)|ステータス情報を返します。|WCHAR.H|
|`intmax_t`|任意の符号付き整数型の任意の値を表すことができる符号付き整数型。|stdint.h|
|`intptr_t` (対象のプラットフォームによって、長整数または `__int64`)|Win32 および Win64 の両方のプラットフォームにポインター (または HANDLE) を格納します。|STDDEF.H およびその他のインクルード ファイル|
|`jmp_buf` 配列|[setjmp](../c-runtime-library/reference/setjmp.md) および[longjmp](../c-runtime-library/reference/longjmp.md) によって、プログラム環境を保存および復元するために使用されます。|SETJMP.H|
|`lconv` 構造体|各国/地域の数値形式に関する規則を格納しています。 [localeconv](../c-runtime-library/reference/localeconv.md) によって使用されます。|LOCALE.H|
|`_LDOUBLE`、<br /><br /> `_LONGDOUBLE`、<br /><br /> `_LDBL12` (long double 型または unsigned char 配列)|long double 型の値を表すために使用します。|STDLIB.H|
|`_locale_t` 構造体|現在のロケール値を格納します。ロケール固有のすべての C ランタイム ライブラリで使用します。|CRTDEF.H|
|`mbstate_t`|マルチバイト文字の変換状態を追跡します。|WCHAR.H|
|`off_t` 長整数、`_off_t` 長整数|ファイル オフセット値を表します。|WCHAR.H、SYS\TYPES.H|
|`_onexit_t`、<br /><br /> `_onexit_m_t` ポインター|[_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md) によって返されます。|STDLIB.H|
|関数への `_PNH` ポインター|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md) に対する引数の型。|NEW.H|
|`ptrdiff_t` (対象のプラットフォームによって、長整数または `__int64`)|2 つのポインターの減算結果。|CRTDEFS.H|
|`_purecall_handler`、<br /><br /> `_purecall_handler_m`|純粋仮想関数を呼び出したときに呼び出されるコールバック関数の型定義。 [_get_purecall_handler、_set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md) によって使用されます。 `_purecall_handler` 関数の戻り値は void 型です。|STDLIB.H|
|`_RTC_error_fn` の型定義|ランタイム エラー チェックを処理する関数の型定義。 [_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md) で使用します。|RTCAPI.H|
|`_RTC_error_fnW` の型定義|ランタイム エラー チェックを処理する関数の型定義。 [_RTC_SetErrorFuncW](../c-runtime-library/reference/rtc-seterrorfuncw.md) で使用します。|RTCAPI.H|
|`_RTC_ErrorNumber` 列挙体|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md) および [_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md) のエラー条件を定義します。|RTCAPI.H|
|`_se_translator_function`|例外を変換するコールバック関数の型定義。 最初のパラメーターは例外コードで、2 番目のパラメーターは例外レコードです。 [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) によって使用されます。|EH.H|
|`sig_atomic_t` 整数|[signal](../c-runtime-library/reference/signal.md) で使用される、非同期な割り込みが発生してもアトミックなエンティティとして変更可能なオブジェクト型。|SIGNAL.H|
|`size_t` (対象のプラットフォームによって、符号なし __int64 または符号なし整数)|`sizeof` 演算子の結果。|CRTDEFS.H およびその他のインクルード ファイル|
|`_stat` 構造体|[_stat](../c-runtime-library/reference/stat-functions.md) および [_fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) が返すファイル ステータス情報を格納します。|SYS\STAT.H|
|`__stat64` 構造体|[_fstat64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)、[_stat64](../c-runtime-library/reference/stat-functions.md)、および [_wstat64](../c-runtime-library/reference/stat-functions.md) が返すファイル ステータス情報を格納します。|SYS\STAT.H|
|`_stati64` 構造体|[_fstati64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)、[_stati64](../c-runtime-library/reference/stat-functions.md)、および [_wstati64](../c-runtime-library/reference/stat-functions.md) が返すファイル ステータス情報を格納します。|SYS\STAT.H|
|`terminate_function` の型定義|[terminate](../c-runtime-library/reference/terminate-crt.md) を呼び出したときに呼び出されるコールバック関数の型定義。 [set_terminate](../c-runtime-library/reference/set-terminate-crt.md) で使用します。|EH.H|
|`time_t` (__int64 または長整数)|[mktime](../c-runtime-library/reference/mktime-mktime32-mktime64.md)、[time](../c-runtime-library/reference/time-time32-time64.md)、[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)、[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)、[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)、[gmtime、_gmtime32、_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) で時刻値を表します。 世界協定時刻 (UTC) 1970 年 1 月 1 日 0:00 からの経過秒数。 _USE_32BIT_TIME_T が定義されている場合、`time_t` は長整数になります。 定義されていない場合は、64 ビット整数になります。|TIME.H、<br /><br /> SYS\STAT.H、<br /><br /> SYS\TIMEB.H|
|`__time32_t` (長整数)|[mktime、_mktime32、_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)、[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)、[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)、[gmtime、_gmtime32、_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)、[localtime、_localtime32、_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md) で時刻値を表します。|CRTDEFS.H、SYS\STAT.H、<br /><br /> SYS\TIMEB.H|
|`__time64_t` (`__int64`)|[mktime、_mktime32、_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)、[_ctime64、_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)、[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)、[_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)、[_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md)、[_time64](../c-runtime-library/reference/time-time32-time64.md) で時刻値を表します。|TIME.H、<br /><br /> SYS\STAT.H、<br /><br /> SYS\TIMEB.H|
|`_timeb` 構造体|[_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) および [_ftime_s、_ftime32_s、_ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) が現在のシステム時刻を格納するために使用します。|SYS\TIMEB.H|
|`__timeb32` 構造体|[_ftime、_ftime32、_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) および [_ftime_s、_ftime32_s、_ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) が現在のシステム時刻を格納するために使用します。|SYS\TIMEB.H|
|`__timeb64` 構造体|[_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) および [_ftime_s、_ftime32_s、_ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) が現在のシステム時刻を格納するために使用します。|SYS\TIMEB.H|
|`tm` 構造体|[asctime、_wasctime](../c-runtime-library/reference/asctime-wasctime.md)、[asctime_s、_wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)、[gmtime、_gmtime32、_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)、[gmtime_s、_gmtime32_s、_gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)、[localtime、_localtime32、_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md)、[localtime_s、_localtime32_s、_localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)、[mktime、_mktime32、_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md) および [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) が時間情報を格納または取得するために使用します。|TIME.H|
|`uintmax_t`|任意の符号なし整数型の任意の値を表すことができる符号なし整数型。|stdint.h|
|`uintptr_t` (対象のプラットフォームによって、長整数または `__int64`)|`intptr_t` の符号なし整数バージョンまたは符号なし __int64 バージョン。|STDDEF.H およびその他のインクルード ファイル|
|`unexpected_function`|[unexpected](../c-runtime-library/reference/unexpected-crt.md) を呼び出したときに呼び出されるコールバック関数の型定義。 [set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md) で使用します。|EH.H|
|`_utimbuf` 構造体|[_utime、_wutime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) および [_futime、_futime32、_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) でファイル変更日付を変更するために使用する、ファイルへのアクセス時刻および変更時刻を格納します。|SYS\UTIME.H|
|`_utimbuf32` 構造体|[_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) および [_futime、_futime32、_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) でファイル変更日付を変更するために使用する、ファイルへのアクセス時刻および変更時刻を格納します。|SYS\UTIME.H|
|`__utimbuf64` 構造体|[_utime64、_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) および [_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) で現在の時刻を格納するために使用します。|SYS\UTIME.H|
|`va_list` 構造体|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) マクロおよび [va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) マクロに必要な情報を格納するために使用します。 呼び出される関数は、ほかの関数に引数として渡すことができる `va_list` 型の変数を宣言します。|STDARG.H、<br /><br /> CRTDEFS.H|
|`wchar_t` ワイド文字|国際市場に対応した移植性の高いプログラムを作成する場合に有効です。|STDDEF.H、STDLIB.H、<br /><br /> CRTDEFS.H<br /><br /> SYS\STAT.H|
|`wctrans_t` 整数|ロケール固有の文字マップを表します。|WCTYPE.H|
|`wctype_t` 整数|各言語の文字セットの文字をすべて表すことができます。|WCHAR.H、<br /><br /> CRTDEFS.H|
|`wint_t` 整数|任意のワイド文字またはワイド文字のファイル終端値を格納するデータ オブジェクト型。|WCHAR.H、<br /><br /> CRTDEFS.H|

## <a name="see-also"></a>関連項目

[C ランタイム ライブラリ リファレンス](../c-runtime-library/c-run-time-library-reference.md)
