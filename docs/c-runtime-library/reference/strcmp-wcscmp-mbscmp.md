---
title: strcmp、wcscmp、_mbscmp、_mbscmp_l
ms.date: 01/22/2019
apiname:
- wcscmp
- _mbscmp
- _mbscmp_l
- strcmp
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: dae5e04809ac7312097cb418ab5ffd561fdbd1d1
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703156"
---
# <a name="strcmp-wcscmp-mbscmp-mbscmpl"></a>strcmp、wcscmp、_mbscmp、_mbscmp_l

文字列を比較します。

> [!IMPORTANT]
> **_mbscmp**と **_mbscmp_l** Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

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

*string1*, *string2*<br/>
Null で終わる比較対象の文字列。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

これらの各関数の戻り値の序数に基づく関係を示す*string1*に*string2*します。

|[値]|string1 と string2 との関係|
|-----------|----------------------------------------|
|< 0|*string1*がより小さい*string2*|
|0|*string1*ヲェヒェケェ ・ *string2*|
|> 0|*string1*がより大きい*string2*|

パラメーター検証エラー、 **_mbscmp**と **_mbscmp_l**返す**すると**、定義されている\<string.h > と\<mbstring.h >。

## <a name="remarks"></a>Remarks

**Strcmp**関数実行の序数に基づく比較*string1*と*string2*の関係を示す値を返します。 **wcscmp**と **_mbscmp**は、それぞれ、ワイド文字とマルチバイト文字のバージョンの**strcmp**します。 **_mbscmp**現在のマルチバイト コード ページに従ってマルチバイト文字シーケンスを認識し、返します**すると**エラーが発生します。 **_mbscmp_l**同じ動作ですが、現在のロケールの代わりに渡されるロケール パラメーターを使用します。 詳細については、「[コード ページ](../../c-runtime-library/code-pages.md)」をご覧ください。 また場合、 *string1*または*string2* null ポインターの場合は、 **_mbscmp**で説明されているように、無効なパラメーター ハンドラーを呼び出します[パラメーターの検証](../../c-runtime-library/parameter-validation.md). 続けるには、実行が許可された場合 **_mbscmp**と **_mbscmp_l**返す**すると**設定と**errno**に**EINVAL**. **strcmp**と**wcscmp**パラメーターを検証できません。 それ以外では、これらの関数の動作は同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

**Strcmp**とは異なり、 **strcoll 系**関数で**strcmp**比較は序数に基づく、およびロケールの影響は受けません。 **strcoll 系**を使用して文字列を辞書順比較、 **LC_COLLATE**の現在のロケールのカテゴリ。 詳細については、 **LC_COLLATE**カテゴリを参照してください[setlocale、_wsetlocale](setlocale-wsetlocale.md)します。

"C"ロケールでは、文字セット (ASCII 文字セット) 内の文字の順序は、辞書式文字順序と同じです。 ただし、その他のロケールでは、文字セット内の文字の順序が辞書式順序と異なる場合があります。 たとえば、ヨーロッパの一部のロケールでは、文字 'a' (値 0x61) は文字セットで文字 'ä' (値 0xE4) の前にありますが、辞書式の順序では文字 'ä' が文字 'a' の前にあります。

対象の文字セットと辞書式文字順序が異なるロケールで使用することができます**strcoll 系**の代わりに**strcmp**の文字列の辞書式比較します。 また、使用することができます**strxfrm**しを使用して、元の文字列で**strcmp**結果の文字列にします。

**Strcmp**関数は大文字小文字を区別します。 **\_stricmp**、  **\_wcsicmp**、および **\_mbsicmp**最初に変換してに小文字の形式の文字列を比較します。 'Z' の間にある文字が含まれている 2 つの文字列と ASCII の表の 'a' ('['、'\\'、']'、' ^'、'_' と'\`')、大文字と小文字によって異なる方法で、比較します。 たとえば、2 つの文字列"ABCDE"と"ABCD ^"場合は、比較では、小文字、1 つの方法を比較 ("abcde">"abcd ^") と、その他の方法 ("ABCDE"<"ABCD ^")、比較が大文字の場合。

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
