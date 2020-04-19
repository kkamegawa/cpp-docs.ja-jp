---
title: _itoa, _itow 関数
ms.date: 08/19/2019
api_name:
- itoa
- _itoa
- ltoa
- _ltoa
- ultoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _itoa
- _ltoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- itoa
- ltoa
- ultoa
- i64toa
- ui64toa
- itow
- ltow
- ultow
- i64tow
- ui64tow
- itot
- _itot
- ltot
- _ltot
- ultot
- _ultot
- i64tot
- _i64tot
- ui64tot
- _ui64tot
- _MAX_ITOSTR_BASE16_COUNT
- _MAX_ITOSTR_BASE10_COUNT
- _MAX_ITOSTR_BASE8_COUNT
- _MAX_ITOSTR_BASE2_COUNT
- _MAX_LTOSTR_BASE16_COUNT
- _MAX_LTOSTR_BASE10_COUNT
- _MAX_LTOSTR_BASE8_COUNT
- _MAX_LTOSTR_BASE2_COUNT
- _MAX_ULTOSTR_BASE16_COUNT
- _MAX_ULTOSTR_BASE10_COUNT
- _MAX_ULTOSTR_BASE8_COUNT
- _MAX_ULTOSTR_BASE2_COUNT
- _MAX_I64TOSTR_BASE16_COUNT
- _MAX_I64TOSTR_BASE10_COUNT
- _MAX_I64TOSTR_BASE8_COUNT
- _MAX_I64TOSTR_BASE2_COUNT
- _MAX_U64TOSTR_BASE16_COUNT
- _MAX_U64TOSTR_BASE10_COUNT
- _MAX_U64TOSTR_BASE8_COUNT
- _MAX_U64TOSTR_BASE2_COUNT
helpviewer_keywords:
- _itot function
- ui64toa function
- _ui64toa function
- converting integers
- itot function
- _i64tow function
- _i64toa function
- _itow function
- ui64tow function
- integers, converting
- itoa function
- _ui64tow function
- i64tow function
- itow function
- i64toa function
- converting numbers, to strings
- _itoa function
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
ms.openlocfilehash: a4e429b51e4157b49086d2425bec2698a724a0e0
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898787"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa、_itoa、ltoa、_ltoa、ultoa、_ultoa、_i64toa、_ui64toa、_itow、_ltow、_ultow、_i64tow、_ui64tow

整数を文字列に変換します。 これらの関数のセキュリティを強化したバージョンを使用できます。「 [_itoa_s、_itow_s functions」を](itoa-s-itow-s.md)参照してください。

## <a name="syntax"></a>構文

```C
char * _itoa( int value, char *buffer, int radix );
char * _ltoa( long value, char *buffer, int radix );
char * _ultoa( unsigned long value, char *buffer, int radix );
char * _i64toa( long long value, char *buffer, int radix );
char * _ui64toa( unsigned long long value, char *buffer, int radix );

wchar_t * _itow( int value, wchar_t *buffer, int radix );
wchar_t * _ltow( long value, wchar_t *buffer, int radix );
wchar_t * _ultow( unsigned long value, wchar_t *buffer, int radix );
wchar_t * _i64tow( long long value, wchar_t *buffer, int radix );
wchar_t * _ui64tow( unsigned long long value, wchar_t *buffer, int radix );

// These POSIX versions of the functions have deprecated names:
char * itoa( int value, char *buffer, int radix );
char * ltoa( long value, char *buffer, int radix );
char * ultoa( unsigned long value, char *buffer, int radix );

// The following template functions are C++ only:
template <size_t size>
char *_itoa( int value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( long value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
char *_i64toa( long long value, char (&buffer)[size], int radix );

template <size_t size>
char * _ui64toa( unsigned long long value, char (&buffer)[size], int radix );

template <size_t size>
wchar_t * _itow( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ltow( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ultow( unsigned long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _i64tow( long long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ui64tow( unsigned long long value, wchar_t (&buffer)[size],
   int radix );
```

### <a name="parameters"></a>パラメーター

*value*<br/>
変換される数値。

*バッファー*<br/>
変換の結果を保持するバッファー。

*radix*<br/>
*値*の変換に使用するベース。2-36 の範囲内である必要があります。

