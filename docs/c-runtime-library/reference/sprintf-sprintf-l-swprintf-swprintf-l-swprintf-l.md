---
title: sprintf、_sprintf_l、swprintf、_swprintf_l、__swprintf_l
ms.date: 11/04/2016
api_name:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _stprintf_l
- __swprintf_l
- sprintf_l
- swprintf
- _sprintf_l
- sprintf
- _stprintf
- stprintf_l
helpviewer_keywords:
- _swprintf_l function
- _stprintf function
- __swprintf_l function
- stprintf function
- sprintf function
- _sprintf_l function
- _stprintf_l function
- swprintf function
- strings [C++], writing to
- _CRT_NON_CONFORMING_SWPRINTFS
- swprintf_l function
- stprintf_l function
- sprintf_l function
- formatted text [C++]
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
ms.openlocfilehash: c9a306788045fc6fe52da835029d32cfc42c0ed4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958291"
---
# <a name="sprintf-_sprintf_l-swprintf-_swprintf_l-__swprintf_l"></a>sprintf、_sprintf_l、swprintf、_swprintf_l、__swprintf_l

文字列に書式付きデータを書き込みます。 これらの関数のセキュリティを強化したバージョンについては、「[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)」をご覧ください。 **Swprintf**と**swprintf_l**のセキュリティで保護されたバージョンは、 *count*パラメーターを受け取りません。

## <a name="syntax"></a>構文

```C
int sprintf(
   char *buffer,
   const char *format [,
   argument] ...
);
int _sprintf_l(
   char *buffer,
   const char *format,
   locale_t locale [,
   argument] ...
);
int swprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument]...
);
int _swprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
int __swprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int sprintf(
   char (&buffer)[size],
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _sprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
出力の格納場所。

*count*<br/>
この関数の Unicode バージョンで格納する最大文字数。

*format*<br/>
書式指定文字列。

*argument*<br/>
省略可能な引数。

*locale*<br/>
使用するロケール。

詳細については、「 [printf 関数と wprintf 関数の書式指定フィールド](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)」を参照してください。

## <a name="return-value"></a>戻り値

書き込まれた文字数。エラーが発生した場合は-1。 *Buffer*または*format*が null ポインターの場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**を**EINVAL**に設定します。

**sprintf**は、*バッファー*に格納されているバイト数を返します。終端の null 文字はカウントされません。 **swprintf**は、*バッファー*に格納されているワイド文字の数を返します。終端の null ワイド文字はカウントされません。

## <a name="remarks"></a>Remarks

**Sprintf**関数は、一連の文字と値の書式を設定し、*バッファー*に格納します。 各*引数*(存在する場合) は、対応する書式指定に従って変換および出力さ*れます。* 形式は通常の文字で構成され、 [printf](printf-printf-l-wprintf-wprintf-l.md)の*format*引数と同じ形式と機能を持ちます。 最後に書き込まれる文字の後に NULL 文字が追加されます。 重なり合う文字列間でコピーした場合の動作は未定義です。

> [!IMPORTANT]
> **Sprintf**を使用すると、書き込まれる文字数を制限することはできません。これは、 **sprintf**を使用するコードがバッファーオーバーランの影響を受ける可能性があることを意味します。 *Buffer*に書き込む最大文字数を指定する、関連する関数[_snprintf](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)を使用することを検討してください。または、バッファーが必要なサイズを決定するために[scprintf](scprintf-scprintf-l-scwprintf-scwprintf-l.md)を使用します。 また、*形式*がユーザー定義の文字列ではないことを確認します。

**swprintf**は、 **sprintf**のワイド文字バージョンです。**swprintf**へのポインター引数はワイド文字列です。 **Swprintf**でのエンコードエラーの検出は、 **sprintf**の場合とは異なる場合があります。 **swprintf**と**fwprintf**は同じように動作しますが、 **Swprintf**は出力を型**ファイル**の出力先ではなく文字列に書き込みます。 **swprintf**では、 *count*パラメーターで最大数を指定する必要があります。書き込まれる文字の。 **_L**サフィックスを持つこれらの関数のバージョンは、現在のスレッドロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

**swprintf**は ISO C 規格に準拠しています。これには、 **size_t**型の2番目のパラメーター *count*が必要です。 古い非標準の動作を強制するには、 **_CRT_NON_CONFORMING_SWPRINTFS**を定義します。 この古い動作は、将来的には削除される可能性があるので、規格に準拠した新しい動作を使用するようにコードを変更する必要があります。

C++ では、これらの関数にテンプレートのオーバーロードがあります。このオーバーロードは、これらの関数に対応するセキュリティで保護された新しい関数を呼び出します。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf**|**sprintf**|**sprintf**|**_swprintf**|
|**stprintf_l (_d)**|**_sprintf_l**|**_sprintf_l**|**__swprintf_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**sprintf**、 **_sprintf_l**|\<stdio.h>|
|**swprintf**、 **swprintf_l**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_sprintf.c
// compile with: /W3
// This program uses sprintf to format various
// data and place them in the string named buffer.

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996
   // Note: sprintf is deprecated; consider using sprintf_s instead

   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example"></a>例

```C
// crt_swprintf.c
// wide character example
// also demonstrates swprintf returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf 系関数](../../c-runtime-library/vprintf-functions.md)<br/>
