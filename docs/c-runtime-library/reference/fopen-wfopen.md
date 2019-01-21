---
title: fopen、_wfopen
ms.date: 11/04/2016
apiname:
- _wfopen
- fopen
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
ms.openlocfilehash: fb5f78411521dcbaddefda6c621b7fe44ce91736
ms.sourcegitcommit: cce52b2232b94ce8fd8135155b86e2d38a4e4562
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54031292"
---
# <a name="fopen-wfopen"></a>fopen、_wfopen

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

*ファイル名*<br/>
ファイル名。

*モード*<br/>
有効なアクセス種類。

## <a name="return-value"></a>戻り値

これらの各関数は、開いているファイルへのポインターを返します。 エラーが発生すると、NULL のポインター値を返します。 場合*filename*または*モード*は**NULL**または空の文字列の場合は、これらの関数トリガーでは説明されている無効なパラメーター ハンドラーを[パラメーター検証](../../c-runtime-library/parameter-validation.md)です。 これらの関数を返すかどうかは、引き続き実行が許可された、 **NULL**設定と**errno**に**EINVAL**します。

詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**Fopen**関数で指定されているファイルが開きます*filename*します。 既定では、幅の狭い*filename* ANSI コード ページ (CP_ACP) を使用して文字列を解釈します。 Windows デスクトップ アプリケーションでは、 [SetFileApisToOEM](/windows/desktop/api/fileapi/nf-fileapi-setfileapistooem) 関数を使用して、これを OEM コード ページ (CP_OEMCP) に変更できます。 使用することができます、 [AreFileApisANSI](/windows/desktop/api/fileapi/nf-fileapi-arefileapisansi)を判断する関数かどうか*filename* ANSI またはシステム既定の OEM コード ページを使用して解釈されます。 **_wfopen**のワイド文字バージョンは、 **fopen**; 引数 **_wfopen**はワイド文字列です。 それ以外の場合、 **_wfopen**と**fopen**動作は同じです。 だけを使用して **_wfopen**ファイル ストリームで使用されているコード化文字セットには影響しません。

**fopen**の実行時にファイル システムでは有効なパスを受け取ります**fopen**はマップ済みネットワーク ドライブをコードを実行するシステムに共有へのアクセスまたは実行時にマップされたドライブの UNC パスとを含むパスを受け取ります。 パスを構築する際に**fopen**ドライブ、パス、またはネットワーク共有される実行環境で使用できるかどうかを確認します。 ディレクトリのパス区切り記号としてスラッシュ (/) または円記号 (\\) のどちらかを使用できます。

ファイルでその他の操作を実行する前には、必ず戻り値をチェックしてポインターが NULL かどうかを確認します。 エラーが発生するグローバル変数場合**errno**が設定され、特定のエラー情報を取得するために使用可能性があります。 詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="unicode-support"></a>Unicode のサポート

**fopen** Unicode のファイル ストリームをサポートしています。 Unicode ファイルを開くには、渡す、 **ccs**に目的のエンコーディングを指定するフラグ**fopen**、次のようにします。

> **ファイル*fp = fopen ("newfile.txt"、"rt + ccs =**_エンコード_**");**

値を許可*エンコード*は**UNICODE**、 **utf-8**、および**UTF 16LE**します。

入力関数の型として格納された utf-16 データに、ファイルから読み取られるデータは変換ファイルが Unicode モードで開かれる、ときに**wchar_t**します。 Unicode モードで開かれたファイルに書き込む関数は、型として格納された utf-16 データを含んでいるバッファーを想定**wchar_t**します。 ファイルが UTF-8 としてエンコードされている場合、UTF-16 データは書き込まれるときに UTF-8 に変換され、ファイルの UTF-8 でエンコードされた内容は読み取られるときに UTF-16 に変換されます。 Unicode モードで奇数バイトの読み取りまたは書き込みを試みると、 [パラメーター検証](../../c-runtime-library/parameter-validation.md) エラーが発生します。 UTF-8 としてプログラムに格納されたデータを読み取るか書き込む場合は、Unicode モードではなくテキストまたはバイナリ ファイル モードを使用します。 必要なエンコード変換は各自が行う必要があります。

既に存在するファイルを読み取り用または追加用に開く場合は、ファイル内にバイト順マーク (BOM: Byte Order Mark) があれば、それによってエンコーディングが決定されます。 BOM エンコーディングよりも優先されるエンコードによって指定されるは、 **ccs**フラグ。 **Ccs** BOM が存在しないか、ファイルが新しいファイルがある場合にのみ使用がエンコードされます。

> [!NOTE]
> BOM 検出は、Unicode モードで開かれたファイルにのみ適用されます (つまりを渡して、 **ccs**フラグ)。

次の表に、さまざまな使用されるモード**ccs**に指定されたフラグ**fopen**ファイル内のバイト順マークします。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>ccs フラグおよび BOM に基づいて使用されるエンコーディング

