---
title: vsscanf_s、vswscanf_s
ms.date: 11/04/2016
api_name:
- vswscanf_s
- vsscanf_s
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
- vsscanf_s
- vswscanf_s
- _vstscanf_s
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
ms.openlocfilehash: bacda4288a6745ea57c31e68e515ae7b37418096
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946013"
---
# <a name="vsscanf_s-vswscanf_s"></a>vsscanf_s、vswscanf_s

文字列から書式付きデータを読み込みます。 これらのバージョンの [vsscanf、vswscanf](vsscanf-vswscanf.md) は、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンです。

## <a name="syntax"></a>構文

```C
int vsscanf_s(
   const char *buffer,
   const char *format,
   va_list argptr
);
int vswscanf_s(
   const wchar_t *buffer,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
格納されるデータ。

*format*<br/>
書式指定文字列。 詳細については、「[Format Specification Fields: scanf and wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)」(scanf 関数と wscanf 関数の書式指定フィールド) をご覧ください。

*arglist*<br/>
可変個引数リスト。

## <a name="return-value"></a>戻り値

これらの関数は、正常に変換および代入されたフィールドの数を返します。読み込まれただけで代入されなかったフィールドは戻り値には含まれません。 戻り値が 0 の場合は、代入されたフィールドがなかったことを示します。 エラーの場合、または最初の変換の前に文字列の末尾に到達した場合、戻り値は**EOF**になります。

*Buffer*または*format*が**NULL**ポインターの場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**を**EINVAL**に設定します。

エラー コードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**Vsscanf_s**関数は、 *arglist*引数リストの各引数によって指定された場所に*バッファー*からデータを読み取ります。 引数リストの引数は、*形式*の型指定子に対応する型を持つ変数へのポインターを指定します。 セキュリティレベルの低いバージョン**vsscanf**とは異なり、 **[]** で囲まれている型フィールド文字**c**、 **c**、 **s**、 **s**、または文字列コントロールセットを使用する場合は、バッファーサイズのパラメーターが必要です。 バッファー サイズ (文字単位) は、バッファー サイズが必要な各バッファーの後に追加パラメーターとして指定する必要があります。

バッファー サイズには、終端 null も含まれます。 読み取られたトークンがバッファーに確実に収まるように、幅指定フィールドが使用される場合もあります。 幅指定フィールドが使用されない場合で、読み取られたトークンがバッファーに収まらない場合、そのバッファーには何も書き込まれません。

詳細については、「[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)」と「[scanf 関数の型フィールド文字](../../c-runtime-library/scanf-type-field-characters.md)」を参照してください。

> [!NOTE]
> Size パラメーターは、 **size_t**ではなく**unsigned**型です。

*Format*引数は、入力フィールドの解釈を制御し、 **scanf_s**関数の*format*引数と同じ形式と機能を持ちます。 重なり合う文字列間でコピーした場合の動作は未定義です。

**vswscanf_s**は、 **vsscanf_s**のワイド文字バージョンです。**vswscanf_s**の引数はワイド文字列です。 **vsscanf_s**では、マルチバイトの16進文字は処理されません。 **vswscanf_s**では、Unicode の全角16進数または "互換ゾーン" の文字は処理されません。 それ以外の場合、 **vswscanf_s**と**vsscanf_s**は同じように動作します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**vstscanf_s (_d)**|**vsscanf_s**|**vsscanf_s**|**vswscanf_s**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**vsscanf_s**|\<stdio.h>|
|**vswscanf_s**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_vsscanf_s.c
// compile with: /W3
// This program uses vsscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vsscanf_s(char *tokenstring, char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vsscanf_s(tokenstring, format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    char  tokenstring[] = "15 12 14...";
    char  s[81];
    char  c;
    int   i;
    float fp;

    // Input various data from tokenstring:
    // max 80 character string:
    call_vsscanf_s(tokenstring, "%80s", s, _countof(s));
    call_vsscanf_s(tokenstring, "%c", &c, sizeof(char));
    call_vsscanf_s(tokenstring, "%d", &i);
    call_vsscanf_s(tokenstring, "%f", &fp);

    // Output the data read
    printf("String    = %s\n", s);
    printf("Character = %c\n", c);
    printf("Integer:  = %d\n", i);
    printf("Real:     = %f\n", fp);
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
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf、vswscanf](vsscanf-vswscanf.md)<br/>
