---
title: mbrtowc
ms.date: 11/04/2016
api_name:
- mbrtowc
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
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: b4c68ae8df9821d862b9f742d8a8ef7ace19c981
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952443"
---
# <a name="mbrtowc"></a>mbrtowc

現在のロケールのマルチバイト文字を、それに対応するワイド文字に変換します。マルチバイト文字の途中から再開することが可能です。

## <a name="syntax"></a>構文

```C
size_t mbrtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   mbstate_t *mbstate
);
```

### <a name="parameters"></a>パラメーター

*wchar*<br/>
変換されたワイド文字の文字列を受け取るワイド文字のアドレス ( **wchar_t**型)。 ワイド文字を返す必要がない場合、この値は null ポインターを指定できます。

*mbchar*<br/>
バイト シーケンスのアドレス (マルチバイト文字)。

*count*<br/>
チェックするバイト数。

*mbstate*<br/>
変換状態のオブジェクトへのポインター。 この値が null ポインターの場合、関数は静的な内部変換状態オブジェクトを使用します。 内部**mbstate_t**オブジェクトはスレッドセーフではないため、常に独自の*mbstate*引数を渡すことをお勧めします。

## <a name="return-value"></a>戻り値

次のいずれかの値です。

0次の*数*以下では、 *wchar*が null ポインターではない場合、 *wchar*に格納されている null ワイド文字を表すマルチバイト文字が完成します。

1が*カウント*されます。次の*カウント*を含むか、有効なマルチバイト文字を入力します。 返される値は、マルチバイト文字を完成するのに必要なバイト数です。 *Wchar*が null ポインターでない場合、それに相当するワイド文字は*wchar*に格納されます。

(size_t)(-1)エンコードエラーが発生しました。 次の*数*以下のバイトは、完全かつ有効なマルチバイト文字に寄与しません。 この場合、 **errno**は EILSEQ に設定され、 *mbstate*の変換のシフト状態は指定されていません。

(size_t)(-2)次の*カウント*バイトは不完全である可能性があるマルチバイト文字に寄与し、すべての*カウント*バイトが処理されています。 *Wchar*に値は格納されませんが、 *mbstate*が更新されて関数が再起動されます。

## <a name="remarks"></a>Remarks

*Mbchar*が null ポインターの場合、関数は呼び出しに相当します。

`mbrtowc(NULL, "", 1, &mbstate)`

この場合、引数*wchar*および*count*の値は無視されます。

*Mbchar*が null ポインターでない場合、関数は、 *mbchar*から*count*バイトを調べて、次のマルチバイト文字を完成させるために必要なバイト数を調べます。 次の文字が有効な場合は、対応するマルチバイト文字が*wchar*に格納されます (null ポインターではない場合)。 文字が対応するワイド null 文字の場合、結果の*mbstate*の状態は初期の変換状態になります。

**Mbrtowc**関数は、 [mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)の再起動によって異なります。 変換状態は、同じまたはその他の再開可能な関数への後続の呼び出しのために*mbstate*に格納されます。 再開可能な関数と再開不可能な関数を混用した場合、結果は未定義です。  たとえば、 **wcstombs**ではなく**wcsrtombs**の後続の呼び出しが使用される場合、アプリケーションでは**wcslen**ではなく**wcsrlen**を使用する必要があります。

## <a name="example"></a>例

マルチバイト文字を対応するワイド文字に変換します。

```cpp
// crt_mbrtowc.cpp

#include <stdio.h>
#include <mbctype.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

#define BUF_SIZE 100

int Sample(char* szIn, wchar_t* wcOut, int nMax)
{
    mbstate_t   state = {0}; // Initial state
    size_t      nConvResult,
                nmbLen = 0,
                nwcLen = 0;
    wchar_t*    wcCur = wcOut;
    wchar_t*    wcEnd = wcCur + nMax;
    const char* mbCur = szIn;
    const char* mbEnd = mbCur + strlen(mbCur) + 1;
    char*       szLocal;

    // Sets all locale to French_Canada.1252
    szLocal = setlocale(LC_ALL, "French_Canada.1252");
    if (!szLocal)
    {
        printf("The fuction setlocale(LC_ALL, \"French_Canada.1252\") failed!\n");
        return 1;
    }

    printf("Locale set to: \"%s\"\n", szLocal);

    // Sets the code page associated current locale's code page
    // from a previous call to setlocale.
    if (_setmbcp(_MB_CP_SBCS) == -1)
    {
        printf("The fuction _setmbcp(_MB_CP_SBCS) failed!");
        return 1;
    }

    while ((mbCur < mbEnd) && (wcCur < wcEnd))
    {
        //
        nConvResult = mbrtowc(wcCur, mbCur, 1, &state);
        switch (nConvResult)
        {
            case 0:
            {  // done
                printf("Conversion succeeded!\nMultibyte String: ");
                printf(szIn);
                printf("\nWC String: ");
                wprintf(wcOut);
                printf("\n");
                mbCur = mbEnd;
                break;
            }

            case -1:
            {  // encoding error
                printf("The call to mbrtowc has detected an encoding error.\n");
                mbCur = mbEnd;
                break;
            }

            case -2:
            {  // incomplete character
                if   (!mbsinit(&state))
                {
                    printf("Currently in middle of mb conversion, state = %x\n", state);
                    // state will contain data regarding lead byte of mb character
                }

                ++nmbLen;
                ++mbCur;
                break;
            }

            default:
            {
                if   (nConvResult > 2) // The multibyte should never be larger than 2
                {
                    printf("Error: The size of the converted multibyte is %d.\n", nConvResult);
                }

                ++nmbLen;
                ++nwcLen;
                ++wcCur;
                ++mbCur;
            break;
            }
        }
    }

   return 0;
}

int main(int argc, char* argv[])
{
    char    mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";
    wchar_t wcBuf[BUF_SIZE] = {L''};

    return Sample(mbBuf, wcBuf, BUF_SIZE);
}
```

### <a name="sample-output"></a>出力例

```Output
Locale set to: "French_Canada.1252"
Conversion succeeded!
Multibyte String: AaBbCcÜïα∩≡xXyYzZ
WC String: AaBbCcÜïα∩≡xXyYzZ
```

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**mbrtowc**|\<wchar.h>|

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
