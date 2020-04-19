---
title: fopen、_wfopen
ms.date: 11/04/2016
api_name:
- _wfopen
- fopen
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
- fopen
- _wfopen
- _tfopen
- corecrt_wstdio/_wfopen
- stdio/fopen
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
ms.openlocfilehash: 0e50854cf35dd58f7f59f67ed861247b51fd4541
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957052"
---
# <a name="fopen-_wfopen"></a>fopen、_wfopen

ファイルを開きます。 追加のパラメーター検証を実行してエラー コードを返す、セキュリティが強化されたバージョンの機能が使用できます。「[fopen_s、_wfopen_s](fopen-s-wfopen-s.md)」をご覧ください。

## <a name="syntax"></a>構文

```C
FILE *fopen(
   const char *filename,
   const char *mode
);
FILE *_wfopen(
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>パラメーター

*filename*<br/>
ファイル名。

*mode*<br/>
有効なアクセス種類。

## <a name="return-value"></a>戻り値

これらの各関数は、開いているファイルへのポインターを返します。 エラーが発生すると、NULL のポインター値を返します。 *filename*または*mode*が**NULL**または空の文字列の場合、これらの関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されている無効なパラメーターハンドラーをトリガーします。 実行の継続が許可された場合、これらの関数は**NULL**を返し、 **errno**を**EINVAL**に設定します。

詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**fopen**関数は、 *filename*によって指定されたファイルを開きます。 既定では、*filename*のナロー文字列は、ANSI コードページ (CP_ACP) を使用して解釈されます。 Windows デスクトップ アプリケーションでは、 [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) 関数を使用して、これを OEM コード ページ (CP_OEMCP) に変更できます。 [AreFileApisANSI](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi)関数を使用すると、ANSI またはシステムの既定の OEM コードページを使用して*ファイル名*を解釈するかどうかを判断できます。 **_wfopen**は、 **fopen**のワイド文字バージョンです。 **_wfopen**の引数はワイド文字列です。 それ以外の場合、 **_wfopen**と**fopen**は同じように動作します。 **_wfopen**を使用するだけで、ファイルストリームで使用されるコード化された文字セットには影響しません。

**fopen**は、実行時にファイルシステムで有効なパスを受け入れます。**fopen**は、コードを実行するシステムが実行時に共有または割り当てられたドライブにアクセスできる限り、マップされたネットワークドライブを含む UNC パスとパスを受け入れます。 **fopen**のパスを構築するときは、ドライブ、パス、またはネットワーク共有を実行環境で使用できるようにする必要があります。 ディレクトリのパス区切り記号としてスラッシュ (/) または円記号 (\\) のどちらかを使用できます。

ファイルでその他の操作を実行する前には、必ず戻り値をチェックしてポインターが NULL かどうかを確認します。 エラーが発生した場合は、グローバル変数**errno**が設定され、特定のエラー情報を取得するために使用されることがあります。 詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="unicode-support"></a>Unicode のサポート

**fopen**は Unicode ファイルストリームをサポートしています。 Unicode ファイルを開くには、次のように、目的のエンコードを指定する**ccs**フラグを**fopen**に渡します。

> **FILE \*fp = fopen("newfile.txt", "rt+, ccs=**_encoding_**");**

_encoding_ に使用できる値は、 **UNICODE**、 **UTF-8**、および**UTF-16LE**です。

ファイルが Unicode モードで開かれると、入力関数は、ファイルから読み取ったデータを**wchar_t**型として格納された UTF-16 データに変換します。 Unicode モードで開かれたファイルに書き込む関数は、 **wchar_t**型として格納された UTF-16 データを含むバッファーを想定します。 ファイルが UTF-8 としてエンコードされている場合、UTF-16 データは書き込まれるときに UTF-8 に変換され、ファイルの UTF-8 でエンコードされた内容は読み取られるときに UTF-16 に変換されます。 Unicode モードで奇数バイトの読み取りまたは書き込みを試みると、 [パラメーター検証](../../c-runtime-library/parameter-validation.md) エラーが発生します。 UTF-8 としてプログラムに格納されたデータを読み取るか書き込む場合は、Unicode モードではなくテキストまたはバイナリ ファイル モードを使用します。 必要なエンコード変換は各自が行う必要があります。

既に存在するファイルを読み取り用または追加用に開く場合は、ファイル内にバイト順マーク (BOM: Byte Order Mark) があれば、それによってエンコーディングが決定されます。 BOM エンコーディングは、 **ccs** フラグによって指定されたエンコーディングよりも優先されます。 **ccs** エンコーディングは、BOM が存在しない場合、またはファイルが新しいファイルの場合にのみ使用されます。

> [!NOTE]
> BOM 検出は、Unicode モードで開かれたファイル (つまり、 **ccs**フラグを渡すことによって) にのみ適用されます。

次の表は、ファイル内の**fopen**およびバイト順マークに指定されたさまざまな**ccs**フラグに使用されるモードをまとめたものです。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>ccs フラグおよび BOM に基づいて使用されるエンコーディング

|ccs フラグ|BOM なし (または新しいファイル)|BOM:UTF-8|BOM:UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Unicode モードで書き込むように開かれたファイルには、自動的に BOM が書き込まれます。

*mode*が **"a, ccs=**_encoding_**"** の場合、 **fopen**はまず、読み取りと書き込みの両方のアクセス権を使用してファイルを開こうとします。 成功すると、この関数は BOM を読み取ってファイルのエンコーディングを決定します。失敗した場合は、ファイルに対して既定のエンコーディングを使用します。 どちらの場合も、 **fopen**は書き込み専用アクセスを使用してファイルを再び開きます。 (これは **"a+"** モードではなく **"a"** モードにのみ適用されます)。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

*mode*文字列では、次のように、ファイルに要求されるアクセスの種類を指定します。

|*mode*|アクセス|
|-|-|
| **"r"** | 読み取り用に開きます。 ファイルが存在しないか見つからない場合、 **fopen**呼び出しは失敗します。 |
| **"w"** | 書き込み用に空のファイルを開きます。 指定したファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **"a"** | 末尾に書き込みができるようにファイルを開きます (追加モード)。EOF (end-of-file) マーカーを削除せずにファイルに新しいデータを書き込みます。 ファイルが存在しない場合は、作成します。 |
| **"r+"** | 読み取りと書き込みの両方のモードで開きます。 ファイルが存在している必要があります。 |
| **"w+"** | 読み取りと書き込みの両方のモードで空のファイルを開きます。 そのファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **"a+"** | 読み取りと追加の両方のモードでファイルを開きます。 追加操作には、新しいデータをファイルに書き込む前に EOF マーカーを削除することが含まれます。 書き込みの完了後に、EOF マーカーは復元されません。 ファイルが存在しない場合は、作成します。 |

**"a"** または **"a+"** のアクセスの種類を使用してファイルを開くと、すべての書き込み操作がファイルの末尾で行われます。 ファイルポインターは、 [fseek](fseek-fseeki64.md) または [rewind](rewind.md) を使用して移動できますが、書き込み操作が実行される前に常にファイルの末尾に戻されます。 したがって、既存のデータは上書きされません。

**"a"** モードでは、ファイルに追加する前に EOF マーカーは削除されません。 追加が行われても、MS-DOS TYPE コマンドでは元の EOF マーカーまでのデータしか表示されず、ファイルに追加されたデータは表示されません。 ファイルに追加する前に、 **"a+"** モードで EOF マーカーが削除されます。 追加が終了すると、MS-DOS の TYPE コマンドでファイル内すべてのデータが表示されます。 CTRL + Z EOF マーカーで終了するストリームファイルに追加するには、 **"a+"** モードが必要です。

**"r+"** 、 **"w+"** 、または **"a+"** のアクセスの種類が指定されている場合、読み取りと書き込みの両方が有効になります (ファイルは "更新" 用に開かれていると言います)。 ただし、読み取りから書き込みに切り替えると、入力操作は EOF マーカーを検出する必要があります。 EOF がない場合、ファイル ポジショニング関数の中間の呼び出しを使用する必要があります。 ファイルポジショニング関数は、 **fsetpos**、 [fseek](fseek-fseeki64.md)、および[rewind](rewind.md)です。 書き込みから読み取りに切り替える場合は、 **fflush**またはファイルポジショニング関数のいずれかに介在する呼び出しを使用する必要があります。

前の値に加えて、次の文字を*mode*に追加して、改行文字の変換モードを指定できます。

|*mode*修飾子|変換モード|
|-|-|
| **t** | ファイルをテキスト (変換) モードで開きます。 |
| **b** | バイナリ (無変換) モードで開く復帰文字と改行文字を含む翻訳は抑制されます。 |

テキストモードでは、CTRL + Z は入力時に EOF 文字として解釈されます。 **"a +"** を使用して読み取り/書き込み用に開かれたファイルでは、 **fopen**がファイル末尾に CTRL + Z があるかどうかをチェックし、可能な場合は削除します。 これは、CTRL + Z で終わるファイル内で[fseek](fseek-fseeki64.md)と**ftell**を使用して移動すると、ファイルの末尾付近で[fseek](fseek-fseeki64.md)が正しく動作しない可能性があるためです。

テキストモードでは、キャリッジリターンラインフィードの組み合わせは入力時に1つの改行に変換され、ラインフィード文字は出力時に復帰と改行の組み合わせに変換されます。 Unicode のストリーム入出力関数が既定のテキスト モードで動作すると、入力元または出力先のストリームはマルチバイト文字のシーケンスと仮定されます。 このため、Unicode ストリーム入力関数はマルチバイト文字をワイド文字に変換し、 **mbtowc** 関数を呼び出した場合と同様の効果を得ます。 同様の理由で、Unicode ストリーム出力関数は、 **wctomb** 関数が呼び出されたかのように、ワイド文字をマルチバイト文字に変換します。

**t**または**b**を*mode*で指定しない場合、既定の変換モードは、グローバル変数[_fmode](../../c-runtime-library/fmode.md)によって定義されます。 **t**または**b**が引数の前に付加されている場合、関数は失敗し、 **NULL**を返します。

テキスト モードとバイナリ モードの Unicode およびマルチバイト ストリーム i/o を使用する方法の詳細については、[テキスト モードとバイナリ モードのファイル入出力](../../c-runtime-library/text-and-binary-mode-file-i-o.md)と[テキストとバイナリ モードの Unicode Stream I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)を参照してください。

次のオプションを*mode*に追加すると、追加の動作を指定できます。

|*mode*修飾子|動作|
|-|-|
| **c** | 関連付けられている*ファイル名*のコミットフラグを有効にして、 **fflush**または **_flushall**が呼び出された場合に、ファイルバッファーの内容がディスクに直接書き込まれるようにします。 |
| **n** | 関連付けられている*ファイル名*のコミットフラグを "コミットなし" にリセットします。 既定値です。 プログラムを COMMODE.OBJ とリンクする場合は、グローバル コミット フラグもオーバーライドします。 プログラムを明示的に COMMODE.OBJ とリンクしない場合、グローバル コミット フラグの既定の設定は "コミットなし" です (「 [Link Options](../../c-runtime-library/link-options.md)」をご覧ください)。 |
| **N** | ファイルが子プロセスによって継承されないように指定します。 |
| **S** | キャッシュがディスクからのシーケンシャル アクセスに最適化されるように指定します。ただし、シーケンシャル アクセスに限定されるわけではありません。 |
| **R** | キャッシュがディスクからのランダム アクセスに最適化されるように指定します。ただし、ランダム アクセスに限定されるわけではありません。 |
| **T** | ファイルを一時ファイルとして指定します。 可能な場合、ファイルはディスクにフラッシュされません。 |
| **D** | ファイルを一時ファイルとして指定します。 最後のファイル ポインターが閉じられると、ファイルは削除されます。 |
| **ccs=**_encoding_ | このファイルに使用するエンコードされた文字セット ( **UTF-8**、 **UTF-16LE**、 **UNICODE**のいずれか) を指定します。 何も指定しない場合は、ANSI エンコーディングが使用されます。 |

**fopen** と **_fdopen**で使用される*mode*文字列の有効な文字は、次のように、 [_open](open-wopen.md)および[_sopen](sopen-wsopen.md)で使用される*oflag*引数に対応します。

|*mode*文字列の文字|_open/_sopen の同等の*oflag*値|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_WRONLY**&#124; **_O_APPEND** (通常は **_O_WRONLY** &#124; **_O_CREAT** &#124; **_O_APPEND**)|
|**a+**|**_O_RDWR** &#124; **_O_APPEND** (通常は **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT** )|
|**r**|**_O_RDONLY**|
|**r+**|**_O_RDWR**|
|**w**|**_O_WRONLY** (通常は **_O_WRONLY** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**w+**|**_O_RDWR**(通常は **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**b**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**c**|なし|
|**n**|なし|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs=UNICODE**|**_O_WTEXT**|
|**ccs=UTF-8**|**_O_UTF8**|
|**ccs=UTF-16LE**|**_O_UTF16**|

**rb**モードを使用している場合は、コードを移植する必要はなく、大規模なファイルの大部分を読み取ることが予想される場合や、ネットワークのパフォーマンスに不安がある場合は、オプションとしてメモリマップ Win32 ファイルを使用するかどうかを検討することもできます。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> または \<wchar.h>|

**_wfopen**は Microsoft の拡張機能です。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

**c**、 **n**、 **t**、 **S**、 **R**、 **T**、および **D** *mode*のオプションは、**fopen** と **_fdopen**のための Microsoft 拡張機能であり、ANSI の移植性が必要な場合は使用しないでください。

## <a name="example-1"></a>例 1

次のプログラムは 2 ファイルを開きます。  この例では、 **fclose**を使用して最初のファイルを閉じ、残りのすべての**ファイルを閉じ**ます。

```C
// crt_fopen.c
// compile with: /W3
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   int numclosed;

   // Open for read (will fail if file "crt_fopen.c" does not exist)
   if( (stream  = fopen( "crt_fopen.c", "r" )) == NULL ) // C4996
   // Note: fopen is deprecated; consider using fopen_s instead
      printf( "The file 'crt_fopen.c' was not opened\n" );
   else
      printf( "The file 'crt_fopen.c' was opened\n" );

   // Open for write
   if( (stream2 = fopen( "data2", "w+" )) == NULL ) // C4996
      printf( "The file 'data2' was not opened\n" );
   else
      printf( "The file 'data2' was opened\n" );

   // Close stream if it is not NULL
   if( stream)
   {
      if ( fclose( stream ) )
      {
         printf( "The file 'crt_fopen.c' was not closed\n" );
      }
   }

   // All other files are closed:
   numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="example-2"></a>例 2

