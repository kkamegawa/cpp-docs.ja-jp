---
title: vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l
ms.date: 11/04/2016
api_name:
- _vsnprintf
- _vsnprintf_l
- _vsnwprintf
- _vsnwprintf_l
- _vsnprintf
- _vsnprintf;
- vsnprintf; _vsnprintf
- _vsnwprintf;
- _vsnprintf_l;
- _vsnwprintf_l;
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
- ntoskrnl.exe
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vsnprintf
- _vsnwprintf
- _vsntprintf
- vsnprintf
- stdio/vsnprintf
- stdio/_vsnprintf
- stdio/_vsnprintf_l
- stdio/_vsnwprintf
- stdio/_vsnwprintf_l
- _vsnprintf_l
- _vsnwprintf_l
helpviewer_keywords:
- vsntprintf function
- _vsnwprintf_l function
- vsnwprintf_l function
- vsntprintf_l function
- _vsntprintf function
- _vsnprintf_l function
- vsnprintf function
- _vsntprintf_l function
- vsnprintf_l function
- _vsnwprintf function
- _vsnprintf function
- formatted text [C++]
- vsnwprintf function
ms.assetid: a97f92df-c2f8-4ea0-9269-76920d2d566a
ms.openlocfilehash: abe34dc0f3baf9bdc63e0314ac70af3783d2bd9a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857711"
---
# <a name="vsnprintf-_vsnprintf-_vsnprintf_l-_vsnwprintf-_vsnwprintf_l"></a>vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l

引数リストへのポインターを使用して、書式付き出力を書き込みます。 これらの関数のセキュリティを強化したバージョンを使用できます。「 [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)」をご覧ください。

## <a name="syntax"></a>構文

```C
int vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_l(
   char *buffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf_l(
   char (&buffer)[size],
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_l(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
出力の格納位置。

*count*<br/>
書き込む最大文字数。

*format*<br/>
書式の指定。

*argptr*<br/>
引数リストへのポインター。

*locale*<br/>
使用するロケール。

詳細については、「 [printf 関数と wprintf 関数の書式指定フィールド](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)」を参照してください。

## <a name="return-value"></a>戻り値

**Vsnprintf**関数は、書き込まれた文字数を返します。終端の null 文字はカウントされません。 *Count*で指定されたバッファーサイズが、 *format*および*argptr*によって指定された出力を格納するのに十分な大きさではない場合、 **vsnprintf**の戻り値は、書き込まれる文字数になります。これは、 *count*が十分に大きい場合、null 文字をカウントしません。 戻り値が*count* -1 より大きい場合、出力は切り捨てられます。 戻り値 -1 は、エンコード エラーが発生したことを示します。

**_Vsnprintf**関数と **_vsnwprintf**関数は、書き込み対象の文字数が*count*以下の場合に書き込まれた文字数を返します。書き込む文字数が*count*よりも大きい場合、これらの関数は、出力が切り捨てられたことを示す-1 を返します。

これらすべての関数によって返される値には、書き込まれているかどうかを問わず、終端の null は含まれません。 *Count*が0の場合、返される値は、関数が書き込む文字の数です。終端の null は含まれません。 この結果を用いて文字列と終端の null に対して十分なバッファー領域を割り当て、関数を再び呼び出してバッファーを埋めることができます。

*Format*が**null**の場合、または*buffer*が**null**で、 *count*が0以外の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**を**EINVAL**に設定します。

## <a name="remarks"></a>Remarks

これらの各関数は、引数リストへのポインターを受け取り、データを書式設定して、*バッファー*が指すメモリに最大文字*数*を書き込みます。 **Vsnprintf**関数は、出力を切り捨てる場合でも、常に null 終端文字を書き込みます。 **_Vsnprintf**と **_vsnwprintf**を使用する場合、バッファーは、末尾に余裕がある場合 (つまり、書き込む文字数が*カウント*未満の場合) にのみ null で終了します。

> [!IMPORTANT]
> 特定の種類のセキュリティリスクを回避するには、その*形式*がユーザー定義の文字列ではないことを確認します。 詳しくは、「 [バッファー オーバーランの回避](/windows/win32/SecBP/avoiding-buffer-overruns)」をご覧ください。

> [!NOTE]
> **_Vsnprintf**、 **_vsnprintf_l**、 **_vsnwprintf**および **_vsnwprintf_l**を呼び出すときに、終端の null 用の空き領域があることを確認するには、 *count*がバッファーの長さより厳密に小さく、バッファーを null に初期化してから、関数を呼び出します。
>
> **Vsnprintf**は常に終端の null を書き込むため、 *count*パラメーターはバッファーのサイズと同じにすることができます。

Visual Studio 2015 と Windows 10 の UCRT 以降、 **vsnprintf**は **_vsnprintf**と同じではなくなりました。 **Vsnprintf**関数は、C99 標準に準拠しています。 **_vnsprintf**は、旧バージョンの Visual Studio code との下位互換性のために残されています。

**_L**サフィックスを持つこれらの関数のバージョンは、現在のスレッドロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

C++ では、これらの関数にテンプレートのオーバーロードがあります。このオーバーロードは、これらの関数に対応するセキュリティで保護された新しい関数を呼び出します。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf**|**_vsnprintf**|**_vsnprintf**|**_vsnwprintf**|
|**_vsntprintf_l**|**_vsnprintf_l**|**_vsnprintf_l**|**_vsnwprintf_l**|

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー (C)|必須ヘッダー (C++)|
|-------------|---------------------------|-------------------------------|
|**vsnprintf**、 **_vsnprintf**、 **_vsnprintf_l**|\<stdio.h>|\<stdio.h> または \<cstdio>|
|**_vsnwprintf**、 **_vsnwprintf_l**|\<stdio.h> または \<wchar.h>|\<stdio.h>、\<wchar.h>、\<cstdio>、または \<cwchar>|

**_Vsnprintf**、 **_vsnprintf_l**、 **_vsnwprintf** 、および **_vsnwprintf_l**の各関数は、Microsoft 固有の関数です。 互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>使用例

```C
// crt_vsnwprintf.c
// compile by using: cl /W3 crt_vsnwprintf.c

