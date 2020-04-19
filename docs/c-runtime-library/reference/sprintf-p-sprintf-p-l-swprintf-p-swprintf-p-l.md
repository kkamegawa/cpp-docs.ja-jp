---
title: _sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l
ms.date: 11/04/2016
api_name:
- _sprintf_p
- _swprintf_p_l
- _swprintf_p
- _sprintf_p_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _sprintf_p
- _swprintf_p_l
- _sprintf_p_l
- _swprintf_p
- sprintf_p
- swprint_p_l
- swprintf_p
- swprintf_p_l
helpviewer_keywords:
- sprintf_p_l function
- swprintf_p function
- swprintf_p_l function
- _sprintf_p function
- _sprintf_p_l function
- _swprintf_p function
- sprintf_p function
- _stprintf_p function
- stprintf_p function
- _swprintf_p_l function
- stprintf_p_l function
- formatted text [C++]
- _stprintf_p_l function
ms.assetid: a2ae78e8-6b0c-48d5-87a9-ea2365b0693d
ms.openlocfilehash: 5bb8993293236a20c87707db06715e9a012e643e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958026"
---
# <a name="_sprintf_p-_sprintf_p_l-_swprintf_p-_swprintf_p_l"></a>_sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l

パラメーターが書式文字列で使用される順序を指定できる文字列に、書式付きデータを書き込みます。

## <a name="syntax"></a>構文

```C
int _sprintf_p(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format [,
   argument_list]
);
int _sprintf_p_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale [,
   argument_list]
);
int _swprintf_p(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format [,
   argument_list]
);
int _swprintf_p_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale [,
   argument_list]
);
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
出力の格納場所。

*sizeOfBuffer*<br/>
格納する最大文字数。

*format*<br/>
書式指定文字列。

*argument_list*<br/>
書式指定文字列への省略可能な引数。

*locale*<br/>
使用するロケール。

詳細については、「 [printf 関数と wprintf 関数の書式指定フィールド](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)」を参照してください。

## <a name="return-value"></a>戻り値

書き込まれた文字数。エラーが発生した場合は-1。

## <a name="remarks"></a>Remarks

**_Sprintf_p**関数は、一連の文字と値の書式を設定し、*バッファー*に格納します。 *Argument_list*内の各引数 (存在する場合) は、*形式*の対応する形式指定に従って変換および出力されます。 *Format*引数は、 [printf 関数と wprintf 関数の書式指定構文](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)を使用します。 最後に書き込まれる文字の後に NULL 文字が追加されます。 重なり合う文字列間でコピーした場合の動作は未定義です。 **_Sprintf_p**と**sprintf_s**の違いは、 **_sprintf_p**は位置指定パラメーターをサポートしている点です。これにより、書式設定文字列で引数を使用する順序を指定できます。 詳細については、「[printf_p の位置指定パラメーター](../../c-runtime-library/printf-p-positional-parameters.md)」をご覧ください。

**_swprintf_p**は、 **_sprintf_p**のワイド文字バージョンです。 **_swprintf_p**へのポインター引数はワイド文字列です。 **_Swprintf_p**でのエンコードエラーの検出は、 **_sprintf_p**の場合とは異なる場合があります。 **_swprintf_p**と**fwprintf_p**は同じように動作しますが、 **_swprintf_p**は、型**ファイル**の出力先ではなく文字列に出力を書き込む点と、 **_swprintf_p**は*count*パラメーターを指定して書き込む最大文字数。 **_L**サフィックスを持つこれらの関数のバージョンは、現在のスレッドロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

**_sprintf_p**は、*バッファー*に格納されているバイト数を返します。終端の null 文字はカウントされません。 **_swprintf_p**は、*バッファー*に格納されているワイド文字の数を返します。終端の null ワイド文字はカウントされません。 *バッファー*または*形式*が null ポインターの場合、または書式指定文字列に無効な書式指定文字が含まれている場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**を**EINVAL**に設定します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_p**|**_sprintf_p**|**_sprintf_p**|**_swprintf_p**|
|**_stprintf_p_l**|**_sprintf_p_l**|**_sprintf_p_l**|**_swprintf_p_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_sprintf_p**、 **_sprintf_p_l**|\<stdio.h>|
|**_swprintf_p**、 **_swprintf_p_l**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_sprintf_p.c
// This program uses _sprintf_p to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
    char     buffer[200],
            s[] = "computer", c = 'l';
    int      i = 35,
            j;
    float    fp = 1.7320534f;

    // Format and print various data:
    j  = _sprintf_p( buffer, 200,
                     "   String:    %s\n", s );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Character: %c\n", c );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Integer:   %d\n", i );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Real:      %f\n", fp );

    printf( "Output:\n%s\ncharacter count = %d\n",
            buffer, j );
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
// crt_swprintf_p.c
// This is the wide character example which
// also demonstrates _swprintf_p returning
// error code.
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    wchar_t buffer[BUFFER_SIZE];
    int     len;

    len = _swprintf_p(buffer, BUFFER_SIZE, L"%2$s %1$d",
                      0, L" marbles in your head.");
    _printf_p( "Wrote %d characters\n", len );

    // _swprintf_p fails because string contains WEOF (\xffff)
    len = _swprintf_p(buffer, BUFFER_SIZE, L"%s",
                      L"Hello\xffff world" );
    _printf_p( "Wrote %d characters\n", len );
}
```

```Output
Wrote 24 characters
Wrote -1 characters
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[_printf_p、_printf_p_l、_wprintf_p、_wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[vprintf 系関数](../../c-runtime-library/vprintf-functions.md)<br/>
[printf_p の位置指定パラメーター](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
