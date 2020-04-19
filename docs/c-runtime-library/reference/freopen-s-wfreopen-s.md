---
title: freopen_s、_wfreopen_s
ms.date: 11/04/2016
api_name:
- _wfreopen_s
- freopen_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- freopen_s
- _tfreopen_s
- _wfreopen_s
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
ms.openlocfilehash: 30cd1612045a9f9a69e6ac856a601bac3101467f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956697"
---
# <a name="freopen_s-_wfreopen_s"></a>freopen_s、_wfreopen_s

ファイル ポインターを再度割り当てます。 これらのバージョンの [freopen、_wfreopen](freopen-wfreopen.md) は、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンです。

## <a name="syntax"></a>構文

```C
errno_t freopen(
   FILE** pFile,
   const char *path,
   const char *mode,
   FILE *stream
);
errno_t _wfreopen(
   FILE** pFile,
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*pFile*<br/>
呼び出しが提供するファイル ポインターへのポインター。

*path*<br/>
新しいファイル パス。

*モード*<br/>
アクセス許可の種類。

*一連*<br/>
**FILE** 構造体へのポインター。

## <a name="return-value"></a>戻り値

これらの関数はエラー コードを返します。 エラーが発生した場合、元のファイルは閉じられます。

## <a name="remarks"></a>Remarks

**Freopen_s**関数は、現在*ストリーム*に関連付けられているファイルを閉じ、 *path*によって指定されたファイルに*ストリーム*を再割り当てします。 **_wfreopen_s**は、 **_freopen_s**のワイド文字バージョンです。 **_wfreopen_s**の*path*引数と*mode*引数はワイド文字列です。 それ以外では、 **_wfreopen_s**と **_freopen_s**は同じように動作します。

*PFile*、*パス*、*モード*、または*ストリーム*のいずれかが**NULL**の場合、または*Path*が空の文字列の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は**errno**を**einval**に設定し、 **einval**を返します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s**は通常、事前に開かれているファイル ( **stdin**、 **stdout**、 **stderr** ) をユーザーが指定したファイルにリダイレクトするために使用されます。 *ストリーム*に関連付けられている新しいファイルは、次のように、ファイルに対して要求されるアクセスの種類を指定する文字列である*モード*で開かれます。

|*モード*|アクセス|
|-|-|
| **"r"** | 読み取り用に開きます。 ファイルが存在しないか見つからない場合、 **freopen_s**の呼び出しは失敗します。 |
| **"w"** | 書き込み用に空のファイルを開きます。 指定したファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **"a"** | 末尾に書き込みができるようにファイルを開きます (追加モード)。EOF (end-of-file) マーカーを削除せずにファイルに新しいデータを書き込みます。 ファイルが存在しない場合は、作成します。 |
| **"r+"** | 読み取りと書き込みの両方のモードで開きます。 ファイルが存在している必要があります。 |
| **"w+"** | 読み取りと書き込みの両方のモードで空のファイルを開きます。 そのファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **"a+"** | 読み取りと追加の両方のモードでファイルを開きます。 追加操作には、新しいデータをファイルに書き込む前に EOF マーカーを削除することが含まれます。 書き込みの完了後に、EOF マーカーは復元されません。 ファイルが存在しない場合は、作成します。 |

既存のファイルが破棄される可能性があるため、 **"w"** および **"w +"** の型は注意して使用してください。

ファイルが **"a"** または **"a +"** アクセスの種類で開かれると、すべての書き込み操作はファイルの末尾で行われます。 [Fseek](fseek-fseeki64.md)または[rewind](rewind.md)を使用してファイルポインターを再設定できますが、書き込み操作が実行される前に、ファイルポインターは常にファイルの末尾に戻されます。したがって、既存のデータは上書きされません。

**"A"** モードでは、ファイルに追加する前に EOF マーカーは削除されません。 追加が行われても、MS-DOS TYPE コマンドでは元の EOF マーカーまでのデータしか表示されず、ファイルに追加されたデータは表示されません。 **"A +"** モードでは、ファイルに追加する前に EOF マーカーが削除されます。 追加が終了すると、MS-DOS の TYPE コマンドでファイル内すべてのデータが表示されます。 CTRL + Z EOF マーカーで終了するストリームファイルに追加するには、 **"a +"** モードが必要です。

**"R +"** 、 **"w +"** 、または **"a +"** のアクセスの種類が指定されている場合は、読み取りと書き込みの両方が許可されます (ファイルは "更新" 用に開かれていると言います)。 ただし、読み取りと書き込みを切り替える場合は、その前に [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md)、または [rewind](rewind.md) のいずれかの関数を実行する必要があります。 必要に応じて、 [fsetpos](fsetpos.md)または[fseek](fseek-fseeki64.md)操作に現在の位置を指定できます。 上記の値に加えて、新しい行の変換モードを指定するために、 *mode*文字列に次の文字のいずれかが含まれている場合があります。

|*モード*修飾子|変換モード|
|-|-|
| **t** | ファイルをテキスト (変換) モードで開きます。 |
| **b** | バイナリ (無変換) モードで開く復帰文字と改行文字を含む翻訳は抑制されます。 |

テキスト (変換) モードでは、キャリッジリターンラインフィード (CR-LF) の組み合わせは入力時に1つの改行 (LF) 文字に変換されます。LF 文字は、出力時に cr-lf の組み合わせに変換されます。 また、Ctrl + Z は入力時に EOF (end-of-file) 文字として解釈されます。 読み取りまたは書き込みのために開かれたファイルと **"a +"** での読み取りの場合、ランタイムライブラリは、ファイルの末尾に CTRL + Z があるかどうかをチェックし、可能な場合は削除します。 これは、 [fseek](fseek-fseeki64.md)と[ftell](ftell-ftelli64.md)を使用してファイル内を移動すると、ファイルの末尾付近で[fseek](fseek-fseeki64.md)が正しく動作しなくなる可能性があるためです。 **T**オプションは、ANSI の移植性が必要な場合に使用しない Microsoft の拡張機能です。

**T**または**b**を*モード*で指定しない場合、既定の変換モードは、グローバル変数[_fmode](../../c-runtime-library/fmode.md)によって定義されます。 **T**または**b**が引数の前に付加されている場合、関数は失敗し、 **NULL**を返します。

テキスト モードと binary モードの詳細については、「[テキスト モードとバイナリ モードのファイル入出力](../../c-runtime-library/text-and-binary-mode-file-i-o.md)」を参照してください。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h> または \<wchar.h>|

コンソールは、ユニバーサル Windows プラットフォーム (UWP) アプリではサポートされていません。 コンソール、 **stdin**、 **stdout**、および**stderr**に関連付けられている標準ストリームハンドルは、C ランタイム関数が UWP アプリで使用できるようになる前にリダイレクトする必要があります。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_freopen_s.c
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.

#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   errno_t err;
   // Reassign "stderr" to "freopen.out":
   err = freopen_s( &stream, "freopen.out", "w", stderr );

   if( err != 0 )
      fprintf( stdout, "error on freopen\n" );
   else
   {
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );
      fprintf( stream, "This will go to the file 'freopen.out'\n" );
      fclose( stream );
   }
   system( "type freopen.out" );
}
```

```Output
successfully reassigned
This will go to the file 'freopen.out'
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
