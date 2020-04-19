---
title: vscanf_s、vwscanf_s
ms.date: 11/04/2016
api_name:
- vscanf_s
- vwscanf_s
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
- _vtscanf_s
- vscanf_s
- vwscanf_s
ms.assetid: 23a1c383-5b01-4887-93ce-534a1e38ed93
ms.openlocfilehash: 4d08679d08fb5b212306cbaeec200d16803a85ef
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945409"
---
# <a name="vscanf_s-vwscanf_s"></a>vscanf_s、vwscanf_s

標準入力ストリームから書式付きデータを読み取ります。 これらのバージョンの [vscanf、vwscanf](vscanf-vwscanf.md) は、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンです。

## <a name="syntax"></a>構文

```C
int vscanf_s(
   const char *format,
   va_list arglist
);
int vwscanf_s(
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>パラメーター

*format*<br/>
書式指定文字列。

*arglist*<br/>
可変個引数リスト。

## <a name="return-value"></a>戻り値

正常に変換され、代入されたフィールドの数を返します。この数には、読み取られても代入されなかったフィールドは含まれません。 戻り値が 0 の場合は、代入されたフィールドがなかったことを示します。 戻り値は、エラーの場合は**EOF** 、ファイルの終端文字または文字列の終端文字が最初に文字を読み取ろうとしたときに検出される場合はです。 *Format*が**NULL**ポインターの場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 **vscanf_s**と**vwscanf_s**は**EOF**を返し、 **errno**を**EINVAL**に設定します。

エラー コードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**Vscanf_s**関数は、標準入力ストリーム**stdin**からデータを読み取り、 *arglist*引数リストによって指定された場所にデータを書き込みます。 リストの各引数は、*形式*の型指定子に対応する型の変数へのポインターである必要があります。 重なり合う文字列間でコピーした場合の動作は未定義です。

**vwscanf_s**は、 **vscanf_s**のワイド文字バージョンです。**vwscanf_s**の*format*引数は、ワイド文字列です。 ストリームが ANSI モードで開かれている場合、 **vwscanf_s**と**vscanf_s**は同じように動作します。 **vscanf_s**は、UNICODE ストリームからの入力をサポートしていません。

**Vscanf**と**vwscanf**とは異なり、 **vscanf_s**と**vwscanf_s**では、[] で囲まれた**c**、 **c**、 **s**、 **s**、または文字列の各コントロールセットのすべての入力パラメーターに対してバッファーサイズを指定する必要があります。 バッファー サイズ (文字単位) は、バッファーまたは変数のポインターの直後に追加パラメーターとして渡されます。 **Wchar_t**文字列のバッファーサイズ (文字数) は、バイト単位のサイズと同じではありません。

バッファー サイズには、終端 null も含まれます。 幅指定フィールドを使用して、読み取られたトークンがバッファーに確実に収まるようにすることができます。 幅指定フィールドが使用されない場合で、読み取られたトークンがバッファーに収まらない場合、そのバッファーには何も書き込まれません。

> [!NOTE]
> *Size*パラメーターは、 **size_t**ではなく**unsigned**型です。

詳細については、「[scanf 関数の文字幅指定](../../c-runtime-library/scanf-width-specification.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**vtscanf_s (_m)**|**vscanf_s**|**vscanf_s**|**vwscanf_s**|

詳細については、「[Format Specification Fields: scanf and wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)」(scanf 関数と wscanf 関数の書式指定フィールド) をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**vscanf_s**|\<stdio.h>|
|**wscanf_s**|\<stdio.h> または \<wchar.h>|

コンソールは、ユニバーサル Windows プラットフォーム (UWP) アプリではサポートされていません。 コンソール、 **stdin**、 **stdout**、および**stderr**に関連付けられている標準ストリームハンドルは、C ランタイム関数が UWP アプリで使用できるようになる前にリダイレクトする必要があります。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_vscanf_s.c
// compile with: /W3
// This program uses the vscanf_s and vwscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vscanf_s(char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vscanf_s(format, arglist);
    va_end(arglist);
    return result;
}

int call_vwscanf_s(wchar_t *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vwscanf_s(format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    int   i, result;
    float fp;
    char  c, s[81];
    wchar_t wc, ws[81];
    result = call_vscanf_s("%d %f %c %C %s %S", &i, &fp, &c, 1,
                           &wc, 1, s, _countof(s), ws, _countof(ws) );
    printf( "The number of fields input is %d\n", result );
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);
    result = call_vwscanf_s(L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                            &wc, 1, s, _countof(s), ws, _countof(ws) );
    wprintf( L"The number of fields input is %d\n", result );
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);
}
```

このプログラムで、この例の入力を指定した場合、次の出力が生成されます。

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[vscanf、vwscanf](vscanf-vwscanf.md)<br/>
