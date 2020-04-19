---
title: wcrtomb_s
ms.date: 11/04/2016
api_name:
- wcrtomb_s
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
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: c1612e7fc4e40e05c46f06d8a29b69534c359421
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945845"
---
# <a name="wcrtomb_s"></a>wcrtomb_s

ワイド文字をマルチバイト文字の表現に変換します。 「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [wcrtomb](wcrtomb.md) です。

## <a name="syntax"></a>構文

```C
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char *mbchar,
   size_t sizeOfmbchar,
   wchar_t *wchar,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char (&mbchar)[size],
   wchar_t *wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>パラメーター

*pReturnValue*<br/>
書き込まれたバイト数を返します。エラーが発生した場合は -1 を返します。

*mbchar*<br/>
結果として得られるマルチバイトに変換された文字。

*sizeOfmbchar*<br/>
*Mbchar*変数のサイズ (バイト単位)。

*wchar*<br/>
変換するワイド文字。

*mbstate*<br/>
**Mbstate_t**オブジェクトへのポインター。

## <a name="return-value"></a>戻り値

エラーが発生した場合は、0または**errno**値を返します。

## <a name="remarks"></a>Remarks

**Wcrtomb_s**関数は、 *mbstate*に含まれる指定された変換状態から始まるワイド文字を、 *wchar*に含まれる値から*mbchar*で表されるアドレスに変換します。 *Preturnvalue*値は、変換されたバイト数になりますが、 **MB_CUR_MAX**バイト以下で、エラーが発生した場合は-1 になります。

*Mbstate*が null の場合、内部**mbstate_t**の変換状態が使用されます。 *Wchar*に含まれる文字に対応するマルチバイト文字がない場合、 *preturnvalue*値は-1 になり、関数は**EILSEQ**の**errno**値を返します。

**Wcrtomb_s**関数は、 [wctomb_s、_wctomb_s_l](wctomb-s-wctomb-s-l.md)の再起動によって異なります。 変換状態は、同じまたはその他の再開可能な関数への後続の呼び出しのために*mbstate*に格納されます。 再開可能な関数と再開不可能な関数を混用した場合、結果は未定義です。 たとえば、 **wcstombs_s**ではなく**wcsrtombs_s**の後続の呼び出しが使用された場合、アプリケーションは**wcslen**ではなく**wcsrlen**を使用します。

C++ では、この関数の使用はテンプレートのオーバーロードによって簡素化されます。オーバーロードでは、バッファー長を自動的に推論できる (サイズの引数を指定する必要がなくなる) だけでなく、古くてセキュリティが万全ではない関数を新しく安全な関数に自動的に置き換えることができます。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

## <a name="exceptions"></a>例外

**Wcrtomb_s**関数は、この関数の実行中に現在のスレッドの関数が**setlocale**を呼び出し、 *mbstate*が null の場合は、マルチスレッドセーフです。

## <a name="example"></a>例

```C
// crt_wcrtomb_s.c
// This program converts a wide character
// to its corresponding multibyte character.
//

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    errno_t     returnValue;
    size_t      pReturnValue;
    mbstate_t   mbstate;
    size_t      sizeOfmbStr = 1;
    char        mbchar = 0;
    wchar_t*    wchar = L"Q\0";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),
                            *wchar, &mbstate);
    if (returnValue == 0) {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wchar);
        printf(" was converted to a the \"%c\" ", mbchar);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to a the "Q" multibyte character.
```

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
