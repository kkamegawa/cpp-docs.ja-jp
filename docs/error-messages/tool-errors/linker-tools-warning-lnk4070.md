---
title: リンカー ツールの警告 LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: e7139b21f053ea8633356c7194cd719a6a4aef35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410266"
---
# <a name="linker-tools-warning-lnk4070"></a>リンカー ツールの警告 LNK4070

/OUT:filename ディレクティブ。Exp 関数は、出力ファイル名 'filename'; によって異なります。ディレクティブは無視されます。

`filename`で指定されている、[名前](../../build/reference/name-c-cpp.md)または[ライブラリ](../../build/reference/library.md).exp ファイルが作成されたときにステートメントと、出力は異なります`filename`が既定で使用されますか、で指定されました。[/Out](../../build/reference/out-output-file-name.md)オプション。

開発環境で、プロジェクトの .def ファイルが更新されたしない出力ファイルの名前を変更する場合、この警告が表示されます。 この警告を解決するのには、.def ファイルを手動で更新します。

結果の DLL を使用するクライアント プログラムには、問題が発生します。