*size*<br/>
文字型の単位でのバッファーの長さ。 このパラメーターは、のC++ *buffer*引数から推論されます。

## <a name="return-value"></a>戻り値

これらの各関数は、*バッファー*へのポインターを返します。 エラーの戻り値はありません。

## <a name="remarks"></a>Remarks

**_Itoa**、 **_ltoa**、 **_ultoa**、 **_i64toa**、および **_ui64toa**の各関数は、指定され*た値*引数の数字を null で終わる文字列に変換し、結果を格納*します (* **_itoa**、 **_ltoa**、**および _ultoa**の場合は最大33文字、_i64toa の場合は65、 **_ui64toa の場合**は **)。** 場合*基数*が10、*値*が負の場合、格納されている文字列の最初の文字は負符号 ( **-** ) です。 **_Itow**、 **_ltow**、 **_ultow**、 **_i64tow**、および **_ui64tow**の各関数は、それぞれ **_itoa**、 **_ltoa**、 **_ultoa**、 **_i64toa**、 **_ui64toa**のワイド文字バージョンです。

> [!IMPORTANT]
> これらの関数は、小さすぎるバッファーの末尾を越えて書き込むことができます。 バッファーオーバーランを防ぐには、*バッファー*が、変換された数字と末尾の null 文字および符号文字を保持するのに十分な大きさであることを確認します。 これらの関数を誤用すると、コードに重大なセキュリティ上の問題が発生する可能性があります。

セキュリティ上の問題が発生する可能性があるため、既定では、これらの関数は非推奨の警告[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)を引き起こします。**この関数または変数は安全でない可能性があります。代わりに safe_function の使用を検討**してください **。廃止を無効にするには、_CRT_SECURE_NO_WARNINGS を使用します。** 警告メッセージによって提案された*safe_function*を使用するようにソースコードを変更することをお勧めします。 より安全な関数では、指定されたバッファーサイズよりも多くの文字を書き込むことはできません。 詳細については、「 [_itoa_s」、「_itow_s functions](itoa-s-itow-s.md)」を参照してください。

これらの関数を非推奨の警告なしで使用するには、CRT ヘッダーを含める前に **_CRT_SECURE_NO_WARNINGS**プリプロセッサマクロを定義します。 この操作は、開発者コマンドプロンプトで **/D_CRT_SECURE_NO_WARNINGS**コンパイラオプションを**cl**コマンドに追加することによって、コマンドラインで行うことができます。 それ以外の場合は、ソースファイルでマクロを定義します。 プリコンパイル済みヘッダーを使用する場合は、プリコンパイル済みヘッダーインクルードファイル (Visual Studio 2017 以前の場合は*stdafx.h* ) の先頭にマクロを定義*します。* ソースコードでマクロを定義するには、次の例のように、CRT ヘッダーを含める前に **#define**ディレクティブを使用します。

