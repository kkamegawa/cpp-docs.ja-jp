---
title: _getch、_getwch
ms.date: 11/04/2016
api_name:
- _getch
- _getwch
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
- api-ms-win-crt-conio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- getwch
- _getch
- _getwch
helpviewer_keywords:
- characters, getting from console
- getch function
- _getwch function
- console, reading from
- _getch function
- getwch function
ms.assetid: cc116be7-cff2-4274-970f-5e7b18ccc05c
ms.openlocfilehash: 122892945e8542afa7f9f944f984387db7c5ec8a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955479"
---
# <a name="_getch-_getwch"></a>_getch、_getwch

エコーなしでコンソールから文字を取得します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _getch( void );
wint_t _getwch( void );
```

## <a name="return-value"></a>戻り値

読み取られた文字を返します。 エラーの戻り値はありません。

## <a name="remarks"></a>Remarks

**_Getch**関数と **_getwch**関数は、文字をエコーしないでコンソールから1文字を読み取ります。 これらの関数のいずれも Ctrl + C の読み取りに使用することはできません。 ファンクション キーまたは方向キーを読み取るときは、各関数を 2 回呼び出す必要があります。最初の呼び出しは 0 または 0xE0 を返し、2 回目の呼び出しは、実際のキー コードを返します。

これらの関数は呼び出し元スレッドをロックするため、スレッド セーフです。 ロックしないバージョンについては、「[_getch_nolock、_getwch_nolock](getch-nolock-getwch-nolock.md)」をご覧ください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_gettch**|**_getch**|**_getch**|**_getwch**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_getch**|\<conio.h>|
|**_getwch**|\<conio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_getch.c
// compile with: /c
// This program reads characters from
// the keyboard until it receives a 'Y' or 'y'.

#include <conio.h>
#include <ctype.h>

int main( void )
{
   int ch;

   _cputs( "Type 'Y' when finished typing keys: " );
   do
   {
      ch = _getch();
      ch = toupper( ch );
   } while( ch != 'Y' );

   _putch( ch );
   _putch( '\r' );    // Carriage return
   _putch( '\n' );    // Line feed
}
```

```Input
abcdefy
```

```Output
Type 'Y' when finished typing keys: Y
```

## <a name="see-also"></a>関連項目

[コンソール入出力とポート入出力](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getche、_getwche](getche-getwche.md)<br/>
[_cgets、_cgetws](../../c-runtime-library/cgets-cgetws.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
[_ungetch、_ungetwch、_ungetch_nolock、_ungetwch_nolock](ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