次のプログラムでは、Unicode エンコーディングのテキスト モードで、ファイルを作成します (ファイルが存在する場合は上書きします)。  その後、2 つの文字列をファイルに書き込み、ファイルを閉じます。 _wfopen_test.xml というファイルが出力されます。このファイルには、出力セクションのデータが格納されます。

```C
// crt__wfopen.c
// compile with: /W3
// This program creates a file (or overwrites one if
// it exists), in text mode using Unicode encoding.
// It then writes two strings into the file
// and then closes the file.

#include <stdio.h>
#include <stddef.h>
#include <stdlib.h>
#include <wchar.h>

#define BUFFER_SIZE 50

int main(int argc, char** argv)
{
    wchar_t str[BUFFER_SIZE];
    size_t  strSize;
    FILE*   fileHandle;

    // Create an the xml file in text and Unicode encoding mode.
    if ((fileHandle = _wfopen( L"_wfopen_test.xml",L"wt+,ccs=UNICODE")) == NULL) // C4996
    // Note: _wfopen is deprecated; consider using _wfopen_s instead
    {
        wprintf(L"_wfopen failed!\n");
        return(0);
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"<xmlTag>\n");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"</xmlTag>");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Close the file.
    if (fclose(fileHandle))
    {
        wprintf(L"fclose failed!\n");
    }
    return 0;
}
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
