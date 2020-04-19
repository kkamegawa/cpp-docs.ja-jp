---
title: _fsopen、_wfsopen
ms.date: 11/04/2016
api_name:
- _wfsopen
- _fsopen
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
- wfsopen
- fsopen
- tfsopen
- _tfsopen
- _wfsopen
- _fsopen
helpviewer_keywords:
- opening files, streams
- fsopen function
- tfsopen function
- wfsopen function
- _fsopen function
- files [C++], opening
- _tfsopen function
- _wfsopen function
- file sharing [C++]
ms.assetid: 5e4502ab-48a9-4bee-a263-ebac8d638dec
ms.openlocfilehash: 1ffc3aa5801ff2ed63ecf815f3351e4d7a8cf459
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956480"
---
# <a name="_fsopen-_wfsopen"></a>_fsopen、_wfsopen

ファイル共有付きでストリームを開きます。

## <a name="syntax"></a>構文

```C
FILE *_fsopen(
   const char *filename,
   const char *mode,
   int shflag
);
FILE *_wfsopen(
   const wchar_t *filename,
   const wchar_t *mode,
   int shflag
);
```

### <a name="parameters"></a>パラメーター

*ファイル名*<br/>
開くファイルの名前。

*モード*<br/>
アクセス許可の種類。

*shflag*<br/>
許可される共有の種類。

## <a name="return-value"></a>戻り値

これらの各関数は、ストリームへのポインターを返します。 エラーが発生すると、NULL のポインター値を返します。 *Filename*または*mode*が**NULL**または空の文字列の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は**NULL**を返し、 **errno**を**EINVAL**に設定します。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Fsopen**関数は、 *filename*によって指定されたファイルをストリームとして開き、mode および*shflag*引数で定義されているように、後続の共有の読み取りまたは書き込み用にファイルを準備します。 **_wfsopen**は、 **_fsopen**のワイド文字バージョンです。 **_wfsopen**の*filename*引数と*mode*引数はワイド文字列です。 それ以外では、 **_wfsopen**と **_fsopen**は同じように動作します。

文字列*モード*では、次の表に示すように、ファイルに対して要求されるアクセスの種類を指定します。

|用語|定義|
|----------|----------------|
|**"r"**|読み取り用に開きます。 ファイルが存在しないか見つからない場合、 **_fsopen**の呼び出しは失敗します。|
|**"w"**|書き込み用に空のファイルを開きます。 指定したファイルが既に存在すると、そのファイルの内容は破棄されます。|
|**"a"**|ファイルの末尾への書き込み用にファイルを開きます (追加モード)。ファイルが存在しない場合は、まず、ファイルを作成します。|
|**"r+"**|読み取りと書き込みの両方のモードで開きます。 ファイルが存在している必要があります。|
|**"w+"**|読み取りと書き込みの両方のモードで空のファイルを開きます。 指定したファイルが既に存在すると、そのファイルの内容は破棄されます。|
|**"a+"**|読み取りおよび追加用にファイルを開きます。ファイルが存在しない場合は、まず、ファイルを作成します。|

既存のファイルが破棄される可能性があるため、 **"w"** および **"w +"** の型は注意して使用してください。

**"A"** または **"a +"** アクセスの種類を使用してファイルを開くと、すべての書き込み操作がファイルの末尾で行われます。 ファイルポインターは、 [fseek](fseek-fseeki64.md)または[rewind](rewind.md)を使用して再配置できますが、書き込み操作が実行される前に、常にファイルの末尾に戻されます。したがって、既存のデータは上書きされません。 **"R +"** 、 **"w +"** 、または **"a +"** のアクセスの種類が指定されている場合は、読み取りと書き込みの両方が許可されます (ファイルは更新のために開かれていると言います)。 ただし、読み取りと書き込みを切り替える場合は、その前に [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md)、または [rewind](rewind.md) のいずれかの操作を実行する必要があります。 必要に応じて、 [fsetpos](fsetpos.md)または[fseek](fseek-fseeki64.md)操作に現在の位置を指定できます。 上記の値に加えて、次のいずれかの文字を*モード*で使用して、新しい行の変換モードとファイル管理を指定できます。

|用語|定義|
|----------|----------------|
|**t**|ファイルをテキスト (変換) モードで開きます。 このモードでは、キャリッジリターンラインフィード (CR-LF) の組み合わせは入力時に単一行フィード (LF) に変換され、LF 文字は出力時に cr-lf の組み合わせに変換されます。 また、Ctrl + Z は入力時に EOF (end-of-file) 文字として解釈されます。 読み取りまたは読み取り/書き込み用に開かれたファイルでは、 **_fsopen**がファイル末尾に CTRL + Z があるかどうかを確認し、削除できる場合は削除します。 これは、CTRL + Z で終わるファイル内で[fseek](fseek-fseeki64.md)と[ftell](ftell-ftelli64.md)を使用して移動すると、ファイルの末尾付近で[fseek](fseek-fseeki64.md)が正しく動作しない可能性があるためです。|
|**b**|ファイルをバイナリ (無変換) モードで開き、前述の変換は行いません。|
|**S**|キャッシュがディスクからのシーケンシャル アクセスに最適化されるように指定します。ただし、シーケンシャル アクセスに限定されるわけではありません。|
|**R**|キャッシュがディスクからのランダム アクセスに最適化されるように指定します。ただし、ランダム アクセスに限定されるわけではありません。|
|**T**|ファイルを一時ファイルとして指定します。 可能な場合、ファイルはディスクにフラッシュされません。|
|**D**|ファイルを一時ファイルとして指定します。 最後のファイル ポインターが閉じられると、ファイルは削除されます。|

**t** または **b** を *mode* に指定しない場合、変換モードは既定のモード変数 **_fmode** によって定義されます。 **T**または**b**が引数の前に付加されている場合、関数は失敗し、 **NULL**を返します。 テキスト モードと binary モードの詳細については、「[テキスト モードとバイナリ モードのファイル入出力](../../c-runtime-library/text-and-binary-mode-file-i-o.md)」を参照してください。

引数*shflag*は、次のマニフェスト定数のいずれかで構成される定数式で、resource.h に定義されています。

|用語|定義|
|----------|----------------|
|**互換性 (_S)**|16 ビット アプリケーションの互換モードを設定します。|
|**(_L)**|読み取りおよび書き込みアクセスを許可します。|
|**検索 (_D)**|ファイルへの読み取りアクセスを拒否します。|
|**(_L)**|ファイルへの読み取りおよび書き込みアクセスを拒否します。|
|**_SH_DENYWR**|ファイルへの書き込みアクセスを拒否します。|

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|省略可能なヘッダー|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> *Shflag*パラメーターのマニフェスト定数。|
|**_wfsopen**|\<stdio.h> または \<wchar.h>|\<share.h><br /><br /> *Shflag*パラメーターのマニフェスト定数。|

## <a name="example"></a>例

```C
// crt_fsopen.c

#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   FILE *stream;

   // Open output file for writing. Using _fsopen allows us to
   // ensure that no one else writes to the file while we are
   // writing to it.
    //
   if( (stream = _fsopen( "outfile", "wt", _SH_DENYWR )) != NULL )
   {
      fprintf( stream, "No one else in the network can write "
                       "to this file until we are done.\n" );
      fclose( stream );
   }
   // Now others can write to the file while we read it.
   system( "type outfile" );
}
```

```Output
No one else in the network can write to this file until we are done.
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
