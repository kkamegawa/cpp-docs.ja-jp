---
title: 下位入出力
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- I/O [CRT], low-level
- I/O [CRT], functions
- low-level I/O routines
- file handles [C++]
- file handles [C++], I/O functions
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
ms.openlocfilehash: 7812656bdcb3f58866f91009b6ad3de9fd67cebe
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740143"
---
# <a name="low-level-io"></a>下位入出力

これらの関数は、ストリーム入出力の操作より低レベルの操作に対してオペレーティング システムを直接呼び出します。 低レベル入出力の呼び出しでは、データはバッファリングまたは書式設定されません。

低レベル ルーチンでは、次の事前定義済みのファイル記述子を使用して、プログラムの起動時に開かれる標準ストリームにアクセスできます。

|ストリーム|ファイル記述子|
|------------|---------------------|
|**stdin**|0|
|**stdout**|1|
|**stderr**|2|

低レベル入出力ルーチンでは、エラー発生時に [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) グローバル変数が設定されます。 ファイルの終端を示すインジケーター (**EOF**) などの STDIO.H で定義された定数が、お使いのプログラムで必要な場合に限り、低レベル関数を使用する際に STDIO.H をインクルードする必要があります。

## <a name="low-level-io-functions"></a>低レベル入出力関数

|関数|使用|
|--------------|---------|
|[_close](../c-runtime-library/reference/close.md)|ファイルを閉じる|
|[_commit](../c-runtime-library/reference/commit.md)|ファイルをディスクにフラッシュする|
|[_creat、_wcreat](../c-runtime-library/reference/creat-wcreat.md)|ファイルを作成する|
|[_dup](../c-runtime-library/reference/dup-dup2.md)|指定されたファイルに対して次に使用できるファイル記述子を返す|
|[_dup2](../c-runtime-library/reference/dup-dup2.md)|指定されたファイルに対して 2 つ目の記述子を作成する|
|[_eof](../c-runtime-library/reference/eof.md)|ファイルの終端をテストする|
|[_lseek、_lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|ファイル ポインターの位置を指定された場所に変更する|
|[_open、_wopen](../c-runtime-library/reference/open-wopen.md)|ファイルを開く|
|[_read](../c-runtime-library/reference/read.md)|ファイルからデータを読み取る|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|ファイル共有のためにファイルを開く|
|[_tell、_telli64](../c-runtime-library/reference/tell-telli64.md)|現在のファイル ポインターの位置を取得する|
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|ファイル アクセス許可マスクを設定する|
|[_write](../c-runtime-library/reference/write.md)|ファイルにデータを書き込む|

**_dup** と **_dup2** は通常、事前定義済みのファイル記述子を別のファイルと関連付けるために使用します。

## <a name="see-also"></a>関連項目

[入出力](../c-runtime-library/input-and-output.md)<br/>
[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
[システム コール](../c-runtime-library/system-calls.md)<br/>
