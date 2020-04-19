---
title: BSCMAKE コマンド ファイル (応答ファイル)
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
ms.openlocfilehash: 6a55fd616a00aeb3ade229bf7cff8220f86085b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295046"
---
# <a name="bscmake-command-file-response-file"></a>BSCMAKE コマンド ファイル (応答ファイル)

> [!WARNING]
> BSCMAKE は、現在も Visual Studio と共にインストールされていますが、IDE では使用されなくなりました。 Visual Studio 2008 以降、ブラウザーとシンボルの情報は、ソリューション フォルダー内の SQL Server の .sdf ファイルに自動的に格納されます。

コマンド ファイルでは、コマンドラインの入力の一部またはすべてを行うことができます。 次の構文を使用してコマンド ファイルを指定します。

```
BSCMAKE @filename
```

1 つのコマンド ファイルが許可されます。 パスを指定する*filename*します。 前に*filename*で、アット マーク (**\@**)。 BSCMAKE では、拡張機能は想定しません。 追加を指定できます*sbrfiles*後のコマンド ラインで*filename*します。 コマンド ファイルは、コマンドラインで指定する場合と同じ順序では、BSCMAKE への入力を含むテキスト ファイルです。 コマンドライン引数を 1 つまたは複数のスペース、タブ、または改行文字で区切ります。

次のコマンドは、BSCMAKE コマンド ファイルを使用して呼び出します。

```
BSCMAKE @prog1.txt
```

コマンド ファイルのサンプルを次に示します。

```
/n /v /o main.bsc /El
/S (
toolbox.h
verdate.h c:\src\inc\screen.h
)
file1.sbr file2.sbr file3.sbr file4.sbr
```

## <a name="see-also"></a>関連項目

[BSCMAKE リファレンス](bscmake-reference.md)
