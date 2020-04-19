---
title: wcrtomb
ms.date: 11/04/2016
api_name:
- wcrtomb
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
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: 8d2108b90f6884113f0bd974bf7aa634544adf5f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945218"
---
# <a name="wcrtomb"></a>wcrtomb

ワイド文字をマルチバイト文字の表現に変換します。 この関数のセキュリティが強化されたバージョンについては、「[wcrtomb_s](wcrtomb-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>パラメーター

*mbchar*<br/>
結果として得られるマルチバイトに変換された文字。

*wchar*<br/>
変換するワイド文字。

*mbstate*<br/>
**Mbstate_t**オブジェクトへのポインター。

## <a name="return-value"></a>戻り値

変換されたマルチバイト文字を表すのに必要なバイト数を返します。エラーが発生した場合は -1 を返します。

## <a name="remarks"></a>Remarks

**Wcrtomb**関数は、 *mbstate*に含まれる指定された変換状態から始まるワイド文字を、 *wchar*に含まれる値から*mbchar*で表されるアドレスに変換します。 戻り値は、対応するマルチバイト文字を表すために必要なバイト数ですが、 **MB_CUR_MAX**バイトを超えることはありません。

*Mbstate*が null の場合、 *mbchar*の変換状態を含む内部**mbstate_t**オブジェクトが使用されます。 文字シーケンス*wchar*に対応するマルチバイト文字表現がない場合は、-1 が返され、 **errno**は**EILSEQ**に設定されます。

**Wcrtomb**関数は、 [wctomb、_wctomb_l](wctomb-wctomb-l.md)の再起動によって異なります。 変換状態は、同じまたはその他の再開可能な関数への後続の呼び出しのために*mbstate*に格納されます。 再開可能な関数と再開不可能な関数を混用した場合、結果は未定義です。 たとえば、 **wcstombs**の代わりに**wcsrtombs**の後続の呼び出しが使用された場合、アプリケーションは**wcsrlen**ではなく**wcsrlen**を使用します。

C++ では、この関数にテンプレートのオーバーロードがあります。このオーバーロードは、この関数に対応するセキュリティで保護された新しい関数を呼び出します。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

## <a name="exceptions"></a>例外

**Wcrtomb**関数は、この関数の実行中に現在のスレッドの関数が**setlocale**を呼び出し、 *mbstate*が null の場合は、マルチスレッドセーフです。

## <a name="example"></a>例

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
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
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**wcrtomb**|\<wchar.h>|

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
