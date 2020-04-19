---
title: _mbclen、mblen、_mblen_l、_mbclen_l
description: Microsoft C ランタイムライブラリ (CRT) の _mbclen、mblen、_mblen_l、および _mbclen_l の各関数について説明します。
ms.date: 01/08/2020
api_name:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 4676d850448af386a5aface69f616a4ac6f85cbf
ms.sourcegitcommit: 7bd3567fc6a0e7124aab51cad63bbdb44a99a848
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755070"
---
# <a name="_mbclen-mblen-_mblen_l-_mbclen_l"></a>_mbclen、mblen、_mblen_l、_mbclen_l

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

*c*\
マルチバイト文字。

*mbstr*\
マルチバイト文字のバイト シーケンスのアドレス。

*カウント*\
チェックするバイト数。

*ロケール*\
使用するロケール。

## <a name="return-value"></a>戻り値

**_mbclen**と **_mbclen_l**は、マルチバイト文字*c*の長さに従って1または2を返します。 関数は、 *c*がマルチバイトであるかどうかにかかわらず、常に utf-8 に対して1を返します。 **_Mbclen**のエラーは返されません。

*Mbstr*が**NULL**でない場合、 **mblen**と **_mblen_l**はマルチバイト文字の長さをバイト単位で返します。 **Mblen**関数と **_mblen_l**関数は、utf-8 では正しく動作し、1 ~ 3 の値を返す場合があります。 *Mbstr*が**null** (またはワイド文字の null 文字を指している) の場合、 **mblen**と **_mblen_l**は0を返します。 *Mbstr*が指すオブジェクトは、最初の*カウント*文字の中で有効なマルチバイト文字を形成する必要があります。または、 **mblen**と **_mblen_l**は-1 を返します。

## <a name="remarks"></a>Remarks

**_Mbclen**関数は、マルチバイト文字*c*の長さをバイト単位で返します。 *C*がマルチバイト文字の先行バイトを指していない場合 ( [_ismbblead](ismbblead-ismbblead-l.md)への暗黙的な呼び出しによって決定された場合)、 **_mbclen**の結果は予測できません。

有効なマルチバイト文字の場合、 **mblen**は*mbstr*の長さをバイト単位で返します。 また、コードページに関連付けられているマルチバイト文字の有効性も確認します。 **mblen**は、 *mbstr*に含まれているが**MB_CUR_MAX**バイト数以下のバイト*数*を調べます。

出力値は、ロケールの**LC_CTYPE**カテゴリの設定に影響されます。 **_L**サフィックスが付いていないこれらの関数のバージョンは、このロケールに依存する動作に現在のロケールを使用します。 **_L**サフィックスが付いたバージョンは同じように動作しますが、渡されたロケールパラメーターを代わりに使用します。 詳細については、「 [setlocale](setlocale-wsetlocale.md)と[ロケール](../../c-runtime-library/locale.md)」を参照してください。

**_mbclen**、 **_mblen_l**、および **_mbclen_l**は、標準 C ライブラリの一部ではなく、Microsoft 固有のものです。 移植性のあるコードを作成する場合は、使用しないことをお勧めします。 標準 C 互換の場合は、代わりに**mblen**または**mbrlen**を使用します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|マクロまたはインライン関数にマップされます|**_mbclen**|マクロまたはインライン関数にマップされます|

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_mbclen**|\<mbstring.h>|
|**mblen**|\<stdlib.h>|
|**_mblen_l**|\<stdlib.h>|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="example"></a>使用例

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

[文字分類](../../c-runtime-library/character-classification.md)\
[ロケール](../../c-runtime-library/locale.md)\
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
[_mbccpy、_mbccpy_l](mbccpy-mbccpy-l.md)\
[mbrlen](mbrlen.md)\
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)
