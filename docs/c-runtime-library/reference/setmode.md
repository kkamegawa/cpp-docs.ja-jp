---
title: _setmode
ms.date: 11/04/2016
apiname:
- _setmode
apilocation:
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 67cca27ba03a99d7e192d438a98f1bb3a93845ee
ms.sourcegitcommit: cce52b2232b94ce8fd8135155b86e2d38a4e4562
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54031279"
---
# <a name="setmode"></a>_setmode

ファイルの変換モードを設定します。

## <a name="syntax"></a>構文

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
ファイル記述子。

*モード*<br/>
新しい変換モード。

## <a name="return-value"></a>戻り値

成功した場合、前の変換モードを返します。

この関数に無効なパラメーターが渡されると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように無効なパラメーター ハンドラーが呼び出されます。 実行が続行すると、この関数は-1 を返し、セットを許可された場合**errno**いずれかに**EBADF**、無効なファイル記述子では、これを示しますまたは**EINVAL**を無効なことを示します*モード*引数。

リターン コードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Setmode**関数に設定*モード*により与えられたファイルの変換モード*fd*します。 渡す **_O_TEXT**として*モード*設定 (変換) をテキスト モード。 キャリッジ リターンとライン フィード (CR-LF) の組み合わせは、1 つのライン フィード文字の入力に変換されます。 ライン フィード文字は、出力時に CR-LF の組み合わせに変換されます。 渡す **_O_BINARY**バイナリ (無変換) モードを設定、これらの翻訳が抑制されます。

渡すこともできます **_O_U16TEXT**、 **_O_U8TEXT**、または **_O_WTEXT**このドキュメントの後半では、2 番目の例に示すように、Unicode モードを有効にします。

> [!CAUTION]
> Unicode モードがワイド印刷機能のためには (たとえば、 `wprintf`) と幅の狭いの印刷機能はサポートされていません。 Unicode モードのストリームの幅の狭い印刷関数を使用するには、アサートがトリガーされます。

**_setmode**の既定の変換モードを変更するのには通常使用**stdin**と**stdout**が任意のファイルで使用することができます。 適用した場合 **_setmode**をストリームのファイル記述子、呼び出す **_setmode**入力または出力ストリームで操作を実行する前にします。

> [!CAUTION]
> データを書き込むファイル ストリームでは、明示的にフラッシュ、コードを使用して場合[fflush](fflush.md)を使用する前に **_setmode**モードを変更します。 コードをフラッシュしないと、予期しない動作が発生することがあります。 ストリームにデータを書き込んでいない場合は、コードをフラッシュする必要はありません。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|省略可能なヘッダー|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_setmode.c
// This program uses _setmode to change
// stdin from text mode to binary mode.

#include <stdio.h>
#include <fcntl.h>
#include <io.h>

int main( void )
{
   int result;

   // Set "stdin" to have binary mode:
   result = _setmode( _fileno( stdin ), _O_BINARY );
   if( result == -1 )
      perror( "Cannot set mode" );
   else
      printf( "'stdin' successfully changed to binary mode\n" );
}
```

```Output
'stdin' successfully changed to binary mode
```

## <a name="example"></a>例

```C
// crt_setmodeunicode.c
// This program uses _setmode to change
// stdout to Unicode. Cyrillic and Ideographic
// characters will appear on the console (if
// your console font supports those character sets).

#include <fcntl.h>
#include <io.h>
#include <stdio.h>

int main(void) {
    _setmode(_fileno(stdout), _O_U16TEXT);
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");
    return 0;
}
```

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
