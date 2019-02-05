---
title: _mbclen、mblen、_mblen_l、_mbclen_l
ms.date: 01/22/2019
apiname:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
apilocation:
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mblen
- ftclen
- _mbclen
- _mbclen_l
- tclen
- _ftclen
- _tclen
- mbclen
helpviewer_keywords:
- tclen function
- _mblen_l function
- _tclen function
- mblen_l function
- _mbclen function
- _mbclen_l function
- mbclen function
- mblen function
ms.assetid: d5eb92a0-b7a3-464a-aaf7-9890a8e3ed70
ms.openlocfilehash: b7888b0b8c87a632dcbb63f54ade11080c7a309a
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702961"
---
# <a name="mbclen-mblen-mblenl-mbclenl"></a>_mbclen、mblen、_mblen_l、_mbclen_l

長さを取得し、マルチバイト文字の有効性を決定します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
size_t _mbclen(
   const unsigned char *c
);
size_t _mbclen_l(
   unsigned char const* c,
   _locale_t locale
);
int mblen(
   const char *mbstr,
   size_t count
);
int _mblen_l(
   const char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*c*<br/>
マルチバイト文字。

*mbstr*<br/>
マルチバイト文字のバイト シーケンスのアドレス。

*count*<br/>
チェックするバイト数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**_mbclen**かどうかに従って、1 または 2 を返します、マルチバイト文字*c* 1 または 2 バイト長。 戻り値エラーがない **_mbclen**します。 場合*mbstr*いない**NULL**、 **mblen**マルチバイト文字のバイト単位の長さを返します。 場合*mbstr*は**NULL**またはワイド文字の null 文字を指す**mblen** 0 を返します。 ときに、オブジェクトを*mbstr*へのポインターは、その中で有効なマルチバイト文字を形成しない*カウント*文字、 **mblen** -1 を返します。

## <a name="remarks"></a>Remarks

**_Mbclen**関数は、マルチバイト文字のバイト単位の長さを返します*c*します。 場合*c*への暗黙的な呼び出しによって決定されるマルチバイト文字の先行バイトを指していません **_ismbblead**の結果 **_mbclen**は予測できません。

**mblen**のバイトの長さを返します*mbstr*場合は、有効なマルチバイト文字し、コード ページに関連付けられているマルチバイト文字の有効性を判断します。 **mblen**検査*カウント*に含まれている以下のバイト*mbstr*、最大**MB_CUR_MAX**バイト。

出力値を受ける、 **LC_CTYPE**ロケールのカテゴリの設定; を参照してください[setlocale](setlocale-wsetlocale.md)詳細についてはします。 この関数のバージョン、 **_l**サフィックスは、このロケールに依存する動作の現在のロケールを使用します。 **_L**サフィックスが付いたバージョンも、同様に動作が、代わりに渡されたロケール パラメーターを使用します。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|マクロまたはインライン関数にマップされます|**_mbclen**|マクロまたはインライン関数にマップされます|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_mbclen**|\<mbstring.h>|
|**mblen**|\<stdlib.h>|
|**_mblen_l**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_mblen.c
/* illustrates the behavior of the mblen function
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    int      i;
    char    *pmbc = (char *)malloc( sizeof( char ) );
    wchar_t  wc   = L'a';

    printf( "Convert wide character to multibyte character:\n" );
    wctomb_s( &i, pmbc, sizeof(char), wc );
    printf( "   Characters converted: %u\n", i );
    printf( "   Multibyte character: %x\n\n", *pmbc );

    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of multibyte character %x: %u\n", *pmbc, i );

    pmbc = NULL;
    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of NULL multibyte character %x: %u\n", pmbc, i );
}
```

```Output
Convert wide character to multibyte character:
   Characters converted: 1
   Multibyte character: 61

Length in bytes of multibyte character 61: 1
Length in bytes of NULL multibyte character 0: 0
```

## <a name="see-also"></a>関連項目

[文字分類](../../c-runtime-library/character-classification.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbccpy、_mbccpy_l](mbccpy-mbccpy-l.md)<br/>
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
