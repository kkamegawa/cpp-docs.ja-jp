---
title: strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l
ms.date: 03/25/2019
api_name:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
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
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
helpviewer_keywords:
- _strtok_s_l function
- _mbstok_s_l function
- strings [C++], searching
- mbstok_s_l function
- wcstok_s_l function
- _wcstok_s_l function
- _tcstok_s function
- _tcstok_s_l function
- strtok_s_l function
- wcstok_s function
- tokens, finding in strings
- mbstok_s function
- _mbstok_s function
- strtok_s function
ms.assetid: 7696c972-f83b-4617-8c82-95973e9fdb46
ms.openlocfilehash: 1bbc5910e6242a0df262cc43b58815ea80ff9681
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946456"
---
# <a name="strtok_s-_strtok_s_l-wcstok_s-_wcstok_s_l-_mbstok_s-_mbstok_s_l"></a>strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l

現在のロケールまたは渡されたロケールを使用して、文字列内の次のトークンを検索します。 これらのバージョンの [strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) は、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」にあるとおり、セキュリティが強化されています。

> [!IMPORTANT]
> **_mbstok_s**と **_mbstok_s_l**は、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
char* strtok_s(
   char* str,
   const char* delimiters,
   char** context
);

char* _strtok_s_l(
   char* str,
   const char* delimiters,
   char** context,
   _locale_t locale
);

wchar_t* wcstok_s(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context
);

wchar_t *_wcstok_s_l(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context,
   _locale_t locale
);

unsigned char* _mbstok_s(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context
);

unsigned char* _mbstok_s_l(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
検索する1つまたは複数のトークンを格納している文字列。

*delimiters*<br/>
使用する区切り文字のセット。

*context*<br/>
関数の呼び出しの間に位置情報を格納するために使用されます。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

*Str*で見つかった次のトークンへのポインターを返します。 トークンが見つからない場合は**NULL**を返します。 各呼び出しは、返されたトークンの後に出現する最初の区切り記号に null 文字を代入することで*str*を変更します。

### <a name="error-conditions"></a>エラー条件

|*str*|*delimiters*|*context*|戻り値|**番号**|
|----------------|------------------|---------------|------------------|-------------|
|**NULL**|任意|null ポインターへのポインター|**NULL**|**EINVAL**|
|任意|**NULL**|任意|**NULL**|**EINVAL**|
|任意|任意|**NULL**|**NULL**|**EINVAL**|

*Str*が**NULL**でも、*コンテキスト*が有効なコンテキストポインターへのポインターである場合、エラーは発生しません。

## <a name="remarks"></a>Remarks

関数の**strtok_s**ファミリは、 *str*内の次のトークンを検索します。 *区切り記号*に含まれる文字セットは、現在の呼び出しの*str*で検索されるトークンの使用可能な区切り記号を指定します。 **wcstok_s**と **_mbstok_s**は、 **strtok_s**のワイド文字バージョンとマルチバイト文字バージョンです。 **Wcstok_s**と **_wcstok_s_l**の引数と戻り値はワイド文字列です。 **_mbstok_s**と **_mbstok_s_l**のこれらはマルチバイト文字列です。 それ以外では、これらの関数の動作は同じです。

この関数は、パラメーターを検証します。 [エラー条件] テーブルのようにエラー状態が発生すると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は**errno**を**EINVAL**に設定し、 **NULL**を返します。

**Strtok_s**の最初の呼び出しでは、関数は先頭の区切り記号をスキップし、 *str*内の最初のトークンへのポインターを返して、トークンを null 文字で終了します。 *Str*の残りの部分から、 **strtok_s**の一連の呼び出しによって、より多くのトークンを分割できます。 **Strtok_s**を呼び出すたびに、その呼び出しによって返されたトークンの後に null 文字を挿入することで*str*が変更されます。 *コンテキスト*ポインターは、読み取られている文字列と、次のトークンが読み取られる文字列内の位置を追跡します。 *Str*から次のトークンを読み取るには、 *Str*引数に**NULL**値を指定して**strtok_s**を呼び出し、同じ*コンテキスト*パラメーターを渡します。 **NULL** *str*引数を指定すると、 **strtok_s**は、変更された*str*内の次のトークンを検索します。 *区切り*記号の引数は、1回の呼び出しから次の呼び出しまでの任意の値を受け取ることができるため、区切り記号のセットが異なる場合があります。

*Context*パラメーターは**strtok**と **_strtok_l**で使用される静的バッファーよりも優先されるため、同じスレッドで2つの文字列を同時に解析することができます。

出力値は、ロケールの**LC_CTYPE**カテゴリの設定に影響されます。 詳細については、「[setlocale](setlocale-wsetlocale.md)」をご覧ください。

**_L**サフィックスが付いていないこれらの関数のバージョンでは、このロケールに依存する動作に現在のスレッドロケールが使用されます。 **_L**サフィックスが付いているバージョンは、 *locale*パラメーターで指定されたロケールを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**、<br />**_wcstok_s_l**|\<string.h> または \<wchar.h>|
|**_mbstok_s**、<br />**_mbstok_s_l**|\<mbstring.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|\_UNICODE & \_MBCS が定義されていません|\_定義済みの MBCS|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok_s**|**strtok_s**|**_mbstok_s**|**wcstok_s**|
|**_tcstok_s_l**|**_strtok_s_l**|**_mbstok_s_l**|**_wcstok_s_l**|

## <a name="example"></a>例

```C
// crt_strtok_s.c
// In this program, a loop uses strtok_s
// to print all the tokens (separated by commas
// or blanks) in two strings at the same time.

#include <string.h>
#include <stdio.h>

char string1[] =
    "A string\tof ,,tokens\nand some  more tokens";
char string2[] =
    "Another string\n\tparsed at the same time.";
char seps[]   = " ,\t\n";
char *token1 = NULL;
char *token2 = NULL;
char *next_token1 = NULL;
char *next_token2 = NULL;

int main(void)
{
    printf("Tokens:\n");

    // Establish string and get the first token:
    token1 = strtok_s(string1, seps, &next_token1);
    token2 = strtok_s(string2, seps, &next_token2);

    // While there are tokens in "string1" or "string2"
    while ((token1 != NULL) || (token2 != NULL))
    {
        // Get next token:
        if (token1 != NULL)
        {
            printf(" %s\n", token1);
            token1 = strtok_s(NULL, seps, &next_token1);
        }
        if (token2 != NULL)
        {
            printf("        %s\n", token2);
            token2 = strtok_s(NULL, seps, &next_token2);
        }
    }
}
```

```Output
Tokens:
A
        Another
string
        string
of
        parsed
tokens
        at
and
        the
some
        same
more
        time.
tokens
```

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
