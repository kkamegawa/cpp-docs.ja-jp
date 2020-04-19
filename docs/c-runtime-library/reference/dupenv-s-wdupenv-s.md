---
title: _dupenv_s、_wdupenv_s
ms.date: 11/04/2016
api_name:
- _dupenv_s
- _wdupenv_s
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
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
ms.openlocfilehash: f66828e0941c2324d75797cbb1fa77bdfa184205
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942022"
---
# <a name="_dupenv_s-_wdupenv_s"></a>_dupenv_s、_wdupenv_s

現在の環境から値を取得します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
errno_t _dupenv_s(
   char **buffer,
   size_t *numberOfElements,
   const char *varname
);
errno_t _wdupenv_s(
   wchar_t **buffer,
   size_t *numberOfElements,
   const wchar_t *varname
);
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
変数の値を格納するバッファー。

*numberOfElements*<br/>
*バッファー*のサイズ。

*varname*<br/>
環境変数名。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。

これらの関数は、パラメーターを検証します。*buffer*または*varname*が**NULL**の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、関数は**errno**を**einval**に設定し、 **einval**を返します。

これらの関数が十分なメモリを割り当てられない場合、 *buffer*を**NULL**に設定し、 *numberofelements*を0に設定して、 **ENOMEM**を返します。

## <a name="remarks"></a>Remarks

**_Dupenv_s**関数は、変数*varname*の環境変数の一覧を検索します。 変数が見つかった場合、 **_dupenv_s**はバッファーを割り当て、変数の値をバッファーにコピーします。 バッファーのアドレスと長さは、 *Buffer* *要素と numberofelements*で返されます。 **_Dupenv_s**は、バッファー自体を割り当てることにより、 [getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)に代わる便利な手段を提供します。

> [!NOTE]
> [free](free.md) の呼び出しによるメモリの解放は、呼び出し元プログラムが行います。

変数が見つからない場合、 *buffer*は**NULL**に設定され、 *numberofelements*は0に設定され、戻り値は0になります。これは、この状況がエラー状態であるとは見なされないためです。

バッファーのサイズに関心がない場合は、 *Numberofelements*に**NULL**を渡すことができます。

Windows オペレーティングシステムでは、 **_dupenv_s**は大文字と小文字が区別されません。 **_dupenv_s**は、グローバル変数 **_environ**が指す環境のコピーを使用して環境にアクセスします。 **_Environ**の説明については、 [getenv_s、_Wgetenv_s](getenv-s-wgetenv-s.md)の「解説」を参照してください。

*Buffer*の値は、環境変数の値のコピーです。これを変更しても、環境には影響しません。 環境変数の値を変更するには、[_putenv_s、_wputenv_s](putenv-s-wputenv-s.md) 関数を使います。

**_wdupenv_s**は、 **_dupenv_s**のワイド文字バージョンです。 **_wdupenv_s**の引数はワイド文字列です。 **_Wenviron**グローバル変数は、 **_environ**のワイド文字バージョンです。 **_Wenviron**の詳細については、 [getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)の解説を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_dupenv_s.c
#include  <stdlib.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s( &pValue, &len, "pathext" );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s( &pValue, &len, "nonexistentvariable" );
   if ( err ) return -1;
   printf( "nonexistentvariable = %s\n", pValue );
   free( pValue ); // It's OK to call free with NULL
}
```

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[環境定数](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg、_wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s、_wputenv_s](putenv-s-wputenv-s.md)<br/>
