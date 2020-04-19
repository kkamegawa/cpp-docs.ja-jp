---
title: wcsrtombs
ms.date: 11/04/2016
api_name:
- wcsrtombs
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
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: e6640a027b03b7aa0dceaf8e61af6cb43a44d6e0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945047"
---
# <a name="wcsrtombs"></a>wcsrtombs

ワイド文字の文字列をマルチバイト文字の文字列形式に変換します。 この関数のセキュリティが強化されたバージョンについては、「[wcsrtombs_s](wcsrtombs-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>パラメーター

*mbstr*<br/>
結果として変換されたマルチバイト文字のアドレスの場所。

*wcstr*<br/>
変換されるワイド文字の文字列の場所を間接的に指します。

*count*<br/>
変換される文字数。

*mbstate*<br/>
**Mbstate_t**の変換状態オブジェクトへのポインター。

## <a name="return-value"></a>戻り値

正常に変換されたバイト数を返します (null で終了する null バイトがあっても含まれません)。それ以外の場合は、エラーが発生した場合に -1 を返します。

## <a name="remarks"></a>Remarks

**Wcsrtombs**関数は、 *mbstate*に含まれる指定された変換の状態で始まるワイド文字の文字列を、 *wcstr*の間接的な値から*mbstr*のアドレスに変換します。 変換は、null 終端ワイド文字が検出された後、対応していない文字が検出されたとき、または次の文字が*カウント*に含まれる制限を超えたときまで、各文字に対して続行されます。 **Wcsrtombs**が、 *count*の前または後に、ワイド文字の null 文字 (L ' \ 0 ') を検出すると、それを8ビットの0に変換して停止します。

このため、 *mbstr*のマルチバイト文字列は、 **wcsrtombs**が変換中にワイド文字の null 文字を検出した場合にのみ、null で終了します。 *Wcstr*と*mbstr*が指すシーケンスが重なり合う場合、 **wcsrtombs**の動作は未定義になります。 **wcsrtombs**は、現在のロケールの LC_TYPE カテゴリの影響を受けます。

**Wcsrtombs**関数は、 [wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)の再起動によって異なります。 変換状態は、同じまたはその他の再開可能な関数への後続の呼び出しのために*mbstate*に格納されます。 再開可能な関数と再開不可能な関数を混用した場合、結果は未定義です。  たとえば、 **wcstombs**の代わりに**wcsrtombs**の後続の呼び出しが使用された場合、アプリケーションは**wcsrlen**ではなく**wcsrlen**を使用します。

*Mbstr*引数が**NULL**の場合、 **wcsrtombs**は、コピー先の文字列の必要なサイズをバイト単位で返します。 *Mbstate*が null の場合、内部**mbstate_t**の変換状態が使用されます。 文字シーケンス*wchar*に対応するマルチバイト文字表現がない場合は、-1 が返され、 **errno**は**EILSEQ**に設定されます。

C++ では、この関数にテンプレートのオーバーロードがあります。このオーバーロードは、この関数に対応するセキュリティで保護された新しい関数を呼び出します。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

## <a name="exceptions"></a>例外

**Wcsrtombs**関数は、この関数の実行中に現在のスレッドの関数が**setlocale**を呼び出しておらず、 *mbstate*が null でない限り、マルチスレッドセーフです。

## <a name="example"></a>例

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
