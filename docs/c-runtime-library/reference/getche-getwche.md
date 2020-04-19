---
title: _getche、_getwche
ms.date: 11/04/2016
api_name:
- _getwche
- _getche
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
- getwche
- _getche
- _getwche
helpviewer_keywords:
- characters, getting from console
- _getwche function
- getche function
- console, reading from
- getwche function
- _getche function
ms.assetid: eac978a8-c43a-4130-938f-54f12e2a0fda
ms.openlocfilehash: cf7aa10702dca5118d03d7ce2e2d4341941fc51c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955328"
---
# <a name="_getche-_getwche"></a>_getche、_getwche

エコーありでコンソールから文字を取得します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _getche( void );
wint_t _getwche( void );
```

## <a name="return-value"></a>戻り値

読み取られた文字を返します。 エラーの戻り値はありません。

## <a name="remarks"></a>Remarks

**_Getche**関数と **_getwche**関数は、echo を使用してコンソールから1文字を読み取ります。つまり、その文字がコンソールに表示されます。 これらの関数のいずれも Ctrl + C の読み取りに使用することはできません。 ファンクション キーまたは方向キーを読み取るときは、各関数を 2 回呼び出す必要があります。最初の呼び出しは 0 または 0xE0 を返し、2 回目の呼び出しは、実際のキー コードを返します。

これらの関数は呼び出し元スレッドをロックするため、スレッド セーフです。 ロックしないバージョンについては、「[_getche_nolock、_getwche_nolock](getche-nolock-getwche-nolock.md)」をご覧ください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_getche**|**_getche**|**_getch**|**_getwche**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_getche**|\<conio.h>|
|**_getwche**|\<conio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_getche.c
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
      ch = _getche();
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
Type 'Y' when finished typing keys: abcdefyY
```

## <a name="see-also"></a>関連項目

[コンソール入出力とポート入出力](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cgets、_cgetws](../../c-runtime-library/cgets-cgetws.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
[_ungetch、_ungetwch、_ungetch_nolock、_ungetwch_nolock](ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