// To turn off error C4996, define this symbol:
#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>
#include <wtypes.h>

#define BUFFCOUNT (10)

void FormatOutput(LPCWSTR formatstring, ...)
{
    int nSize = 0;
    wchar_t buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    // Note: _vsnwprintf is deprecated; consider vsnwprintf_s instead
    nSize = _vsnwprintf(buff, BUFFCOUNT - 1, formatstring, args); // C4996
    wprintf(L"nSize: %d, buff: %ls\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput(L"%ls %ls", L"Hi", L"there");
    FormatOutput(L"%ls %ls", L"Hi", L"there!");
    FormatOutput(L"%ls %ls", L"Hi", L"there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

代わりに vsnprintf を使用し、パラメータに小さな文字列を指定すると、挙動が変化します。 *Count*パラメーターにはバッファーのサイズ全体を指定できます。戻り値は、 *count*が十分に大きい場合に書き込まれた文字数です。

## <a name="example"></a>使用例

```C
// crt_vsnprintf.c
// compile by using: cl /W4 crt_vsnprintf.c
#include <stdio.h>
#include <stdarg.h> // for va_list, va_start
#include <string.h> // for memset

#define BUFFCOUNT (10)

void FormatOutput(char* formatstring, ...)
{
    int nSize = 0;
    char buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    nSize = vsnprintf(buff, sizeof(buff), formatstring, args);
    printf("nSize: %d, buff: %s\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput("%s %s", "Hi", "there");   //  8 chars + null
    FormatOutput("%s %s", "Hi", "there!");  //  9 chars + null
    FormatOutput("%s %s", "Hi", "there!!"); // 10 chars + null
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: 10, buff: Hi there!
```

## <a name="see-also"></a>参照

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 系関数](../../c-runtime-library/vprintf-functions.md)<br/>
[書式指定構文: printf 関数と wprintf 関数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)<br/>
