---
title: かっこ付きのファイル名を含む
ms.date: 11/04/2016
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
ms.openlocfilehash: 87de00814f58ed86ee33abdcf96dd210f418c5ba
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147582"
---
# <a name="including-bracketed-filenames"></a>かっこ付きのファイル名を含む

**ANSI 3.8.2** インクルード可能なソース ファイルを見つけるための手段

山かっこで囲まれたファイル指定の場合、プリプロセッサは親ファイルのディレクトリを検索しません。 "親" ファイルとは、[#include](../preprocessor/hash-include-directive-c-cpp.md) ディレクティブがあるファイルです。 代わりに、コンパイラ コマンド ラインで /I の後に指定したディレクトリからファイル検索を開始します。 /I オプションがない場合または失敗した場合、プリプロセッサは INCLUDE 環境変数を使用して、山かっこで囲まれたインクルード ファイルを検索します。 INCLUDE 環境変数には、セミコロン (**;**) で区切られた複数のパスを含めることができます。 複数のディレクトリが /I オプションの一部として、または INCLUDE 環境変数内にある場合、プリプロセッサではそれらのディレクトリを表示されている順序で検索します。

## <a name="see-also"></a>関連項目

[プリプロセス ディレクティブ](../c-language/preprocessing-directives.md)