```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

でC++は、これらの関数には、より安全な対応するテンプレートオーバーロードがあります。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

POSIX 名**itoa**、 **ltoa**、および**ultoa**は、 **_itoa**、 **_ltoa**、および **_ultoa**関数のエイリアスとして存在します。 POSIX 名は、ISO C の実装固有のグローバル関数名規則に従っていないため、非推奨とされます。既定では、これらの関数は非推奨の警告[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)を引き起こします。**この項目の POSIX 名は非推奨とされます。代わりに、ISO C とC++準拠する名前:** *new_name*を使用します。 これらの関数、 **_itoa_s**、 **_ltoa_s**、または **_ultoa_s**のより安全なバージョンを使用するようにソースコードを変更することをお勧めします。 詳細については、「 [_itoa_s」、「_itow_s functions](itoa-s-itow-s.md)」を参照してください。

ソースコードの移植性を確保するために、コードで POSIX 名を保持することをお勧めします。 これらの関数を非推奨の警告なしで使用するには、CRT ヘッダーを含める前に、 **_CRT_NONSTDC_NO_WARNINGS**と **_CRT_SECURE_NO_WARNINGS**のプリプロセッサマクロの両方を定義します。 この操作は、コマンドラインで **/D_CRT_SECURE_NO_WARNINGS**および **/D_CRT_NONSTDC_NO_WARNINGS**コンパイラオプションを**cl**コマンドに追加することで、コマンドラインで実行できます。 それ以外の場合は、ソースファイルでマクロを定義します。 プリコンパイル済みヘッダーを使用する場合は、プリコンパイル済みヘッダーインクルードファイルの先頭にマクロを定義します。 ソースコードでマクロを定義するには、次の例のように、CRT ヘッダーを含める前に **#define**ディレクティブを使用します。

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>最大変換数マクロ

変換用のセキュリティで保護されたバッファーを作成できるように、CRT には便利なマクロがいくつか含まれています。 これらは、複数の一般的な基本クラスについて、各整数型の最大有効値 (null 終端文字と符号文字を含む) を変換するために必要なバッファーのサイズを定義します。 *基数*によって指定されたベースの変換を受け取るのに十分なサイズの変換バッファーがあることを確認するには、バッファーを割り当てるときに、これらの定義済みマクロのいずれかを使用します。 これにより、整数型を文字列に変換するときに、バッファーオーバーランエラーを防ぐことができます。 これらのマクロは、ソースに stdlib.h> または wchar を含めるときに定義されます。

文字列変換関数でこれらのマクロのいずれかを使用するには、適切な文字型の変換バッファーを宣言し、整数型にはマクロ値を、ベースにはバッファーディメンションとしてを使用します。 次の表に、表示されるベースの各関数に適したマクロを示します。

||||
|-|-|-|
|関数|radix|[マクロ]|
|**_itoa**、 **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**、 **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**、 **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**、 **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**、 **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

この例では、変換数マクロを使用して、基数が2である**unsigned long long**を格納するのに十分な大きさのバッファーを定義します。

```cpp
#include <wchar.h>
#include <iostream>
int main()
{
    wchar_t buffer[_MAX_U64TOSTR_BASE2_COUNT];
    std:wcout << _ui64tow(0xFFFFFFFFFFFFFFFFull, buffer, 2) << std::endl;
}
```

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot**|**_itoa**|**_itoa**|**_itow**|
|**_ltot**|**_ltoa**|**_ltoa**|**_ltow**|
|**_ultot**|**_ultoa**|**_ultoa**|**_ultow**|
|**_i64tot**|**_i64toa**|**_i64toa**|**_i64tow**|
|**_ui64tot**|**_ui64toa**|**_ui64toa**|**_ui64tow**|

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**itoa**、 **ltoa**、 **ultoa**|\<stdlib.h>|
|**_itoa**、 **_ltoa**、 **_ultoa**、 **_i64toa**、 **_ui64toa**|\<stdlib.h>|
|**_itow**、 **_ltow**、 **_ultow**、 **_i64tow**、 **_ui64tow**|\<stdlib.h> または \<wchar.h>|

これらの関数とマクロは、Microsoft 固有のものです。 互換性について詳しくは、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>使用例

このサンプルでは、いくつかの整数変換関数の使用方法を示します。 **_CRT_SECURE_NO_WARNINGS**マクロを使用して、警告 C4996 をサイレント状態にすることに注意してください。

```C
// crt_itoa.c
// Compile by using: cl /W4 crt_itoa.c
// This program makes use of the _itoa functions
// in various examples.

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen
#include <stdlib.h>     // for _countof, _itoa fns, _MAX_COUNT macros

int main(void)
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;

    for (r = 10; r >= 2; --r)
    {
        _itoa(-1, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _i64toa(-1LL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _ui64toa(0xffffffffffffffffULL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
}
```

```Output
base 10: -1 (2 chars)
base 9: 12068657453 (11 chars)
base 8: 37777777777 (11 chars)
base 7: 211301422353 (12 chars)
base 6: 1550104015503 (13 chars)
base 5: 32244002423140 (14 chars)
base 4: 3333333333333333 (16 chars)
base 3: 102002022201221111210 (21 chars)
base 2: 11111111111111111111111111111111 (32 chars)

base 10: -1 (2 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)

base 10: 18446744073709551615 (20 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)
```

## <a name="see-also"></a>参照

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[_itoa_s, _itow_s 関数](itoa-s-itow-s.md)<br/>
