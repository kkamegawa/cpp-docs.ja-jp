---
title: _cscanf、_cscanf_l、_cwscanf、_cwscanf_l
ms.date: 10/21/2019
api_name:
- _cscanf_l
- _cscanf
- _cwscanf
- _cwscanf_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cwscanf
- cwscanf_l
- tcscanf_l
- _tcscanf_l
- _cscanf
- _cscanf_l
- tcscanf
- cwscanf
- _cwscanf_l
- cscanf_l
- _tcscanf
helpviewer_keywords:
- _cwscanf function
- data [C++], reading from the console
- cscanf_l function
- tcscanf function
- _cscanf_l function
- cwscanf function
- _tcscanf_l function
- _cscanf function
- _tcscanf function
- cwscanf_l function
- tcscanf_l function
- reading data [C++], from the console
- _cwscanf_l function
ms.assetid: dbfe7547-b577-4567-a1cb-893fa640e669
ms.openlocfilehash: 8b996e510d6a8c106aa88a60a8da456d36a4b3e5
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778310"
---
# <a name="_cscanf-_cscanf_l-_cwscanf-_cwscanf_l"></a>_cscanf、_cscanf_l、_cwscanf、_cwscanf_l

コンソールから書式化されたデータを読み出します。 これらの関数のセキュリティを強化したバージョンを使用できます。「[_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)」を参照してください。

> [!NOTE] 
> Visual Studio 2015 では、`printf` および `scanf` の関数ファミリが**inline**として宣言され、`<stdio.h>` と `<conio.h>` のヘッダーに移動されました。 古いコードを移行する場合、これらの関数との接続に*LNK2019*が表示されることがあります。 詳細については、「[ビジュアルC++の変更履歴 2003-2015](../../porting/visual-cpp-change-history-2003-2015.md#stdio_and_conio)」を参照してください。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _cscanf(
   const char *format [,
   argument] ...
);
int _cscanf_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _cwscanf(
   const wchar_t *format [,
   argument] ...
);
int _cwscanf_l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>パラメーター

*format*<br/>
書式指定文字列。

*argument*<br/>
省略可能なパラメーター。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

正常に変換され、割り当てられたフィールドの数。 戻り値には、読まれたが割り当てられなかったフィールドは含まれません。 ファイルの終端で読み取ろうとした場合、戻り値は**EOF**です。 これは、キーボード入力がオペレーティング システムのコマンド ラインのレベルでリダイレクトされる場合に発生します。 戻り値が 0 の場合は、代入されたフィールドがなかったことを意味します。

## <a name="remarks"></a>Remarks

**_Cscanf**関数は、*引数*によって指定された場所に、コンソールから直接データを読み取ります。 [_getche](getch-getwch.md) 関数は文字を読み取るために使用されます。 省略可能な各パラメーターは、*形式*の型指定子に対応する型を持つ変数へのポインターである必要があります。 この形式は、入力フィールドの解釈を制御し、 [scanf](scanf-scanf-l-wscanf-wscanf-l.md)関数の*format*パラメーターと同じ形式と機能を持ちます。 **_Cscanf**は通常、入力文字をエコーしますが、最後の呼び出しが **_ungetch**になった場合は無効になります。

この関数は、パラメーターを検証します。 Format が**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno**は**EINVAL**に設定され、関数は**EOF**を返します。

**_L**サフィックスを持つこれらの関数のバージョンは、現在のスレッドロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcscanf**|**_cscanf**|**_cscanf**|**_cwscanf**|
|**_tcscanf_l**|**_cscanf_l**|**_cscanf_l**|**_cwscanf_l**|

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_cscanf**、 **_cscanf_l**|\<conio.h>|
|**_cwscanf**、 **_cwscanf_l**|\<conio.h> または \<wchar.h>|

互換性について詳しくは、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_cscanf.c
// compile with: /c /W3
/* This program prompts for a string
* and uses _cscanf to read in the response.
* Then _cscanf returns the number of items
* matched, and the program displays that number.
*/

#include <stdio.h>
#include <conio.h>

int main( void )
{
   int   result, i[3];

   _cprintf_s( "Enter three integers: ");
   result = _cscanf( "%i %i %i", &i[0], &i[1], &i[2] ); // C4996
   // Note: _cscanf is deprecated; consider using _cscanf_s instead
   _cprintf_s( "\r\nYou entered " );
   while( result-- )
      _cprintf_s( "%i ", i[result] );
   _cprintf_s( "\r\n" );
}
```

```Input
1 2 3
```

```Output
Enter three integers: 1 2 3
You entered 3 2 1
```

## <a name="see-also"></a>関連項目

[コンソール入出力とポート入出力](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
