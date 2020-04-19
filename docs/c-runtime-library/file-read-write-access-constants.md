---
title: ファイル読み出し/書き込みアクセス定数
ms.date: 11/04/2016
f1_keywords:
- c.constants.file
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
ms.openlocfilehash: 0dfbc925c5252724cbb1caad58470849915242a9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746072"
---
# <a name="file-readwrite-access-constants"></a>ファイル読み出し/書き込みアクセス定数

## <a name="syntax"></a>構文

```
#include <stdio.h>
```

## <a name="remarks"></a>解説

これらの定数は、ファイルに対して要求されるアクセスの種類 ("a"、"r"、または "w") を指定します。 [変換モード](../c-runtime-library/file-translation-constants.md) ("b" または "t") と[ディスク コミット モード](../c-runtime-library/commit-to-disk-constants.md) ("c" または "n") をアクセスの種類で指定できます。

アクセスの種類を次のテーブルに示します。

|アクセスの種類|説明|
|----------|----------------|
|**"r"**|読み取り用に開きます。 ファイルが存在しない場合や見つからない場合、ファイルを開く呼び出しは失敗します。|
|**"w"**|書き込み用に空のファイルを開きます。 指定したファイルが既に存在すると、そのファイルの内容は破棄されます。|
|**"a"**|ファイルの末尾への書き込み用にファイルを開きます (追加モード)。ファイルが存在しない場合は、まず、ファイルを作成します。 すべての書き込み操作はファイルの終端で行われます。 `fseek` または `rewind` を使用することでファイル ポインターの位置を変更できますが、書き込み操作の実行前には必ずファイルの終端に戻されます。 |
|**"r+"**|読み取りと書き込みの両方のモードで開きます。 ファイルが存在しない場合や見つからない場合、ファイルを開く呼び出しは失敗します。|
|**"w+"**|読み取りと書き込みの両方のモードで空のファイルを開きます。 指定したファイルが既に存在すると、そのファイルの内容は破棄されます。|
|**"a+"**|**"a"** と同様ですが、読み取りも許可されます。|

"r+"、"w+"、または "a+" のいずれかを指定すると、読み取りと書き込みの両方を行うことができます (この場合、ファイルは"更新"用に開かれると言います)。 ただし、読み取りと書き込みを切り替える場合は、その前に `fflush`、`fsetpos`、`fseek`、または `rewind` のいずれかの操作を実行する必要があります。 `fsetpos` または `fseek` の操作には現在位置を指定できます。

## <a name="see-also"></a>関連項目

[_fdopen、_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen、_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[_popen、_wpopen](../c-runtime-library/reference/popen-wpopen.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
