---
title: メイクファイル プリプロセスの式
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
ms.openlocfilehash: 3d668492441eb2fc09be378dbebfe2b18c1b5753
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271308"
---
# <a name="expressions-in-makefile-preprocessing"></a>メイクファイル プリプロセスの式

**!IF**または **!ELSE IF** `constantexpression` (10 進数または C 言語表記) に整数の定数、文字列定数、またはコマンドで構成されます。 グループ式にかっこを使用します。 式を使用して、C スタイル符号付き長整数演算です。番号は 32 ビット 2 の補数形式、範囲 - 2147483648 ~ 2147483647 です。

式は、定数値、コマンド、文字列、マクロ、およびファイル システム パスからの終了コードで機能する演算子を使用できます。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

[メイクファイルのプリプロセッサ演算子](makefile-preprocessing-operators.md)

[プリプロセスでのプログラムの実行](executing-a-program-in-preprocessing.md)

## <a name="see-also"></a>関連項目

[メイクファイルのプリプロセス](makefile-preprocessing.md)
