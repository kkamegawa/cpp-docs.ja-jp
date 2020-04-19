---
title: /BIND
ms.date: 11/04/2016
f1_keywords:
- /bind
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
ms.openlocfilehash: e8ba0a5f0235c8771567e4e43172bdf8c81c99a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295033"
---
# <a name="bind"></a>/BIND

```
/BIND[:PATH=path]
```

## <a name="remarks"></a>Remarks

このオプションは、実行可能ファイルまたは DLL のインポート アドレス テーブル内のエントリ ポイントのアドレスを設定します。 このオプションを使用すると、プログラムの読み込み時間を短縮できます。

プログラムの実行可能ファイルと Dll の指定、*ファイル*EDITBIN コマンドラインの引数。 省略可能な*パス*/bind」と入力する引数を指定したファイルで使用される Dll の場所を指定します。 複数のディレクトリをセミコロンで区切ります (**;**)。 場合*パス*が指定されていない、EDITBIN が PATH 環境変数で指定されたディレクトリを検索します。 場合*パス*を指定すると、EDITBIN PATH 変数は無視されます。

既定では、プログラムのローダーは、プログラムの読み込み時にエントリ ポイントのアドレスを設定します。 このプロセスにかかる時間の量は、Dll の数と、プログラムで参照されているエントリ ポイントの数によって異なります。 /Bind」と入力でプログラムが変更された場合、および実行可能ファイルのベース アドレスし、その Dll が既に読み込まれている Dll と競合しない場合は、オペレーティング システムがこれらのアドレスを設定する必要はありません。 場所、ファイルが正しく基づいての状況では、オペレーティング システムは、プログラムの Dll を再配置し、プログラムの読み込み時に追加するエントリ ポイントのアドレスを再計算されます。

## <a name="see-also"></a>関連項目

[EDITBIN オプション](editbin-options.md)
