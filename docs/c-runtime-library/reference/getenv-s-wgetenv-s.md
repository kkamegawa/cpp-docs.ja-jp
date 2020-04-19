---
title: getenv_s、_wgetenv_s
description: Microsoft C ランタイムライブラリ getenv_s および _wgetenv_s 関数について説明します。
ms.date: 01/15/2020
api_name:
- getenv_s
- _wgetenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- getenv_s
- _tgetenv_s
- _wgetenv_s
helpviewer_keywords:
- _tgetenv_s function
- wgetenv_s function
- _wgetenv_s function
- getenv_s function
- environment variables
- tgetenv_s function
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
no-loc:
- getenv_s
- _wgetenv_s
- _putenv_s
- main
- wmain
- errno
- EINVAL
- ERANGE
- _environ
- _wenviron
- _putenv
- _wputenv
- _tgetenv_s
- _tzset
- _dupenv_s
- _wdupenv_s
ms.openlocfilehash: 1eb0adc8c92f1133fd929b9d877b2526c042855f
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76124008"
---
# <a name="opno-locgetenv_s-opno-loc_wgetenv_s"></a>getenv_s、_wgetenv_s

現在の環境から値を取得します。 これらの [getenv および _wgetenvgets](getenv-wgetenv.md) のバージョンは、「[Security Features in the CRT](../../c-runtime-library/security-features-in-the-crt.md)」(CRT のセキュリティ機能) で説明されているように、セキュリティが強化されています。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
errno_t getenv_s(
   size_t *pReturnValue,
   char* buffer,
   size_t numberOfElements,
   const char *varname
);
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *varname
);
template <size_t size>
errno_t getenv_s(
   size_t *pReturnValue,
   char (&buffer)[size],
   const char *varname
); // C++ only
template <size_t size>
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t (&buffer)[size],
   const wchar_t *varname
); // C++ only
```

### <a name="parameters"></a>パラメーター

*pReturnValue*<br/>
必要なバッファー サイズ。変数が見つからない場合は 0。

*バッファー*<br/>
環境変数の値を格納するバッファー。

*numberOfElements*<br/>
*バッファー*のサイズ。

*varname*<br/>
環境変数名。

## <a name="return-value"></a>戻り値

正常に終了した場合は 0 を返し、それ以外の場合は失敗に関するエラー コードを返します。

### <a name="error-conditions"></a>エラー条件

|*pReturnValue*|*バッファー*|*numberOfElements*|*varname*|戻り値|
|--------------------|--------------|------------------------|---------------|------------------|
|**NULL**|任意|任意|任意|**EINVAL**|
|任意|**NULL**|>0|任意|**EINVAL**|
|任意|任意|任意|**NULL**|**EINVAL**|

これらのいずれかのエラー条件の場合は、「[Parameter Validation](../../c-runtime-library/parameter-validation.md)」(パラメーターの検証) で説明されているように、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、関数は **errno** を **EINVAL** に設定し **EINVAL** を返します。

また、バッファーが小さすぎる場合、これらの関数は **ERANGE** を返します。 無効なパラメーター ハンドラーは呼び出されません。 これらは、必要なバッファーサイズを*Preturnvalue*値として書き込みます。これにより、プログラムはより大きなバッファーを使用して関数を再度呼び出すことができます。

## <a name="remarks"></a>Remarks

**getenv_s** 関数は、変数*varname*の環境変数の一覧を検索します。 Windows オペレーティングシステムでは、 **getenv_s** の大文字と小文字は区別されません。 **getenv_s** と[_putenv_s](putenv-s-wputenv-s.md)は、グローバル変数 **_environ** が指す環境のコピーを使用して環境にアクセスします。 **getenv_s** は、ランタイムライブラリからアクセスできるデータ構造体でのみ動作し、オペレーティングシステムによってプロセス用に作成された環境 "セグメント" では動作しません。 したがって、 [main](../../cpp/main-function-command-line-args.md)または[wmain](../../cpp/main-function-command-line-args.md)に対して*envp*引数を使用するプログラムは、無効な情報を取得する可能性があります。

**_wgetenv_s** は **getenv_s** のワイド文字バージョンです。 **_wgetenv_s** の引数と戻り値はワイド文字列です。 **_wenviron** グローバル変数は、 **_environ** のワイド文字バージョンです。

MBCS プログラム (SBCS ASCII プログラムなど) では、環境がマルチバイト文字列で構成されているため、 **_wenviron** は最初は**NULL**になります。 次に、 [_wputenv](putenv-wputenv.md)への最初の呼び出しで、または (MBCS) 環境が既に存在する場合 **_wgetenv_s** は、対応するワイド文字の文字列環境が作成され、その後 **_wenviron** によって参照されます。

同様に、Unicode ( **_wmain**) プログラムでは、環境がワイド文字列で構成されているため、 **_environ** は最初は**NULL**になります。 次に、 [_putenv](putenv-wputenv.md)を最初に呼び出すとき、または (Unicode) 環境が既に存在する場合に **getenv_s** を初めて呼び出すときに、対応する MBCS 環境が作成され、その後 **_environ** によって参照されます。

2 つの環境のコピー (MBCS および Unicode) がプログラムに同時に存在する場合、ランタイム システムは、両方のコピーを保持する必要があるため、実行時間が長くなります。 たとえば、 **_putenv** を呼び出すと、2つの環境文字列が対応するように、 **_wputenv** の呼び出しも自動的に実行されます。

> [!CAUTION]
> まれに、ランタイム システムが Unicode 環境とマルチバイト環境の両方を保持している場合、これら 2 つの環境が正確に対応しないことがあります。 これは、一意のマルチバイト文字列はすべて一意の Unicode 文字列に対応していますが、一意の Unicode 文字列は必ずしも一意のマルチバイト文字列に対応していないために発生します。 詳細については、「 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)」を参照してください。

> [!NOTE]
> 関数の **_putenv_s** および **_getenv_s**ファミリは、スレッドセーフではありません。 **_getenv_s**が文字列を変更して **_putenv_s** いるときに文字列ポインターを返すことがあり、その結果、ランダムにエラーが発生する可能性があります。 これらの関数の呼び出しが同期されていることを確認する必要があります。

C++ では、テンプレートのオーバーロードによってこれらの関数を簡単に使用できます。オーバーロードでは、バッファー長を自動的に推論できるため、サイズ引数を指定する必要がなくなります。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

**TZ**環境変数の値を確認または変更するには、必要に応じて **getenv_s** 、 **_putenv** 、および **_tzset** を使用します。 **TZ**の詳細については、「 [_tzset](tzset.md)と[_daylight、_dstbias、_timezone、および _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)」を参照してください。

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**getenv_s**|\<stdlib.h>|
|**_wgetenv_s**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>使用例

```C
// crt_getenv_s.c
// This program uses getenv_s to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* libvar;
   size_t requiredSize;

   getenv_s( &requiredSize, NULL, 0, "LIB");
   if (requiredSize == 0)
   {
      printf("LIB doesn't exist!\n");
      exit(1);
   }

   libvar = (char*) malloc(requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects
   // the environment variable of the current process. The command
   // processor's environment is not changed.
   _putenv_s( "LIB", "c:\\mylib;c:\\yourlib" );

   getenv_s( &requiredSize, NULL, 0, "LIB");

   libvar = (char*) realloc(libvar, requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the new value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "New LIB variable is: %s\n", libvar );

   free(libvar);
}
```

```Output
Original LIB variable is: c:\vctools\lib;c:\vctools\atlmfc\lib;c:\vctools\PlatformSDK\lib;c:\vctools\Visual Studio SDKs\DIA Sdk\lib;c:\vctools\Visual Studio SDKs\BSC Sdk\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[環境定数](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv、_wputenv](putenv-wputenv.md)<br/>
[_dupenv_s、_wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
