---
title: _cgets、_cgetws
ms.date: 11/04/2016
api_name:
- _cgetws
- _cgets
api_location:
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-conio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cgetws
- _cgetws
- _cgets
helpviewer_keywords:
- _cgetws function
- strings [C++], getting from console
- console, getting strings from
- _cgets function
- cgetws function
- cgets function
ms.assetid: 4d5e134a-58c3-4f62-befd-5d235b0212f4
ms.openlocfilehash: 97a8de0a7fd0f278e6b0e3730a52ca3d0be6e07a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299001"
---
# <a name="_cgets-_cgetws"></a>_cgets、_cgetws

コンソールから文字列を取得します。 これらの関数のセキュリティを強化したバージョンを使用できます。「 [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)」を参照してください。

> [!IMPORTANT]
>  これらは古い関数です。 Visual Studio 2015 以降では、CRT で使用できません。 これらの関数のセキュリティを強化したバージョン _cgets_s および _cgetws_s は、引き続き使用できます。 これらの代替関数の詳細については、「 [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)」を参照してください。

> [!IMPORTANT]
>  この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```
char *_cgets(
   char *buffer
);
wchar_t *_cgetws(
   wchar_t *buffer
);
template <size_t size>
char *_cgets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_cgetws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>パラメーター

*バッファー*<br/>
データの格納場所。

## <a name="return-value"></a>戻り値

`_cgets` と `_cgetws` は文字列の先頭である `buffer[2]`へのポインターを返します。 `buffer` が **NULL** の場合は、「[パラメーターの検証](../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーター ハンドラーを呼び出します。 実行の継続が許可された場合、これらは **NULL** を返し、`errno` を `EINVAL` に設定します。

## <a name="remarks"></a>コメント

これらの関数は、コンソールから文字列を読み込み、 `buffer`が指す位置に文字列とその長さを格納します。 `buffer` パラメーターは文字配列へのポインターである必要があります。 配列の最初の要素 ( `buffer[0]`) には、読み取る文字列の最大長 (文字数) を格納します。 配列は、文字列、終端の null 文字 ('\0')、およびその他の 2 バイト分を格納するのに十分な要素を持つ必要があります。 関数は、文字をキャリッジ リターンとラインフィード (CR-LF) の組み合わせが現れるか、指定した文字数を読み取るまで文字を読み取ります。 文字列は `buffer[2]`を先頭として格納されます。 関数が CR-LF を読み取ると、null 文字 ('\0') を格納します。 次に、関数は 2 番目の配列要素である `buffer[1]`に文字列の実際の長さを格納します。

コンソール ウィンドウでは、 `_cgets` または `_cgetws` が呼び出されたときにはすべての編集キーがアクティブになっているため、F3 キーを押すと最後に入力したエントリが繰り返されます。

C++ では、これらの関数にテンプレートのオーバーロードがあります。このオーバーロードは、これらの関数に対応するセキュリティで保護された新しい関数を呼び出します。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../c-runtime-library/secure-template-overloads.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|`_cgets`|\<conio.h>|
|`_cgetws`|\<conio.h> または \<wchar.h>|

互換性について詳しくは、「 [Compatibility](../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="example"></a>使用例

```c
// crt_cgets.c
// compile with: /c /W3
// This program creates a buffer and initializes
// the first byte to the size of the buffer. Next, the
// program accepts an input string using _cgets and displays
// the size and text of that string.

#include <conio.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
   char buffer[83] = { 80 };  // Maximum characters in 1st byte
   char *result;

   printf( "Input line of text, followed by carriage return:\n");

   // Input a line of text:
   result = _cgets( buffer ); // C4996
   // Note: _cgets is deprecated; consider using _cgets_s
   if (!result)
   {
      printf( "An error occurred reading from the console:"
              " error code %d\n", errno);
   }
   else
   {
      printf( "\nLine length = %d\nText = %s\n",
              buffer[1], result );
   }
}
```

```Output

      A line of input.Input line of text, followed by carriage return:
Line Length = 16
Text = A line of input.
```

## <a name="see-also"></a>関連項目

[コンソール入出力とポート入出力](../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch、_getwch](../c-runtime-library/reference/getch-getwch.md)
