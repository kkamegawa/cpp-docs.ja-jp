---
title: wcstombs_s、_wcstombs_s_l
ms.date: 11/04/2016
api_name:
- _wcstombs_s_l
- wcstombs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcstombs_s
- _wcstombs_s_l
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
ms.openlocfilehash: 135bcb90e6a82591bf05e56b60575719f4c7d45c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945023"
---
# <a name="wcstombs_s-_wcstombs_s_l"></a>wcstombs_s、_wcstombs_s_l

ワイド文字のシーケンスを、対応するマルチバイト文字のシーケンスに変換します。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおりセキュリティが強化されたバージョンの [wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md) です。

## <a name="syntax"></a>構文

```C
errno_t wcstombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count
);

errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);

template <size_t size>
errno_t wcstombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only

template <size_t size>
errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>パラメーター

*pReturnValue*<br/>
Null 終端文字を含む、変換された文字列のサイズ (バイト単位)。

*mbstr*<br/>
結果として変換されたマルチバイト文字の文字列のバッファーのアドレス。

*sizeInBytes*<br/>
*Mbstr*バッファーのサイズ (バイト単位)。

*wcstr*<br/>
変換するワイド文字の文字列を指します。

*count*<br/>
*Mbstr*バッファーに格納する最大バイト数。終端の null 文字または[TRUNCATE](../../c-runtime-library/truncate.md)は含まれません。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。

|エラー状況|戻り値と**errno**|
|---------------------|------------------------------|
|*mbstr*が**NULL**で、 *sizeinbytes* > 0|**EINVAL**|
|*wcstr*が**NULL**です|**EINVAL**|
|コピー先のバッファーが小さすぎて、変換された文字列を含めることができません ( *count*が**TRUNCATE**の場合を除きます。次の「解説」を参照してください)。|**ERANGE**|

これらのいずれかの条件が発生すると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーター例外が呼び出されます。 実行の継続が許可された場合、関数はエラーコードを返し、表に示されているように**errno**を設定します。

## <a name="remarks"></a>Remarks

**Wcstombs_s**関数は、 *wcstr*が指すワイド文字の文字列を、 *mbstr*が指すバッファーに格納されているマルチバイト文字に変換します。 これらの条件のいずれかが満たされるまで、各文字に対して変換が続きます。

- ワイド文字の null が検出されました。

- 変換できないワイド文字が検出されました。

- *Mbstr* buffer に格納されているバイト数は*count*と等しくなります。

変換後の文字列は、常に null で終わります (エラーの場合も同様)。

*Count*が特別な値の[切り捨て](../../c-runtime-library/truncate.md)である場合、 **wcstombs_s**は、null 終端文字用の空きを残したまま、コピー先のバッファーに収まる限りの文字列を変換します。 文字列が切り捨てられた場合、戻り値は**Strate**になり、変換は成功したと見なされます。

**Wcstombs_s**がソース文字列を正常に変換した場合は、null 終端文字を含む、変換された文字列のサイズが (指定した*preturnvalue* **値が null**ではない)  *&#42;preturnvalue*に配置されます。 これは、 *mbstr*引数が**NULL**の場合にも発生し、必要なバッファーサイズを決定する手段を提供します。 *Mbstr*が**NULL**の場合、 *count*は無視されることに注意してください。

**Wcstombs_s**がマルチバイト文字に変換できないワイド文字を検出した場合は、  *&#42;preturnvalue*値に0を格納し、コピー先のバッファーを空の文字列に設定して、 **errno**を**EILSEQ**に設定し、 **EILSEQ**を返します。

*Wcstr*と*mbstr*が指すシーケンスが重なり合う場合、 **wcstombs_s**の動作は未定義になります。

> [!IMPORTANT]
> *Wcstr*と*mbstr*が重複しないようにし、その*カウント*に変換するワイド文字の数が正しく反映されていることを確認します。

**wcstombs_s**は、ロケールに依存する動作に現在のロケールを使用します。 **_wcstombs_s_l**は、渡されたロケールを代わりに使用する点を除いて、 **wcstombs**と同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

C++ では、これらの関数の使用はテンプレートのオーバーロードによって簡素化されます。オーバーロードでは、バッファー長を自動的に推論できる (サイズの引数を指定する必要がなくなる) だけでなく、古くてセキュリティが万全ではない関数を新しく安全な関数に自動的に置き換えることができます。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

このプログラムは、 **wcstombs_s**関数の動作を示しています。

```C
// crt_wcstombs_s.c
// This example converts a wide character
// string to a multibyte character string.
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t   i;
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t*pWCBuffer = L"Hello, world.";

    printf( "Convert wide-character string:\n" );

    // Conversion
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,
               pWCBuffer, (size_t)BUFFER_SIZE );

    // Output
    printf("   Characters converted: %u\n", i);
    printf("    Multibyte character: %s\n\n",
     pMBBuffer );

    // Free multibyte character buffer
    if (pMBBuffer)
    {
    free(pMBBuffer);
    }
}
```

```Output
Convert wide-character string:
   Characters converted: 14
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s、_wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
