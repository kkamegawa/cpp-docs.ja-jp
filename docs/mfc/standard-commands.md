---
title: 標準コマンド
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- identifiers [MFC], command IDs
- command IDs, standard commands
- OLE commands
- commands [MFC], standard
- standard command IDs
- Window menu commands
- standard commands
- View menu commands
- Edit menu standard commands
- Help [MFC], menus
- programmer-defined IDs [MFC]
ms.assetid: 88cf3ab4-79b3-4ac6-9365-8ac561036fbf
ms.openlocfilehash: 987023322e38584d10901c1ab1fe20ac46926bd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307160"
---
# <a name="standard-commands"></a>標準コマンド

フレームワークは、多くの標準コマンド メッセージを定義します。 これらのコマンドの Id は、通常、形式をとります。

**Id _** *ソース*_*項目*

場所*ソース*メニュー名では、通常と*項目*のメニュー項目。 たとえば、[ファイル] メニューの新しいコマンドのコマンド ID では、ID_FILE_NEW です。 標準コマンド Id は、ドキュメントで太字で表示されます。 プログラマで定義された Id は、周囲のテキストとは異なるフォントで表示されます。

次はサポートされている最も重要なコマンドの一部の一覧です。

*ファイル メニュー コマンド*<br/>
新しいを開いて、閉じるには、保存、名前を付けて保存、ページ設定、印刷のセットアップ、印刷、印刷プレビュー、終了時に、最近使ったファイル。

*メニュー コマンドを編集します。*<br/>
クリア、消去すべてであるため、コピー、切り取り、検索、貼り付け、繰り返すには、元に戻したり、置換、すべて選択、および再実行します。

*[表示] メニューのコマンド*<br/>
ツールバーとステータス バー。

*[ウィンドウ] メニューのコマンド*<br/>
配置では、新しい、連鎖的に、水平に並べて表示、垂直、タイルおよび分割します。

*[ヘルプ] メニューのコマンド*<br/>
インデックス作成、ヘルプを使用しようとします。

*OLE コマンド ([編集] メニュー)*<br/>
新しいオブジェクト、リンクの編集、リンク、貼り付け、挿入と*typename*オブジェクト (動詞コマンド)。

フレームワークは、これらのコマンドのさまざまなレベルのサポートを提供します。 いくつかのコマンドは定義されているコマンドの Id としてのみサポートされている他のユーザーは完全に実装でサポートされています。 たとえば、フレームワークは、新しい document オブジェクトを作成を開く ダイアログ ボックスを表示する、開くと、ファイルの読み取りを ファイル メニュー、開く コマンドを実装します。 これに対し、する必要があります実装コマンド [編集] メニュー自分で、コピーするため ID_EDIT_COPY などのコマンドは、データの性質によって異なります。

用意されている実装のレベルとサポートされているコマンドの詳細については、次を参照してください。[テクニカル ノート 22:](../mfc/tn022-standard-commands-implementation.md)します。 標準のコマンドは、コマ ファイルで定義されます。H.

## <a name="see-also"></a>関連項目

[ユーザー インターフェイス オブジェクトとコマンド ID](../mfc/user-interface-objects-and-command-ids.md)
