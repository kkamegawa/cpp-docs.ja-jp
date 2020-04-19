---
title: リンカ ツール エラー LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: 657e78ece2ce4039eb8dc8561abd455c60aaff75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62254921"
---
# <a name="linker-tools-error-lnk1181"></a>リンカ ツール エラー LNK1181

入力ファイル 'filename' を開くことができません。

リンカーが見つかりませんでした。`filename`が存在しないか、パスが見つかりませんでした。

よくある原因のエラー LNK1181 が含まれます。

- `filename` リンカーのコマンドラインは、ファイルの追加の依存関係が存在しないために参照されます。

- A **/LIBPATH**格納されているディレクトリを指定するステートメント`filename`がありません。

上記の問題を解決するには、リンカーのコマンドラインで参照されているすべてのファイルは、システムに存在を確認します。  あることを確認、 **/LIBPATH**リンカーの依存ファイルを含む各ディレクトリに対してステートメントです。

詳細については、次を参照してください。[リンカー入力としての .lib ファイル](../../build/reference/dot-lib-files-as-linker-input.md)します。

LNK1181 のもう 1 つの考えられる原因は、長いファイル名に埋め込まれたスペースが引用符で囲まれていないことです。  その場合は、リンカーだけ最初のスペースでは、最大のファイル名が認識され、ファイル拡張子を想定します .obj。このような状況を解決するには長いファイル名を囲む (パスとファイル名) 引用符で囲んで指定します。

コンパイルすると、 [/P (ファイルへのプリプロセス)](../../build/reference/p-preprocess-to-a-file.md)オプションにより、LNK1181 のため、そのオプションの .obj ファイルの作成を抑制します。

## <a name="see-also"></a>関連項目

[/LIBPATH (追加ライブラリのパス)](../../build/reference/libpath-additional-libpath.md)