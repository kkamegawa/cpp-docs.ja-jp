---
title: LINK の入力ファイル
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
ms.openlocfilehash: 48ad9423ae35c22a97a873fe6a2a0479c12ab33b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291510"
---
# <a name="link-input-files"></a>LINK の入力ファイル

リンカーは、オブジェクト、インポートと標準ライブラリ、リソース、モジュールの定義、およびコマンドの入力が含まれているファイルに指定します。 リンクは、ファイルの内容に関する判断を行うファイルの拡張機能を使用しません。 代わりに、リンクは、各入力ファイルがファイルの種類を判断するを調べます。

コマンドラインでのオブジェクト ファイルは、コマンドラインで表示される順序で処理されます。 ライブラリは、次の注意点がありますも、コマンドラインの順序で検索されます。シンボルは未解決のときライブラリからのオブジェクト ファイルで検索のライブラリで最初に、され、コマンドラインから次のライブラリと[/DEFAULTLIB (既定のライブラリの指定)](defaultlib-specify-default-library.md)ディレクティブ、し、コマンドラインの先頭のすべてのライブラリを

> [!NOTE]
>  リンクでは、応答ファイルおよびファイルの順序でのコメントの始まりとしてセミコロン (またはその他の任意の文字) を不要になった受け取ります。 セミコロンは、モジュール定義ファイル (.def) 内のコメントの始まりとしてのみ認識されます。

リンクは、次の種類の入力ファイルを使用します。

- [.obj ファイル](dot-obj-files-as-linker-input.md)

- [.netmodule ファイル](netmodule-files-as-linker-input.md)

- [.lib ファイル](dot-lib-files-as-linker-input.md)

- [.exp ファイル](dot-exp-files-as-linker-input.md)

- [.def ファイル](dot-def-files-as-linker-input.md)

- [.pdb ファイル](dot-pdb-files-as-linker-input.md)

- [.res ファイル](dot-res-files-as-linker-input.md)

- [.exe ファイル](dot-exe-files-as-linker-input.md)

- [.txt ファイル](dot-txt-files-as-linker-input.md)

- [.ilk ファイル](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
