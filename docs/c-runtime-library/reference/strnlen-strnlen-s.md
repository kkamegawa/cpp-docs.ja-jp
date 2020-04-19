---
title: strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l
ms.date: 11/04/2016
api_name:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
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
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
ms.openlocfilehash: 6613c79bd9637b857dbf825eca2b37c71c154bec
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946996"
---
# <a name="strnlen-strnlen_s-wcsnlen-wcsnlen_s-_mbsnlen-_mbsnlen_l-_mbstrnlen-_mbstrnlen_l"></a>strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l

現在のロケールまたは渡されたロケールを使用して、文字列の長さを取得します。 これらは、[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md) のセキュリティを強化したバージョンです。

> [!IMPORTANT]
> **_mbsnlen**、 **_mbsnlen_l**、 **_mbstrnlen**、および **_mbstrnlen_l**は、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
size_t strnlen(
   const char *str,
   size_t numberOfElements
);
size_t strnlen_s(
   const char *str,
   size_t numberOfElements
);
size_t wcsnlen(
   const wchar_t *str,
   size_t numberOfElements
);
size_t wcsnlen_s(
   const wchar_t *str,
   size_t numberOfElements
);
size_t _mbsnlen(
   const unsigned char *str,
   size_t numberOfElements
);
size_t _mbsnlen_l(
   const unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
size_t _mbstrnlen(
   const char *str,
   size_t numberOfElements
);
size_t _mbstrnlen_l(
   const char *str,
   size_t numberOfElements,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
NULL で終わる文字列。

*numberOfElements*<br/>
文字列バッファーのサイズ。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

これらの関数は、文字列内の文字数を返します (終端の null 文字は含まれません)。 文字列の最初の*numberofelements*バイト (または**wcsnlen**のワイド文字) 内に null 終端文字がない場合は、エラー状態を示す*numberofelements*が返されます。null で終わる文字列には、 *Numberofelements*より厳密に小さい長さがあります。

**_mbstrnlen**と **_mbstrnlen_l**文字列に無効なマルチバイト文字が含まれている場合は、-1 を返します。

## <a name="remarks"></a>Remarks

> [!NOTE]
> **strnlen**は**strlen**に代わるものではありません。**strnlen**は、既知のサイズのバッファー (ネットワークパケットなど) の受信した信頼できないデータのサイズを計算するためにのみ使用することを目的としています。 **strnlen**は長さを計算しますが、文字列が終了していない場合は、バッファーの末尾を越えていません。 その他の状況では、 **strlen**を使用します。 ( **Wcsnlen**、 **_mbsnlen**、および **_mbstrnlen**にも同じことが当てはまります)。

これらの関数は、 *str*の文字数を返します。終端の null 文字は含まれません。 ただし、 **strnlen**と**strnlen_s**は文字列を1バイト文字列として解釈するため、文字列にマルチバイト文字が含まれている場合でも、戻り値は常にバイト数と等しくなります。 **wcsnlen**と**wcsnlen_s**はそれぞれ**strnlen**と**strnlen_s**のワイド文字バージョンです。**wcsnlen**と**wcsnlen_s**の引数はワイド文字列で、文字数はワイド文字単位です。 それ以外の場合、 **wcsnlen**と**strnlen**は、 **strnlen_s**と**wcsnlen_s**と同じように動作します。

**strnlen**、 **wcsnlen**、および **_mbsnlen**では、パラメーターは検証されません。 *Str*が**NULL**の場合、アクセス違反が発生します。

**strnlen_s**と**wcsnlen_s**は、そのパラメーターを検証します。 *Str*が**NULL**の場合、関数は0を返します。

**_mbstrnlen**もそのパラメーターを検証します。 *Str*が**NULL**の場合、または*numberofelements*が**INT_MAX**より大きい場合、 **_mbstrnlen**は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーター例外を生成します。 実行の継続が許可された場合、 **_mbstrnlen**は**errno**を**EINVAL**に設定し、-1 を返します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen**と **_mbstrnlen**は、マルチバイト文字列のマルチバイト文字数を返します。 **_mbsnlen**は、現在使用されているマルチバイトコードページに従って、または渡されたロケールに従って、マルチバイト文字のシーケンスを認識します。マルチバイト文字の有効性はテストされません。 **_mbstrnlen**は、マルチバイト文字の有効性をテストし、マルチバイト文字のシーケンスを認識します。 **_Mbstrnlen**に渡された文字列に無効なマルチバイト文字が含まれている場合、 **errno**は**EILSEQ**に設定されます。

出力値は、ロケールの**LC_CTYPE**カテゴリの設定に影響されます。詳細については[、「setlocale、_wsetlocale](setlocale-wsetlocale.md) 」を参照してください。 これらの関数のバージョンは同じですが、 **_l**サフィックスが付いていないバージョンでは、このロケールに依存する動作に現在のロケールを使用し、 **_l**サフィックスが付いているバージョンは渡されたロケールパラメーターを代わりに使用する点が異なります。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strnlen**、 **strnlen_s**|\<string.h>|
|**wcsnlen**、 **wcsnlen_s**|\<string.h> または \<wchar.h>|
|**_mbsnlen**、 **_mbsnlen_l**|\<mbstring.h>|
|**_mbstrnlen**、 **_mbstrnlen_l**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_strnlen.c

#include <string.h>

int main()
{
   // str1 is 82 characters long. str2 is 159 characters long

   char* str1 = "The length of a string is the number of characters\n"
               "excluding the terminating null.";
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"
                "than the maximum size specified, the maximum size is\n"
                "returned rather than the actual size of the string.";
   size_t len;
   size_t maxsize = 100;

   len = strnlen(str1, maxsize);
   printf("%s\n Length: %d \n\n", str1, len);

   len = strnlen(str2, maxsize);
   printf("%s\n Length: %d \n", str2, len);
}
```

```Output
The length of a string is the number of characters
excluding the terminating null.
Length: 82

strnlen takes a maximum size. If the string is longer
than the maximum size specified, the maximum size is
returned rather than the actual size of the string.
Length: 100
```

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strcoll 系関数](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
