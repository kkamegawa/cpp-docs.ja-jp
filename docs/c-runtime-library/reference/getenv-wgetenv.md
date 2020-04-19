---
title: getenv、_wgetenv
description: Microsoft C ランタイムライブラリ getenv および _wgetenv 関数について説明します。
ms.date: 01/15/2020
api_name:
- getenv
- _wgetenv
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
- _wgetenv
- getenv
- _tgetenv
helpviewer_keywords:
- getenv function
- tgetenv function
- wgetenv function
- environment values
- environment variables
- _tgetenv function
- _wgetenv function
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
no-loc:
- getenv
- _wgetenv
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
ms.openlocfilehash: 5e06e0c66d1ee60a067c2e27fedb5ca1dca7109a
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123995"
---
# <a name="opno-locgetenv-opno-loc_wgetenv"></a>getenv、_wgetenv

現在の環境から値を取得します。 これらの関数のセキュリティを強化したバージョンを使用できます。「 [getenv_s、_wgetenv_s」を](getenv-s-wgetenv-s.md)参照してください。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
char *getenv(
   const char *varname
);
wchar_t *_wgetenv(
   const wchar_t *varname
);
```

### <a name="parameters"></a>パラメーター

*varname*<br/>
環境変数名。

## <a name="return-value"></a>戻り値

*Varname*を含む環境のテーブルエントリへのポインターを返します。 返されたポインターを使用して環境変数の値を変更することは安全ではありません。 環境変数の値を変更するには、 [_putenv](putenv-wputenv.md)関数を使用します。 *Varname*が環境テーブルに見つからない場合、戻り値は**NULL**になります。

## <a name="remarks"></a>Remarks

**getenv** 関数は、変数*varname*の環境変数の一覧を検索します。 Windows オペレーティングシステムでは、 **getenv** の大文字と小文字は区別されません。 **getenv** および **_putenv** 、グローバル変数 **_environ** が指す環境のコピーを使用して環境にアクセスします。 **getenv** は、ランタイムライブラリからアクセスできるデータ構造体でのみ動作し、オペレーティングシステムによってプロセス用に作成された環境 "セグメント" では動作しません。 したがって、 [main](../../cpp/main-function-command-line-args.md)または[wmain](../../cpp/main-function-command-line-args.md)に対して*envp*引数を使用するプログラムは、無効な情報を取得することがあります。

*Varname*が**NULL**の場合、この関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は **errno** を **EINVAL** に設定し、 **NULL**を返します。

**_wgetenv** は **getenv** のワイド文字バージョンです。 **_wgetenv** の引数と戻り値はワイド文字列です。 **_wenviron** グローバル変数は、 **_environ** のワイド文字バージョンです。

MBCS プログラム (SBCS ASCII プログラムなど) では、環境がマルチバイト文字列で構成されているため、 **_wenviron** は最初は**NULL**になります。 次に、 [_wputenv](putenv-wputenv.md)の最初の呼び出しで、または (MBCS) 環境が既に存在する場合に **_wgetenv** を初めて呼び出すときに、対応するワイド文字列環境が作成され、その後 **_wenviron** によってポイントされます。

同様に、Unicode ( **_wmain**) プログラムでは、環境がワイド文字列で構成されているため、 **_environ** は最初は**NULL**になります。 次に、 **_putenv** を最初に呼び出すとき、または (Unicode) 環境が既に存在する場合に **getenv** を初めて呼び出すときに、対応する MBCS 環境が作成され、その後 **_environ** によって参照されます。

2 つの環境のコピー (MBCS および Unicode) がプログラムに同時に存在する場合、ランタイム システムは、両方のコピーを保持する必要があるため、実行時間が長くなります。 たとえば、 **_putenv** を呼び出すと、2つの環境文字列が対応するように、 **_wputenv** の呼び出しも自動的に実行されます。

> [!CAUTION]
> まれに、ランタイム システムが Unicode 環境とマルチバイト環境の両方を保持している場合、これら 2 つの環境が正確に対応しないことがあります。 これは、一意のマルチバイト文字列はすべて一意の Unicode 文字列に対応していますが、一意の Unicode 文字列は必ずしも一意のマルチバイト文字列に対応していないためです。 詳細については、「 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)」を参照してください。

> [!NOTE]
> 関数の **_putenv** および **_getenv**ファミリは、スレッドセーフではありません。 **_getenv**が文字列を変更しているときに文字列ポインターを返すことで、ランダム **_putenv** にエラーが発生する可能性があります。 これらの関数の呼び出しが同期されていることを確認する必要があります。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv**|**getenv**|**_wgetenv**|

**TZ**環境変数の値を確認または変更するには、必要に応じて **getenv** 、 **_putenv** 、および **_tzset** を使用します。 **TZ**の詳細については、「 [_tzset](tzset.md)と _daylight」 [、「タイムゾーン」、および「_tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)」を参照してください。

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**getenv**|\<stdlib.h>|
|**_wgetenv**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>使用例

```C
// crt_getenv.c
// compile with: /W3
// This program uses getenv to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *libvar;

   // Get the value of the LIB environment variable.
   libvar = getenv( "LIB" ); // C4996
   // Note: getenv is deprecated; consider using getenv_s instead

   if( libvar != NULL )
      printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects the environment
   // variable of the current process. The command processor's
   // environment is not changed.
   _putenv( "LIB=c:\\mylib;c:\\yourlib" ); // C4996
   // Note: _putenv is deprecated; consider using putenv_s instead

   // Get new value.
   libvar = getenv( "LIB" ); // C4996

   if( libvar != NULL )
      printf( "New LIB variable is: %s\n", libvar );
}
```

```Output
Original LIB variable is: C:\progra~1\devstu~1\vc\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>関連項目

[プロセスと環境の制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[_putenv、_wputenv](putenv-wputenv.md)<br/>
[環境定数](../../c-runtime-library/environmental-constants.md)<br/>
