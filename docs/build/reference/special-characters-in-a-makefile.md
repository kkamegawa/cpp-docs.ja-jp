---
title: メイクファイルの特殊文字
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
ms.openlocfilehash: d915b182d72b4251f416433642cd8b1832b80e08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318577"
---
# <a name="special-characters-in-a-makefile"></a>メイクファイルの特殊文字

NMAKE の特殊文字をリテラル文字として使用するには、その前にキャレット (^) を配置します。 NMAKE では、その他の文字の前にキャレットを無視します。 特殊文字は次のとおりです。

`:  ;  #  (  )  $  ^  \  {  }  !  @  —`

引用符で囲まれた文字列内のキャレット (^) は、キャレットのリテラル文字として扱われます。 行の末尾のキャレットは、文字列またはマクロでリテラルの改行文字を挿入します。

マクロ、円記号 (\\) の後に改行文字がスペースで置き換えられます。

コマンドで、パーセント記号 (%)ファイル指定子です。 コマンドでは文字どおり % を表す、2 つのパーセント記号 (%) を指定します1 つ代わりにです。 その他の状況で (nmake の) 解釈単一の % をそのまま使いますが、常に double 型の値を解釈 %% として単一の % です。 そのため、リテラルを表す %%、3 つのパーセント記号をいずれかを指定 %%%c、または 4 つのパーセント記号、%%%c。

ドル記号 ($) をコマンドにリテラル文字として使用するには、2 つのドル記号 ($$) を指定します。 このメソッドは、他の状況でも使用できます、^ $ 動作します。

## <a name="see-also"></a>関連項目

[メイクファイルの内容](contents-of-a-makefile.md)
