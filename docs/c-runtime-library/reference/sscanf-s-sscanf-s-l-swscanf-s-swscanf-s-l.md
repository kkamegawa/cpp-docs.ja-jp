---
title: sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l
ms.date: 11/04/2016
api_name:
- _sscanf_s_l
- sscanf_s
- _swscanf_s_l
- swscanf_s
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _stscanf_s
- sscanf_s
- swscanf_s
- _swscanf_s_l
- _stscanf_s_l
- _sscanf_s_l
helpviewer_keywords:
- stscanf_s_l function
- stscanf_s function
- swscanf_s function
- swscanf_s_l function
- sscanf_s_l function
- _stscanf_s_l function
- strings [C++], reading data from
- sscanf_s function
- _swscanf_s_l function
- _stscanf_s function
- reading data, strings
- strings [C++], reading
- _sscanf_s_l function
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
ms.openlocfilehash: 14707b64a9c5c49837391be59d83ee39b79d5065
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957965"
---
# <a name="sscanf_s-_sscanf_s_l-swscanf_s-_swscanf_s_l"></a>sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l

文字列から書式付きデータを読み込みます。 これらのバージョンの [sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md) は、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」にあるとおり、セキュリティが強化されています。

## <a name="syntax"></a>構文

```C
int sscanf_s(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_s_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf_s(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_s_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
格納されるデータ。

*format*<br/>
書式指定文字列。 詳細については、「[Format Specification Fields: scanf and wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)」(scanf 関数と wscanf 関数の書式指定フィールド) をご覧ください。

*argument*<br/>
省略可能な引数。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

これらの関数は、正常に変換および代入されたフィールドの数を返します。読み込まれただけで代入されなかったフィールドは戻り値には含まれません。 戻り値が 0 の場合は、代入されたフィールドがなかったことを示します。 エラーの場合、または最初の変換の前に文字列の末尾に到達した場合、戻り値は**EOF**になります。

*Buffer*または*format*が**NULL**ポインターの場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**を**EINVAL**に設定します。

エラー コードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**Sscanf_s**関数は、各*引数*によって指定された場所に*バッファー*からデータを読み取ります。 書式指定文字列の後の引数は、*形式*の型指定子に対応する型を持つ変数へのポインターを指定します。 安全性の低いバージョン[sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md)とは異なり、 **[]** で囲まれている型フィールド文字**c**、 **c**、 **s**、 **s**、または文字列コントロールセットを使用する場合は、バッファーサイズのパラメーターが必要です。 バッファー サイズ (文字単位) は、バッファー サイズが必要な各バッファーの後に追加パラメーターとして指定する必要があります。 たとえば、文字列を読み込む場合、その文字列のバッファー サイズは次のように渡されます。

```C
wchar_t ws[10];
swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9
```

バッファー サイズには、終端 null も含まれます。 読み取られたトークンがバッファーに確実に収まるように、幅指定フィールドが使用される場合もあります。 幅指定フィールドが使用されない場合で、読み取られたトークンがバッファーに収まらない場合、そのバッファーには何も書き込まれません。

文字の場合、次のように 1 文字読み込む場合もあります。

```C
wchar_t wc;
swscanf_s(in_str, L"%c", &wc, 1);
```

次に、この例では、入力文字列とデータ ストアから 1 つの文字をワイド文字バッファーに読み込みます。 null で終わらない文字列に対して複数の文字列を読み込む場合、幅指定とバッファー サイズとして符号なし整数が使用されます。

```C
char c[4];
sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated
```

詳細については、「[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)」と「[scanf 関数の型フィールド文字](../../c-runtime-library/scanf-type-field-characters.md)」を参照してください。

> [!NOTE]
> Size パラメーターは、 **size_t**ではなく**unsigned**型です。 64ビットターゲットのコンパイル時には、静的なキャストを使用して、または**sizeof** **の**結果を正しいサイズに変換します。

*Format*引数は、入力フィールドの解釈を制御し、 **scanf_s**関数の*format*引数と同じ形式と機能を持ちます。 重なり合う文字列間でコピーした場合の動作は未定義です。

**swscanf_s**は、 **sscanf_s**のワイド文字バージョンです。**swscanf_s**の引数はワイド文字列です。 **sscanf_s**では、マルチバイトの16進文字は処理されません。 **swscanf_s**では、Unicode の全角16進数または "互換ゾーン" の文字は処理されません。 それ以外の場合、 **swscanf_s**と**sscanf_s**は同じように動作します。

**_L**サフィックスが付いているこれらの関数のバージョンは、現在のスレッドロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**stscanf_s (_d)**|**sscanf_s**|**sscanf_s**|**swscanf_s**|
|**_stscanf_s_l**|**_sscanf_s_l**|**_sscanf_s_l**|**_swscanf_s_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**sscanf_s**、 **_sscanf_s_l**|\<stdio.h>|
|**swscanf_s**、 **_swscanf_s_l**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_sscanf_s.c
// This program uses sscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string plus null terminator
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );
   sscanf_s( tokenstring, "%d", &i );
   sscanf_s( tokenstring, "%f", &fp );

   // Output the data read
   printf_s( "String    = %s\n", s );
   printf_s( "Character = %c\n", c );
   printf_s( "Integer:  = %d\n", i );
   printf_s( "Real:     = %f\n", fp );
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf、_snprintf、_snprintf_l、_snwprintf、_snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
