---
title: メイクファイルのコマンド
ms.date: 11/04/2016
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
ms.openlocfilehash: fcb8737070931cf95d7bfb3971a84e22c7ad70a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294396"
---
# <a name="commands-in-a-makefile"></a>メイクファイルのコマンド

説明のブロックまたは推論のルールでは、依存関係が古くなっている場合に実行するコマンドのブロックを指定します。 しない限り (nmake の) にそれを実行する前に各コマンドが表示されます、/S**します。サイレント**、 **!CMDSWITCHES**、または\@使用されます。 (Nmake の) は、記述ブロックの後にコマンドのブロックがない場合、照合の推論のルールを探します。

コマンドのブロックには、それぞれ独自の行に 1 つまたは複数のコマンドが含まれています。 依存関係またはルールとコマンドのブロックの間に空白行を表示できません。 ただし、スペースまたはタブのみが含まれる行も表示されます。この行は、null コマンドとして解釈され、エラーは発生しません。 コマンド行の間の空白行が許可されます。

コマンド ラインは、1 つまたは複数のスペースやタブから始まります。 改行文字の後に円記号 (\) は、コマンド内の領域として解釈されます。行の最後に円記号を使用して、次の行にコマンドを続行します。 解釈される円記号を文字どおり (nmake の) スペースまたはタブを含むその他の文字が円記号の後ろにある場合。

コマンドの先頭にセミコロン (;) は、コマンドのブロックに依存しているかどうかを示す依存関係の行または推論規則に表示されます。

```
project.obj : project.c project.h ; cl /c project.c
```

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

[コマンド修飾子](command-modifiers.md)

[ファイル名分割構文](filename-parts-syntax.md)

[メイクファイルのインライン ファイル](inline-files-in-a-makefile.md)

## <a name="see-also"></a>関連項目

[NMAKE リファレンス](nmake-reference.md)
