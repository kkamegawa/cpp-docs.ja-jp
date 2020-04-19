---
title: /FD (IDE の簡易リビルド)
ms.date: 04/08/2019
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: ac63b021dc0cb9ee5964af7fa2e168f710653979
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292876"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (IDE の簡易リビルド)

**/FD**内のユーザーにのみ公開されますが、[コマンドライン](command-line-property-pages.md)のプロパティ ページ、C++プロジェクトの**プロパティ ページ** ダイアログ ボックス。 それが使用可能な場合、場合にのみ、非推奨と既定ではオフ[/Gm (簡易リビルドの有効)](gm-enable-minimal-rebuild.md)オプションが選択されていません。 **/FD**以外の開発環境からの影響を与えません。 **/FD**の出力で公開されていない`cl /?`します。

非推奨を有効にしない場合 **/Gm**オプションは、開発環境で **/FD**使用されます。 **/FD** .idb ファイルのある依存関係のための十分な情報を確認します。 **/FD**は、開発環境でのみ使用し、コマンド ライン ビルド スクリプトのために使用しないでください。

## <a name="see-also"></a>関連項目

[出力ファイル (/F) オプション](output-file-f-options.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
