---
title: gets、_getws
ms.date: 11/04/2016
api_name:
- _getws
- gets
api_location:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getts
- gets
- _getws
helpviewer_keywords:
- getws function
- getts function
- _getws function
- lines, getting
- streams, getting lines
- _getts function
- gets function
- standard input, reading from
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
ms.openlocfilehash: f4e052f91dd2b4adfd5fd7e1ad7c81e0e5b07a11
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300275"
---
# <a name="gets-_getws"></a>gets、_getws

`stdin` ストリームから行を取得します。 これらの関数のセキュリティを強化したバージョンを使用できます。「 [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)」を参照してください。

> [!IMPORTANT]
>  これらは古い関数です。 Visual Studio 2015 以降では、CRT で使用できません。 これらの関数のセキュリティを強化したバージョン gets_s および _getws_s は、引き続き使用できます。 これらの代替関数の詳細については、「 [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)」を参照してください。

> [!IMPORTANT]
>  この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```
char *gets(
   char *buffer
);
wchar_t *_getws(
   wchar_t *buffer
);
template <size_t size>
char *gets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_getws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>パラメーター

*バッファー*<br/>
入力文字列の格納場所。

## <a name="return-value"></a>戻り値

正常に終了した場合はその引数を返します。 エラーが発生した場合またはファイルの終端に達した場合は、**NULL** ポインターを返します。 どちらが発生したかを確認するには、 [ferror](../c-runtime-library/reference/ferror.md) または [feof](../c-runtime-library/reference/feof.md) を使用します。 `buffer` が **NULL** の場合は、「[パラメーターの検証](../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーター ハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は **NULL** を返し、errno を `EINVAL`に設定します。

## <a name="remarks"></a>コメント

`gets` 関数は、 `stdin` 標準入力ストリームから行を読み取り、 `buffer`に格納します。 行は、最初の改行文字 ('\n') までのすべての文字 (改行文字を含む) で構成されます。 `gets` は、行を返す前に、改行文字を null 文字 ('\0') に置き換えます。 これとは対照的に、`fgets` 関数は改行文字を保持します。 ワイド文字を扱う場合は、`_getws` ではなく `gets`を使用します。引数にはワイド文字列を指定します。また戻り値もワイド文字列です。

> [!IMPORTANT]
>  gets で読み取る文字の数を制限する方法がないため、信頼できない入力によってバッファー オーバーランが発生しやすくなります。 代わりに、 `fgets` を使用してください。

C++ では、これらの関数にテンプレートのオーバーロードがあります。このオーバーロードは、これらの関数に対応するセキュリティで保護された新しい関数を呼び出します。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../c-runtime-library/secure-template-overloads.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_getts`|`gets`|`gets`|`_getws`|

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|`gets`|\<stdio.h>|
|`_getws`|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「[互換性](../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>使用例

```c
// crt_gets.c
// compile with: /WX /W3

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets( line );  // C4996
   // Danger: No way to limit input to 20 chars.
   // Consider using gets_s instead.
   printf( "The line entered was: %s\n", line );
}
```

入力が 20 文字を超えると、行バッファーのオーバーランが発生し、ほぼ確実にプログラムがクラッシュします。

```Output

Hello there!The line entered was: Hello there!
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../c-runtime-library/stream-i-o.md)<br/>
[fgets、fgetws](../c-runtime-library/reference/fgets-fgetws.md)<br/>
[fputs、fputws](../c-runtime-library/reference/fputs-fputws.md)<br/>
[puts、_putws](../c-runtime-library/reference/puts-putws.md)
