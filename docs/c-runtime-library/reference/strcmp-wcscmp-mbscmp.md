---
title: strcmp、wcscmp、_mbscmp、_mbscmp_l
ms.date: 01/22/2019
api_name:
- wcscmp
- _mbscmp
- _mbscmp_l
- strcmp
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscmp
- _mbscmp_l
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- _mbscmp_l function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
ms.openlocfilehash: 4bef0c61122e93bd45bc0d1238030743f1196d9e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957955"
---
# <a name="strcmp-wcscmp-_mbscmp-_mbscmp_l"></a>strcmp、wcscmp、_mbscmp、_mbscmp_l

文字列を比較します。

> [!IMPORTANT]
> **_mbscmp**と **_mbscmp_l**は、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int strcmp(
   const char *string1,
   const char *string2
);
int wcscmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _mbscmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*string1*、 *string2*<br/>
Null で終わる比較対象の文字列。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

これらの各関数の戻り値は、 *string1*と*string2*の序数の関係を示します。

|値|string1 と string2 との関係|
|-----------|----------------------------------------|
|< 0|*string1*が*string2*未満です|
|0|*string1*は*string2*と同じ|
|> 0|*string1*が*string2*を超えています。|

パラメーターの検証エラーが発生した場合、_mbscmp と **_mbscmp_l**は **_NLSCMPERROR**を\<返します。これは\<、および mbstring.h > > で定義されています。

## <a name="remarks"></a>Remarks

**Strcmp**関数は、 *string1*と*string2*の序数の比較を実行し、それらのリレーションシップを示す値を返します。 **wcscmp**と **_mbscmp**は、それぞれ、 **strcmp**のワイド文字バージョンとマルチバイト文字バージョンです。 **_mbscmp**は、現在のマルチバイトコードページに従ってマルチバイト文字のシーケンスを認識し、エラーが発生した場合は **_NLSCMPERROR**を返します。 **_mbscmp_l**の動作は同じですが、現在のロケールの代わりに渡されたロケールパラメーターを使用します。 詳細については、「[コード ページ](../../c-runtime-library/code-pages.md)」をご覧ください。 また、 *string1*または*string2*が null ポインターの場合、 **_mbscmp**は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、 **_mbscmp**と **_mbscmp_l**は **_NLSCMPERROR**を返し、 **errno**を**EINVAL**に設定します。 **strcmp**と**wcscmp**は、パラメーターを検証しません。 それ以外では、これらの関数の動作は同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

Strcmp**関数は**、 **strcoll 系**関数とは異なります。これは、 **strcmp**比較は序数であり、ロケールの影響を受けません。 **strcoll 系**は、現在のロケールの**LC_COLLATE**カテゴリを使用して辞書式文字列を比較します。 **LC_COLLATE**カテゴリの詳細については、「 [setlocale、_wsetlocale](setlocale-wsetlocale.md)」を参照してください。

"C"ロケールでは、文字セット (ASCII 文字セット) 内の文字の順序は、辞書式文字順序と同じです。 ただし、その他のロケールでは、文字セット内の文字の順序が辞書式順序と異なる場合があります。 たとえば、ヨーロッパの一部のロケールでは、文字 'a' (値 0x61) は文字セットで文字 'ä' (値 0xE4) の前にありますが、辞書式の順序では文字 'ä' が文字 'a' の前にあります。

文字セットと辞書式文字順序が異なるロケールでは、文字列の辞書式比較に**strcmp**ではなく**strcoll 系**を使用できます。 または、元の文字列で**strxfrm**を使用し、結果の文字列で**strcmp**を使用することもできます。

**Strcmp**関数では大文字と小文字が区別されます。 stricmp、 **wcsicmp 、および\_**  **\_**  **mbsicmp\_** 文字列を小文字形式に変換して比較します。 ASCII テーブルの ' Z ' と ' a ' の間にある文字を含む2つの文字列 (' ['、\\' '、'] '、' ^ '、' _ '、および\`' ') は、大文字と小文字によって異なる方法で比較されます。 たとえば、2つの文字列 "ABCDE...Z" と "ABCD ^" は、比較が小文字 ("abcde...z" > "abcd ^") である場合は1つの方法、比較が大文字の場合は "ABCDE...Z" < "ABCD ^") と比較されます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strcmp**|\<string.h>|
|**wcscmp**|\<string.h> または \<wchar.h>|
|**_mbscmp**|\<mbstring.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_strcmp.c

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown dog jumps over the lazy fox";

int main( void )
{
   char tmp[20];
   int result;

   // Case sensitive
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );
   result = strcmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof (tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
   The quick brown dog jumps over the lazy fox
   The QUICK brown dog jumps over the lazy fox

   strcmp:   String 1 is greater than string 2
   _stricmp:  String 1 is equal to string 2
```

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp、_memicmp_l](memicmp-memicmp-l.md)<br/>
[strcoll 系関数](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