|ccs フラグ|BOM なし (または新しいファイル)|BOM:UTF-8|BOM:UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Unicode モードで書き込むように開かれたファイルには、自動的に BOM が書き込まれます。

場合*モード*は **"、ccs =**_エンコード_**"**、 **fopen**読み書きの両方を使用して、ファイルを開くには、まずおよび書き込みアクセス。 成功すると、この関数は BOM を読み取ってファイルのエンコーディングを決定します。失敗した場合は、ファイルに対して既定のエンコーディングを使用します。 いずれの場合も、 **fopen**は、ファイルを再度開く書き込み専用アクセスを使用しています。 (これに適用されます **"a"** モードのみが、 **「a +」** モード)。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

文字の文字列*モード*ファイルは、次のように要求するアクセスの種類を指定します。

|*モード*|アクセス|
|-|-|
| **"r"** | 読み取り用に開きます。 ファイルが存在しないか見つからない場合、 **fopen**呼び出しは失敗します。 |
| **"w"** | 書き込み用に空のファイルを開きます。 指定したファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **"a"** | 末尾に書き込みができるようにファイルを開きます (追加モード)。EOF (end-of-file) マーカーを削除せずにファイルに新しいデータを書き込みます。 ファイルが存在しない場合は、作成します。 |
| **"r+"** | 読み取りと書き込みの両方のモードで開きます。 ファイルが存在している必要があります。 |
| **"w+"** | 読み取りと書き込みの両方のモードで空のファイルを開きます。 そのファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **"a+"** | 読み取りと追加の両方のモードでファイルを開きます。 追加操作には、新しいデータをファイルに書き込む前に EOF マーカーを削除することが含まれます。 書き込みの完了後に、EOF マーカーは復元されません。 ファイルが存在しない場合は、作成します。 |

使用してファイルを開くと、 **"a"** アクセスの種類または **「a +」** アクセスの種類、すべての書き込み操作、ファイルの末尾から行われます。 使用して、ファイル ポインターの位置を変更できる[fseek](fseek-fseeki64.md)または[巻き戻し](rewind.md)は常に戻さファイルの末尾に、書き込み操作が実行される前にします。 したがって、既存のデータは上書きされません。

**"A"** ファイルに追加の前に、モードが EOF マーカーを削除できません。 追加が行われても、MS-DOS TYPE コマンドでは元の EOF マーカーまでのデータしか表示されず、ファイルに追加されたデータは表示されません。 ファイルに追加の前に、 **「a +」** モードでは、EOF マーカーを削除します。 追加が終了すると、MS-DOS の TYPE コマンドでファイル内すべてのデータが表示されます。 **「A +」** モードが CTRL + Z EOF マーカーで終了するストリーム ファイルを追加するために必要です。

ときに、 **「r +」**、 **「w +」**、または **「a +」** アクセスの種類を指定すると、読み取りと書き込みの両方が有効になっている (ファイルが開かれると言います"update")。 ただし、読み取りから書き込みに切り替えると、入力操作は EOF マーカーを検出する必要があります。 EOF がない場合、ファイル ポジショニング関数の中間の呼び出しを使用する必要があります。 ファイル ポジショニング関数は**fsetpos**、 [fseek](fseek-fseeki64.md)、および[巻き戻し](rewind.md)します。 書き込みから読み取りに切り替えたときに中間の呼び出しを使用する必要があります**fflush**またはファイル ポジショニング関数。

以前の値のほかに、次の文字を追加できる*モード*改行文字の変換モードを指定します。

|*モード*修飾子|変換モード|
|-|-|
| **t** | ファイルをテキスト (変換) モードで開きます。 |
| **b** | ファイルをバイナリ (無変換) モードで開きます。キャリッジ リターンとライン フィードの変換は行われません。 |

テキスト モードでは、CTRL + Z は入力時に EOF 文字として解釈されます。 使用して読み取り/書き込みモードで開かれたファイルで **「a +」**、 **fopen**ファイルの末尾に CTRL + Z をチェックし、可能な場合は、削除します。 これを使用して、 [fseek](fseek-fseeki64.md)と**ftell** CTRL + Z で終わるを引き起こす可能性のあるファイル内で移動する[fseek](fseek-fseeki64.md)ファイルの末尾近く正しく動作します。

テキスト モードで復帰と改行の組み合わせは、入力、1 つの改行に変換し、改行文字は出力に復帰と改行の組み合わせに変換します。 Unicode のストリーム入出力関数が既定のテキスト モードで動作すると、入力元または出力先のストリームはマルチバイト文字のシーケンスと仮定されます。 このため、Unicode ストリーム入力関数はマルチバイト文字をワイド文字に変換し、 **mbtowc** 関数を呼び出した場合と同様の効果を得ます。 同様の理由で、Unicode ストリーム出力関数は、 **wctomb** 関数が呼び出されたかのように、ワイド文字をマルチバイト文字に変換します。

