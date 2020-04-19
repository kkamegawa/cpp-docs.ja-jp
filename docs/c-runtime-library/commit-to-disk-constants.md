---
title: ディスク コミット定数
ms.date: 11/04/2016
f1_keywords:
- vc.constants
helpviewer_keywords:
- commit-to-disk constants
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
ms.openlocfilehash: c02b18e5a4a731957a7c74cc45e6e181fe23fad8
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750612"
---
# <a name="commit-to-disk-constants"></a>ディスク コミット定数

**Microsoft 固有の仕様**

## <a name="syntax"></a>構文

```
#include <stdio.h>
```

## <a name="remarks"></a>解説

これらの Microsoft 固有の定数は、開いているファイルに関連付けられているバッファーが、オペレーティング システムのバッファーまたはディスクにフラッシュされるかどうかを指定します。 このモードは、読み取り/書き込みのアクセス権の種類 (**"r"**、**"w"**、**"a"**、**"r+"**、**"w+"**、**"a+"**) を指定する文字列に含まれます。

ディスク コミット モードは次のとおりです。

- **c**

   指定したバッファーの書き込まれていない内容をディスクに書き込みます。 このディスク コミット機能は、[fflush](../c-runtime-library/reference/fflush.md) または [_flushall](../c-runtime-library/reference/flushall.md) 関数のいずれかを明示的に呼び出す場合にのみ発生します。 このモードは、機密データを処理する場合に便利です。 たとえば、プログラムが `fflush` または `_flushall` を呼び出した後に終了する場合、データがオペレーティング システムのバッファーに達したと考えて間違いありません。 ただし、ファイルを **c** オプションで開く場合を除き、オペレーティング システムも終了する場合は、データがディスクに書き込まれることはほぼありません。

- **n**

   指定したバッファーの書き込まれていない内容をオペレーティング システムのバッファーに書き込みます。 オペレーティング システムはデータをキャッシュし、ディスクに書き込むための最適な時間を決定します。 多くの状況で、この動作は効率的なプログラムの動作になります。 ただし、データの保有期間が重要な場合 (銀行取引や航空券の情報など) は、**c**オプションを使用することを検討してください。 既定では **n** モードです。

> [!NOTE]
> **c** および **n** オプションは、`fopen` の ANSI 標準には含まれませんが、Microsoft 拡張機能です。ANSI 互換が必要な場合は使用しないでください。

## <a name="using-the-commit-to-disk-feature-with-existing-code"></a>既存のコードと共にディスク コミット機能を使用する

既定では、[fflush](../c-runtime-library/reference/fflush.md) または [_flushall](../c-runtime-library/reference/flushall.md) ライブラリ関数への呼び出しは、オペレーティング システムによって保持されるバッファーにデータを書き込みます。 オペレーティング システムでは、ディスクにデータを実際に書き込むための最適な時間を決定します。 ランタイム ライブラリのディスク コミット機能を使用すると、重要なデータをオペレーティング システムのバッファーではなく、ディスクに直接書き込むことができます。 既存のプログラムのオブジェクト ファイルと COMMODE.OBJ をリンクさせて書き直すことなく、既存のプログラムにこの機能を提供することができます。

生成される実行ファイルでは、`fflush` への呼び出しはバッファーの内容をディスクに直接書き込み、`_flushall` への呼び出しはすべてのバッファーの内容をディスクに書き込みます。 これら 2 つの関数のみが、COMMODE.OBJ の影響を受けます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[ストリーム入出力](../c-runtime-library/stream-i-o.md)<br/>
[_fdopen、_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
