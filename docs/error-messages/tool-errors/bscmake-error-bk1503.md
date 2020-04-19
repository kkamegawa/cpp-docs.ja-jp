---
title: BSCMAKE エラー BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: c81e955b912e03b322c0429097410fae74713b9d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280140"
---
# <a name="bscmake-error-bk1503"></a>BSCMAKE エラー BK1503

'filename' をファイルに書き込みできません [: 理由]

BSCMAKE では、ブラウザーの 1 つのデータベースへのコンパイル中に生成された .sbr ファイルを結合します。 結果として得られるブラウザー データベースが 64 MB を超える場合、または入力 (.sbr) ファイルの数が 4092 を超えた場合は、このエラーが出力されます。

問題の原因が 4092 以上の .sbr ファイルである場合は、入力ファイルの数を減らす必要があります。 Visual Studio で、これは実現できますで[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)し、プロジェクト全体、ファイルをファイルごとに再確認します。

問題の原因が、64 MB を超える .bsc ファイルである場合は、入力としての .sbr ファイルの数を減らすと生成された .bsc ファイルのサイズを小さくは。 さらに、/Em (マクロ展開シンボルを除外する)、/El (除外するローカル変数)、および/Es (システム ファイルを除外する) を使用してブラウザー情報の量を削減することがあります。

## <a name="see-also"></a>関連項目

[BSCMAKE オプション](../../build/reference/bscmake-options.md)