---
title: ストリーム入出力
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- I/O routines, stream I/O
- I/O [CRT], stream
- stream I/O
ms.assetid: dc7874d3-a91b-456a-9015-4748bb358217
ms.openlocfilehash: 8bf81d1969fcbcfd255f3d4f9878bd3aab421703
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746254"
---
# <a name="stream-io"></a>ストリーム入出力

これらの関数は、1 文字から大きなデータ構造に至るまで、さまざまなサイズと形式のデータを処理します。 バッファリングも提供しており、パフォーマンスを向上させることができます。 ストリーム バッファーの既定のサイズは 4K です。 これらのルーチンは、ランタイム ライブラリ ルーチンによって作成されるバッファーにのみ影響し、オペレーティング システムによって作成されるバッファーには影響しません。

## <a name="stream-io-routines"></a>ストリーム入出力ルーチン

|ルーチンによって返される値|使用|
|-------------|---------|
|[clearerr](../c-runtime-library/reference/clearerr.md)、 [clearerr_s](../c-runtime-library/reference/clearerr-s.md)|ストリームのクリア エラー インジケーター|
|[fclose](../c-runtime-library/reference/fclose-fcloseall.md)|ストリームを閉じる|
|[_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)|**stdin**、**stdout**、**stderr** を除く、開いているすべてのストリームを閉じる|
|[_fdopen、wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|開いているファイルのファイル記述子にストリームを関連付ける|
|[feof](../c-runtime-library/reference/feof.md)|ストリームのファイルの終わりをテストする|
|[ferror](../c-runtime-library/reference/ferror.md)|ストリームのエラーをテストする|
|[fflush](../c-runtime-library/reference/fflush.md)|ストリームをバッファーまたはストレージ デバイスにフラッシュする|
|[fgetc、fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|ストリームから文字を読み取る (**getc** および **getwc** の関数バージョン)|
|[_fgetchar、_fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|**stdin** から文字を読み取る (**getchar** および **getwchar** の関数バージョン)|
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|ストリームの位置インジケーターを取得する|
|[fgets、fgetws](../c-runtime-library/reference/fgets-fgetws.md)|文字列をストリームから読み取る|
|[_fileno](../c-runtime-library/reference/fileno.md)|ストリームに関連付けられているファイル記述子を取得する|
|[_flushall](../c-runtime-library/reference/flushall.md)|すべてのストリームをバッファーまたはストレージ デバイスにフラッシュする|
|[fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md)、 [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|ストリームを開く|
|[fprintf、_fprintf_l、fwprintf、_fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)、[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|ストリームに書式付きデータを書き込む|
|[fputc、fputwc](../c-runtime-library/reference/fputc-fputwc.md)|ストリームに文字を書き込む (**putc** および **putwc** の関数バージョン)|
|[_fputchar、_fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|**stdout** に文字を書き込む (**putchar** および **putwchar** の関数バージョン)|
|[fputs、fputws](../c-runtime-library/reference/fputs-fputws.md)|文字列をストリームに書き込む|
|[fread](../c-runtime-library/reference/fread.md)|書式設定されていないデータをストリームから読み取る|
|[freopen、_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)、 [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|**FILE** ストリーム ポインターを新しいファイルまたはデバイスに再割り当てする|
|[fscanf、fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)、[fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|書式付きデータをストリームから読み取る|
|[fseek、_fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|ファイルの位置を指定の場所に移動する|
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|ストリームの位置インジケーターを設定する|
|[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|ファイル共有付きでストリームを開く|
|[ftell、_ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|現在のファイルの位置を取得する|
|[fwrite](../c-runtime-library/reference/fwrite.md)|書式設定されていないデータの項目をストリームに書き込む|
|[getc、getwc](../c-runtime-library/reference/getc-getwc.md)|ストリームから文字を読み取る (**fgetc** および **fgetwc** のマクロ バージョン)|
|[getchar、getwchar](../c-runtime-library/reference/getc-getwc.md)|**stdin** から文字を読み取る (**fgetchar** および **fgetwchar** のマクロ バージョン)|
|[_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|ストリーム入出力のレベルで許可されている、同時に開かれたファイルの数を返します。|
|[gets_s、_getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|**stdin** から行を読み取る|
|[_getw](../c-runtime-library/reference/getw.md)|ストリームからバイナリ **int** を読み取る|
|[printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)、[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|**stdout** に書式付きデータを書き込む|
|[putc、putwc](../c-runtime-library/reference/putc-putwc.md)|ストリームに文字を書き込む (**fputc** および **fputwc** のマクロ バージョン)|
|[putchar、putwchar](../c-runtime-library/reference/putc-putwc.md)|**stdout** に文字を書き込む (**fputchar** および **fputwchar** のマクロ バージョン)|
|[puts、_putws](../c-runtime-library/reference/puts-putws.md)|ストリームに行を書き込む|
|[_putw](../c-runtime-library/reference/putw.md)|ストリームにバイナリ **int** を書き込む|
|[rewind](../c-runtime-library/reference/rewind.md)|ファイルの位置をストリームの先頭に移動する|
|[_rmtmp](../c-runtime-library/reference/rmtmp.md)|**tmpfile** によって作成された一時ファイルを削除する|
|[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)、[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|**stdin** から書式付きデータを読み取る|
|[setbuf](../c-runtime-library/reference/setbuf.md)|ストリーム バッファリングを制御する|
|[_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|ストリーム入出力のレベルで同時に開かれるファイルの数の最大値を設定する。|
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|ストリーム バッファリングとバッファー サイズを制御する|
|[_snprintf、_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)、 [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|指定された長さの書式付きデータを文字列に書き込む|
|[_snscanf、_snwscanf](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md)、[_snscanf_s、_snscanf_s_l、_snwscanf_s、_snwscanf_s_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|指定した長さの書式付きデータを標準入力ストリームから読み取ります。|
|[sprintf、swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)、[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|文字列に書式付きデータを書き込む|
|[sscanf、swscanf](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)、[sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|文字列から書式付きデータを読み取る|
|[_tempnam、_wtempnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|指定されたディレクトリに一時ファイル名を生成する|
|[tmpfile](../c-runtime-library/reference/tmpfile.md)、 [tmpfile_s](../c-runtime-library/reference/tmpfile-s.md)|一時ファイルを作成する|
|[tmpnam、_wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)、 [tmpnam_s, _wtmpnam_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|一時ファイル名を生成する|
|[ungetc、ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|文字をストリームにプッシュし直す|
|[_vcprintf、_vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)、[_vcprintf_s、_vcprintf_s_l、_vcwprintf_s、_vcwprintf_s_l](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|コンソールに書式付きデータを書き込む。|
|[vfprintf、vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)、[vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|ストリームに書式付きデータを書き込む|
|[vprintf、vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)、[vprintf_s、_vprintf_s_l、vwprintf_s、_vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|**stdout** に書式付きデータを書き込む|
|[_vsnprintf、_vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)、[vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|指定された長さの書式付きデータをバッファーに書き込む|
|[vsprintf、vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)、[vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|バッファーに書式付きデータを書き込む|

プログラムの実行を開始すると、スタートアップ コードは自動的に複数のストリームを開きます。すなわち、標準入力 (**stdin** が指す)、標準出力 (**stdout** が指す)、および標準エラー (**stderr** が指す) です。 これらのストリームは既定でコンソール (キーボードと画面) に送られます。 ディスク ファイルまたはデバイスに **stdin**、**stdout**、または **stderr** をリダイレクトするには **freopen** を使用します。

ストリーム ルーチンを使用して開くファイルは、既定でバッファリングされます。 いっぱいになった場合、またはキャラクター デバイスに書き込みを行う場合、各ライブラリ呼び出しの後に **stdout** および **stderr** の関数はフラッシュされます。 プログラムが異常に終了した場合、出力バッファーがフラッシュされず、データが失われる可能性があります。 **fflush** または **_flushall** を使用して、特定のファイルに関連付けられているバッファー、または開いているすべてのバッファーが必ずオペレーティング システムにフラッシュされるようにします。データをディスクに書き込む前に、オペレーティング システムはデータをキャッシュすることができます。 ディスクへのコミットの機能により、フラッシュされるバッファーの内容がシステム障害時に失われないようにすることができます。

バッファーの内容をディスクにコミットする 2 つの方法があります。

- ファイル COMMODE.OBJ とリンクして、グローバル コミット フラグを設定します。 グローバル フラグの既定の設定は、**n** ("コミットなし") です。

- モード フラグを **fopen** または **_fdopen** で **c** に設定します。

**c** または **n** フラグで開かれるファイルは、グローバル コミット/コミットなしのフラグの状態にかかわらず、フラグに従って動作します。

プログラムが明示的にストリームを閉じない場合、ストリームはプログラムが終了するときに自動的に閉じます。 ただし、一度に開くことのできるストリームの数は限られているため、プログラムがストリームの作業を終了したら、そのストリームを閉じる必要があります。 この制限については、 [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) を参照してください。

出力の直後に入力を行うには、**fflush** またはファイル ポジショニング関数 (**fseek** **fsetpos**、または **rewind**) の呼び出しを間に挟まなければなりません。 入力操作がファイルの末尾に達した場合、ファイル ポジショニング関数の呼び出しを間に挟まなくても、入力の直後に出力を行うことができます。

## <a name="see-also"></a>関連項目

[入出力](../c-runtime-library/input-and-output.md)<br/>
[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
