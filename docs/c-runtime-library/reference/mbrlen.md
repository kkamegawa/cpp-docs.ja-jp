---
title: mbrlen
ms.date: 11/04/2016
api_name:
- mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: c9559731f39db35e03f640bb30b9af3fff00cf66
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952504"
---
# <a name="mbrlen"></a>mbrlen

現在のロケールのマルチバイト文字を完成させるのに必要なバイト数を決定します。マルチバイト文字の途中から再開することが可能です。

## <a name="syntax"></a>構文

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
マルチバイト文字列内の検査対象となる次のバイトへのポインター。

*count*<br/>
検査対象の最大バイト数。

*mbstate*<br/>
*Str*の初期バイトの現在のシフト状態へのポインター。

## <a name="return-value"></a>戻り値

次のいずれかの値です。

|||
|-|-|
0|次の*数*以下のバイトでは、ワイド null 文字を表すマルチバイト文字が完成します。
*カウント*(含む)|次の*数*以下のバイトでは、有効なマルチバイト文字が完成します。 返される値は、マルチバイト文字を完成するのに必要なバイト数です。
(size_t)(-2)|次の*カウント*バイトは不完全である可能性があるマルチバイト文字に寄与し、すべての*カウント*バイトが処理されています。
(size_t)(-1)|エンコーディング エラーが発生しました。 次の*数*以下のバイトは、完全かつ有効なマルチバイト文字に寄与しません。 この場合、 **errno**は EILSEQ に設定され、 *mbstate*の変換状態は指定されていません。

## <a name="remarks"></a>Remarks

**Mbrlen**関数は、 *str*が指すバイトで*始まる最大バイト数を*検査して、シフトシーケンスを含め、次のマルチバイト文字を完了するために必要なバイト数を決定します。 これは、 *mbstate*がユーザー `mbrtowc(NULL, str, count, &mbstate)`指定の**mbstate_t**オブジェクト、またはライブラリによって提供される静的な内部オブジェクトのいずれかである呼び出しに相当します。

**Mbrlen**関数は、不完全なマルチバイト文字のシフト状態を*mbstate*パラメーターに保存して使用します。 これにより、必要に応じてマルチバイト文字の途中で再起動する機能が**mbrlen**され、最大バイト*数*を調べることができます。 *Mbstate*が null ポインターの場合、 **mbrlen**は、内部の静的**mbstate_t**オブジェクトを使用して、シフト状態を格納します。 内部**mbstate_t**オブジェクトはスレッドセーフではないため、常に独自の*mbstate*パラメーターを割り当てて渡すことをお勧めします。

**Mbrlen**関数は、 [_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)の再起動によって異なります。 シフト状態は、同じまたはその他の再開可能な関数への後続の呼び出しのために*mbstate*に格納されます。 再開可能な関数と再開不可能な関数を混用した場合、結果は未定義です。  たとえば、 **wcstombs**ではなく**wcsrtombs**の後続の呼び出しが使用される場合、アプリケーションでは**wcslen**ではなく**wcsrlen**を使用する必要があります。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|該当なし|該当なし|**mbrlen**|該当なし|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

この例は、マルチバイト文字の解釈が現在のコードページにどのように依存しているかを示し、 **mbrlen**の再開機能を示しています。

```C
// crt_mbrlen.c
// Compile by using: cl crt_mbrlen.c
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

size_t Example(const char * pStr)
{
    size_t      charLen = 0;
    size_t      charCount = 0;
    mbstate_t   mbState = {0};

    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&
            charLen != (size_t)-1)
    {
        if (charLen != (size_t)-2) // if complete mbcs char,
        {
            charCount++;
        }
    }
    return (charCount);
}

int main( void )
{
    int         cp;
    size_t      charCount = 0;
    const char  *pSample =
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";

    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);

    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale
    _setmbcp(932); // and Japanese multibyte code page
    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);
}
```

```Output

Code page: 0
é╨éτé¬é╚: Shift-jis hiragana.
Character count: 29

Code page: 932
????: Shift-jis hiragana.
Character count: 25
```

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
