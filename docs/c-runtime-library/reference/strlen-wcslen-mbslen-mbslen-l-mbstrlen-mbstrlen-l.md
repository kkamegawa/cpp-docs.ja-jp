---
title: strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l
ms.date: 11/04/2016
api_name:
- _mbslen
- _mbslen_l
- _mbstrlen
- wcslen
- _mbstrlen_l
- strlen
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstrlen
- wcslen
- _tcslen
- _ftcslen
- strlen
- _mbslen
helpviewer_keywords:
- wcslen function
- string length, getting
- ftcslen function
- lengths, strings
- mbstrlen_l function
- _mbslen_l function
- _tcslen function
- mbslen_l function
- mbslen function
- _mbstrlen function
- strings [C++], getting length
- mbstrlen function
- _mbstrlen_l function
- _ftcslen function
- tcslen function
- strlen function
- _mbslen function
ms.assetid: 16462f2a-1e0f-4eb3-be55-bf1c83f374c2
ms.openlocfilehash: 5b1d3f7483ec96cbcda7c72178613d81747c8060
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947576"
---
# <a name="strlen-wcslen-_mbslen-_mbslen_l-_mbstrlen-_mbstrlen_l"></a>strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l

現在のロケールまたは指定されたロケールを使用し、文字列の長さを取得します。 これらの関数についてセキュリティ保護が強化されたバージョンを使用できます。「[strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l](strnlen-strnlen-s.md)」をご覧ください

> [!IMPORTANT]
> **_mbslen**、 **_mbslen_l**、 **_mbstrlen**、および **_mbstrlen_l**は、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
size_t strlen(
   const char *str
);
size_t wcslen(
   const wchar_t *str
);
size_t _mbslen(
   const unsigned char *str
);
size_t _mbslen_l(
   const unsigned char *str,
   _locale_t locale
);
size_t _mbstrlen(
   const char *str
);
size_t _mbstrlen_l(
   const char *str,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
NULL で終わる文字列。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

これらの各関数は、端末の null を除く、 *str*内の文字数を返します。 **_Mbstrlen**と **_mbstrlen_l**を除き、エラーを示す戻り値は予約されていませ`((size_t)(-1))`ん。これは、文字列に無効なマルチバイト文字が含まれている場合にを返します。

## <a name="remarks"></a>Remarks

**strlen**は文字列を1バイト文字列として解釈するため、文字列にマルチバイト文字が含まれている場合でも、戻り値は常にバイト数と等しくなります。 **wcslen**は、 **strlen**のワイド文字バージョンです。**wcslen**の引数はワイド文字列で、文字数はワイド (2 バイト) 文字で指定します。 それ以外では、 **wcslen**と**strlen**は同じように動作します。

**セキュリティに関するメモ** これらの関数は、バッファー オーバーランが原因で発生する潜在的な脅威の影響を受けます。 バッファー オーバーランは、システムを攻撃するときによく使用される方法であり、その結果、認められていない権限が昇格されます。 詳しくは、「 [バッファー オーバーランの回避](/windows/win32/SecBP/avoiding-buffer-overruns)」をご覧ください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcslen**|**strlen**|**strlen**|**wcslen**|
|**_tcsclen**|**strlen**|**_mbslen**|**wcslen**|
|**_tcsclen_l**|**strlen**|**_mbslen_l**|**wcslen**|

**_mbslen**と **_mbslen_l**は、マルチバイト文字の文字列に含まれるマルチバイト文字の数を返しますが、マルチバイト文字の有効性はテストしません。 **_mbstrlen**と **_mbstrlen_l**は、マルチバイト文字の有効性をテストし、マルチバイト文字のシーケンスを認識します。 **_Mbstrlen**または **_mbstrlen_l**に渡された文字列に、コードページの無効なマルチバイト文字が含まれている場合、この関数は-1 を返し、 **errno**を**EILSEQ**に設定します。

出力値は、ロケールの **LC_CTYPE** カテゴリの設定に影響されます。詳細については、「[setlocale](setlocale-wsetlocale.md)」を参照してください。 **_l** サフィックスが付いていないこれらの関数のバージョンでは、このロケールに依存する動作に現在のロケールを使用します。 **_l** サフィックスが付いているバージョンは、渡されたロケール パラメーターを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strlen**|\<string.h>|
|**wcslen**|\<string.h> または \<wchar.h>|
|**_mbslen**、 **_mbslen_l**|\<mbstring.h>|
|**_mbstrlen**、 **_mbstrlen_l**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_strlen.c
// Determine the length of a string. For the multi-byte character
// example to work correctly, the Japanese language support for
// non-Unicode programs must be enabled by the operating system.

#include <string.h>
#include <locale.h>

int main()
{
   char* str1 = "Count.";
   wchar_t* wstr1 = L"Count.";
   char * mbstr1;
   char * locale_string;

   // strlen gives the length of single-byte character string
   printf("Length of '%s' : %d\n", str1, strlen(str1) );

   // wstrlen gives the length of a wide character string
   wprintf(L"Length of '%s' : %d\n", wstr1, wcslen(wstr1) );

   // A multibyte string: [A] [B] [C] [katakana A] [D] [\0]
   // in Code Page 932. For this example to work correctly,
   // the Japanese language support must be enabled by the
   // operating system.
   mbstr1 = "ABC" "\x83\x40" "D";

   locale_string = setlocale(LC_CTYPE, "Japanese_Japan");

   if (locale_string == NULL)
   {
      printf("Japanese locale not enabled. Exiting.\n");
      exit(1);
   }
   else
   {
      printf("Locale set to %s\n", locale_string);
   }

   // _mbslen will recognize the Japanese multibyte character if the
   // current locale used by the operating system is Japanese
   printf("Length of '%s' : %d\n", mbstr1, _mbslen(mbstr1) );

   // _mbstrlen will recognize the Japanese multibyte character
   // since the CRT locale is set to Japanese even if the OS locale
   // isnot.
   printf("Length of '%s' : %d\n", mbstr1, _mbstrlen(mbstr1) );
   printf("Bytes in '%s' : %d\n", mbstr1, strlen(mbstr1) );

}
```

```Output
Length of 'Count.' : 6
Length of 'Count.' : 6
Length of 'ABCァD' : 5
Length of 'ABCァD' : 5
Bytes in 'ABCァD' : 6
```

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strcat、wcscat、_mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll 系関数](../../c-runtime-library/strcoll-functions.md)<br/>
[strcpy、wcscpy、_mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
