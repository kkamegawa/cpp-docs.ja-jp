---
title: strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l
ms.date: 03/25/2019
api_name:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
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
- _mbstok
- strtok
- _tcstok
- wcstok
helpviewer_keywords:
- mbstok_l function
- strings [C++], searching
- tcstok function
- _tcstok function
- _strtok_l function
- strtok function
- mbstok function
- wcstok_l function
- _mbstok function
- tcstok_l function
- tokens, finding in strings
- _mbstok_l function
- wcstok function
- _wcstok_l function
- _tcstok_l function
- strtok_l function
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
ms.openlocfilehash: 62ed9edc6ec5a7ee60223f1c5e908aa14f421a25
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957652"
---
# <a name="strtok-_strtok_l-wcstok-_wcstok_l-_mbstok-_mbstok_l"></a>strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l

現在のロケールまたは渡された指定のロケールを使用して、文字列内の次のトークンを検索します。 これらの関数にはセキュリティが強化されたバージョンがあります。「[strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)」を参照してください。

> [!IMPORTANT]
> **_mbstok**と **_mbstok_l**は、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
char *strtok(
   char *strToken,
   const char *strDelimit
);
char *strtok_l(
   char *strToken,
   const char *strDelimit,
   _locale_t locale
);
wchar_t *wcstok(
   wchar_t *strToken,
   const wchar_t *strDelimit
);
wchar_t *wcstok_l(
   wchar_t *strToken,
   const wchar_t *strDelimit,
   _locale_t locale
);
unsigned char *_mbstok(
   unsigned char *strToken,
   const unsigned char *strDelimit
);
unsigned char *_mbstok_l(
   unsigned char *strToken,
   const unsigned char *strDelimit,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*strToken*<br/>
トークンを含む文字列。

*strDelimit*<br/>
区切り記号文字のセット。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

*StrToken*で見つかった次のトークンへのポインターを返します。 これらの関数は、トークンが見つからない場合は**NULL**を返します。 各呼び出しは、返されたトークンの後に出現する最初の区切り記号として null 文字を置換することで、 *strToken*を変更します。

## <a name="remarks"></a>Remarks

**Strtok**関数は、 *strToken*内の次のトークンを検索します。 *Strdelimit*の文字セットは、現在の呼び出しの*strToken*にあるトークンの有効な区切り記号を指定します。 **wcstok**と **_mbstok**は、 **strtok**のワイド文字バージョンとマルチバイト文字バージョンです。 **Wcstok**の引数と戻り値はワイド文字列です。これらの **_mbstok**はマルチバイト文字列です。 それ以外では、これらの関数の動作は同じです。

> [!IMPORTANT]
> これらの関数は、バッファー オーバーランが原因で発生する可能性のある問題の影響を受けます。 バッファー オーバーランは、システムを攻撃するときによく使用される方法であり、その結果、認められていない権限が昇格されます。 詳しくは、「 [バッファー オーバーランの回避](/windows/win32/SecBP/avoiding-buffer-overruns)」をご覧ください。

**Strtok**の最初の呼び出しでは、関数は先頭の区切り記号をスキップし、 *strToken*の最初のトークンへのポインターを返し、null 文字でトークンを終了します。 *StrToken*の残りの部分から、 **strtok**の一連の呼び出しによって、より多くのトークンを分割できます。 **Strtok**を呼び出すたびに、その呼び出しによって返された**トークン**の後に null 文字を挿入することによって*strToken*が変更されます。 *StrToken*から次のトークンを読み取るには、 *StrToken*引数に**NULL**値を指定して**strtok**を呼び出します。 **NULL**の*strToken*引数を指定すると、 **strtok**は、変更された*strToken*内の次のトークンを検索します。 *Strdelimit*引数は、区切り記号のセットが異なる可能性があるため、次の呼び出しのいずれかの値を受け取ることができます。

出力値は、ロケールの**LC_CTYPE**カテゴリの設定に影響されます。 詳細については、「[setlocale](setlocale-wsetlocale.md)」をご覧ください。

**_L**サフィックスが付いていないこれらの関数のバージョンは、このロケールに依存する動作に現在のロケールを使用します。 **_L**サフィックスが付いているバージョンは、渡されたロケールパラメーターを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

> [!NOTE]
> 各関数は、文字列をトークンに解析する際にスレッド ローカルの静的変数を使用します。 したがって、複数のスレッドが望ましくない影響を受けずに同時にこれらの関数を呼び出すことができます。 ただし、1 つのスレッド内でこれらの関数のいずれかの呼び出しをインターリーブすると、データの破損や正確でない結果が生成される可能性が非常に高くなります。 さまざまな文字列を解析する際、1 つの文字列の解析を完了してから、次の解析を開始します。 また、別の関数が呼び出されているループから、これらの関数の 1 つを呼び出す場合の危険性にも注意してください。 他の関数が最終的にこれらの関数の 1 つを使用した場合、インターリーブされた呼び出しのシーケンスにより、データの破損を招くことがあります。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strtok**|\<string.h>|
|**wcstok**|\<string.h> または \<wchar.h>|
|**_mbstok**、 **_mbstok_l**|\<mbstring.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_strtok.c
// compile with: /W3
// In this program, a loop uses strtok
// to print all the tokens (separated by commas
// or blanks) in the string named "string".
//
#include <string.h>
#include <stdio.h>

char string[] = "A string\tof ,,tokens\nand some  more tokens";
char seps[]   = " ,\t\n";
char *token;

int main( void )
{
   printf( "Tokens:\n" );

   // Establish string and get the first token:
   token = strtok( string, seps ); // C4996
   // Note: strtok is deprecated; consider using strtok_s instead
   while( token != NULL )
   {
      // While there are tokens in "string"
      printf( " %s\n", token );

      // Get next token:
      token = strtok( NULL, seps ); // C4996
   }
}
```

```Output
Tokens:
A
string
of
tokens
and
some
more
tokens
```

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