場合**t**または**b**には、指定しない*モード*、グローバル変数によって既定の変換モードが定義されている[_fmode](../../c-runtime-library/fmode.md)します。 場合**t**または**b**先頭に、引数、関数が失敗して返します**NULL**します。

テキスト モードとバイナリ モードの Unicode およびマルチバイト ストリーム i/o を使用する方法の詳細については、次を参照してください。[テキスト モードとバイナリ モードのファイル入出力](../../c-runtime-library/text-and-binary-mode-file-i-o.md)と[テキストとバイナリ モードの Unicode Stream I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)します。

次のオプションを追加できる*モード*追加の動作を指定します。

|*モード*修飾子|動作|
|-|-|
| **c** | 関連付けられているコミット フラグを有効にする*filename*ファイル バッファーの内容がいずれかのディスクに直接書き込まれるように**fflush**または **_flushall**が呼び出されます。 |
| **n** | 関連付けられているコミット フラグをリセット*filename* 「コミットなし」。 既定値です。 プログラムを COMMODE.OBJ とリンクする場合は、グローバル コミット フラグもオーバーライドします。 プログラムを明示的に COMMODE.OBJ とリンクしない場合、グローバル コミット フラグの既定の設定は "コミットなし" です (「 [Link Options](../../c-runtime-library/link-options.md)」をご覧ください)。 |
| **N** | ファイルが子プロセスによって継承されないように指定します。 |
| **S** | キャッシュがディスクからのシーケンシャル アクセスに最適化されるように指定します。ただし、シーケンシャル アクセスに限定されるわけではありません。 |
| **R** | キャッシュがディスクからのランダム アクセスに最適化されるように指定します。ただし、ランダム アクセスに限定されるわけではありません。 |
| **T** | ファイルを一時ファイルとして指定します。 可能な場合、ファイルはディスクにフラッシュされません。 |
| **D** | ファイルを一時ファイルとして指定します。 最後のファイル ポインターが閉じられると、ファイルは削除されます。 |
| **ccs =**_エンコード_ | 使用する設定でエンコードされた文字を指定します (いずれかの**utf-8**、 **UTF 16LE**、または**UNICODE**) このファイル。 何も指定しない場合は、ANSI エンコーディングが使用されます。 |

有効な文字は、*モード*で使用される文字列**fopen**と **_fdopen**に対応して*oflag* で使用される引数[_open](open-wopen.md)と[_sopen](sopen-wsopen.md)、次のようにします。

|文字*モード*文字列|等価*oflag*値\_開く/\_sopen|
|-------------------------------|----------------------------------------------------|
|**a**|**\_O\_WRONLY** &#124;  **\_O\_APPEND** (通常は **\_O\_WRONLY** &#124; **\_O\_CREAT** &#124;  **\_O\_APPEND**)|
|**+**|**\_O\_RDWR** &#124;  **\_O\_APPEND** (通常は **\_O\_RDWR** &#124;  **\_O\_APPEND** &#124;  **\_O\_CREAT** )|
|**r**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (通常は **\_O\_WRONLY** &#124;  **\_O\_CREAT** &#124; **\_O\_TRUNC**)|
|**w +**|**\_O\_RDWR** (通常は **\_O\_RDWR** &#124;  **\_O\_CREAT** &#124;  **\_O\_TRUNC**)|
|**b**|**\_O\_バイナリ**|
|**t**|**\_O\_TEXT**|
|**c**|なし|
|**n**|なし|
|**S**|**\_O\_シーケンシャル**|
|**R**|**\_O\_ランダム**|
|**T**|**\_O\_SHORTLIVED**|
|**D**|**\_O\_一時**|
|**ccs = UNICODE**|**\_O\_WTEXT**|
|**ccs utf-8 を =**|**\_O\_UTF8**|
|**ccs UTF 16LE を =**|**\_O\_UTF16**|

使用する場合**rb**モードで、コードを移植する必要がある、メモリを使用するオプションとしての Win32 ファイルをマップするかどうかを検討する大きなファイルのほとんどを読み取るするか、またはネットワークのパフォーマンスに心配がない場合も可能性があります。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> または \<wchar.h>|

**_wfopen**は Microsoft 拡張機能です。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

**C**、 **n**、 **t**、 **S**、 **R**、 **T**、および**D** *モード*オプション用の Microsoft 拡張機能は、 **fopen**と **_fdopen** ANSI 互換が必要な場合は使用する必要があります。

## <a name="example-1"></a>例 1

次のプログラムは 2 ファイルを開きます。  使用して**fclose**最初のファイルを閉じると **_fcloseall**を残りのすべてのファイルを閉じます。

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
