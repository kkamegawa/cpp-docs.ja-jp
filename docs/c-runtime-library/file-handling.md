---
title: ファイル処理
ms.date: 11/04/2016
f1_keywords:
- c.files
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
ms.openlocfilehash: 2a5c6ec3a70a85bf81f00b104d0c505677f609ac
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740054"
---
# <a name="file-handling"></a>ファイル処理

ファイル処理ルーチンは、ファイルの作成、削除、操作、およびファイル アクセス許可の設定、チェックに使用します。

C ランタイム ライブラリには、同時に開くことのできるファイル数の上限が 512 に設定されています。 上限を超える数のファイル記述子またはファイル ストリームを開こうとすると、プログラム エラーが発生します。 上限のファイル数を変更するには、 [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) を使用します。

## <a name="file-handling-routines-file-descriptor"></a>ファイル処理ルーチン (ファイル記述子)

ファイル記述子で指定されたファイルを操作するには、次のルーチンを使います。

|ルーチンによって返される値|上限のファイル数を変更するには、|
|-------------|---------|
|[_chsize](../c-runtime-library/reference/chsize.md)、[_chsize_s](../c-runtime-library/reference/chsize-s.md)|ファイル サイズを変更します。|
|[_filelength、_filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|ファイル長を取得します。|
|[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|記述子のファイル ステータス情報を取得します。|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|C ランタイムの既存のファイル記述子に関連付けられたオペレーティング システムのファイル ハンドルを返します。|
|[_isatty](../c-runtime-library/reference/isatty.md)|キャラクター デバイスをチェックします。|
|[_locking](../c-runtime-library/reference/locking.md)|ファイル領域をロックします。|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|C ランタイムのファイル記述子を既存のオペレーティング システムのファイル ハンドルに関連付けます。|
|[_setmode](../c-runtime-library/reference/setmode.md)|ファイルの変換モードを設定します。|

## <a name="file-handling-routines-path-or-filename"></a>ファイル処理ルーチン (パスまたはファイル名)

パスまたはファイル名で指定されたファイルを操作するには、次のルーチンを使います。

|ルーチンによって返される値|使用|
|-------------|---------|
|[_access, _waccess](../c-runtime-library/reference/access-waccess.md), [_access_s, _waccess_s](../c-runtime-library/reference/access-s-waccess-s.md)|ファイルのアクセス許可の設定をチェックします。|
|[_chmod、_wchmod](../c-runtime-library/reference/chmod-wchmod.md)|ファイルのアクセス許可の設定を変更します。|
|[_fullpath、_wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|相対パス名を絶対パス名に展開します。|
|[_makepath, _wmakepath](../c-runtime-library/reference/makepath-wmakepath.md), [_makepath_s, _wmakepath_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|パス コンポーネントを単一の完全パスにマージします。|
|[_mktemp、_wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md)、 [_mktemp_s, _wmktemp_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|一意のファイル名を作成します。|
|[remove、_wremove](../c-runtime-library/reference/remove-wremove.md)|ファイルの削除|
|[rename、_wrename](../c-runtime-library/reference/rename-wrename.md)|ファイル名の変更|
|[_splitpath、_wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md)、 [_splitpath_s, _wsplitpath_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|コンポーネントのパスを解析します。|
|[_stat、_stat64、_stati64、_wstat、_wstat64、_wstati64](../c-runtime-library/reference/stat-functions.md)|名前付きファイルのファイル ステータス情報を取得します。|
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|プログラムが新しく作成したファイルに、既定のアクセス許可マスクを設定します。|
|[_unlink、_wunlink](../c-runtime-library/reference/unlink-wunlink.md)|ファイルの削除|

## <a name="file-handling-routines-open-file"></a>ファイル処理ルーチン (開いているファイル)

これらのルーチンは、ファイルを開きます。

|ルーチンによって返される値|使用|
|-------------|---------|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|ファイルを開き、開いているファイルへのポインターを返します。|
|[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|ファイル共有でストリームを開き、開いているファイルへのポインターを返します。|
|[_open、_wopen](../c-runtime-library/reference/open-wopen.md)|ファイルを開き、開いているファイルへのファイル記述子を返します。|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|ファイル共有でファイルを開き、開いているファイルへのファイル記述子を返します。|
|[_pipe](../c-runtime-library/reference/pipe.md)|読み取りおよび書き込み用のパイプを作成します。|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|ファイル ポインターを再度割り当てます。|

次のルーチンを使うと、`FILE` 構造体、ファイル記述子、および Win32 ファイル ハンドル間でファイルの表示を変更できます。

|ルーチンによって返される値|使用|
|-------------|---------|
|[_fdopen、wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|ストリームを前回下位入出力で開いたファイルに関連付け、オープン ストリームへのポインターを返します。|
|[_fileno](../c-runtime-library/reference/fileno.md)|ストリームに関連付けられているファイル記述子を取得します。|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|C ランタイムの既存のファイル記述子に関連付けられたオペレーティング システムのファイル ハンドルを返します。|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|C ランタイム ファイル記述子を既存のオペレーティング システムのファイル ハンドルに関連付けます。|

ファイルおよびパイプは、次の Win32 関数でも開くことができます。

- [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)

- [CreatePipe](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe)

- [CreateNamedPipe](/windows/win32/api/winbase/nf-winbase-createnamedpipea)

## <a name="see-also"></a>関連項目

[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
[ディレクトリ制御](../c-runtime-library/directory-control.md)<br/>
[システム コール](../c-runtime-library/system-calls.md)<br/>
