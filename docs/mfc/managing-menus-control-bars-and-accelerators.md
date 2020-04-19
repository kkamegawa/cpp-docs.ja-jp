---
title: メニュー、コントロール バー、およびアクセラレータの管理
ms.date: 11/04/2016
helpviewer_keywords:
- MDI [MFC], frame windows
- control bars [MFC], updating in frame windows
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- accelerator tables [MFC]
- sharing menus [MFC]
- updating user-interface objects [MFC]
- frame windows [MFC], updating
- status bars [MFC], updating
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
ms.openlocfilehash: 9a089829658265cd835a8c7344aa5bc45fbc109a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226171"
---
# <a name="managing-menus-control-bars-and-accelerators"></a>メニュー、コントロール バー、およびアクセラレータの管理

フレーム ウィンドウは、メニューのツールバーのボタン、ステータス バー、およびアクセラレータなどの更新のユーザー インターフェイス オブジェクトを管理します。 また、MDI アプリケーションでメニュー バーの共有を管理します。

## <a name="managing-menus"></a>メニューの管理

フレーム ウィンドウが「ON_UPDATE_COMMAND_UI メカニズムを使用してユーザー インターフェイスの項目の更新に参加する[ユーザー インターフェイス オブジェクトを更新する方法](../mfc/how-to-update-user-interface-objects.md)します。 ツールバーとその他のコントロール バーのボタンは、アイドル ループの中に更新されます。 ドロップダウン メニューの直前に、メニュー バーのドロップダウン メニューにメニュー項目が更新されます。

MDI アプリケーションでは、MDI フレーム ウィンドウは、メニュー バーとキャプションを管理します。 MDI フレーム ウィンドウには、アクティブな MDI 子ウィンドウがない場合に、メニュー バーとして使用される 1 つの既定のメニューが所有しています。 アクティブな子が存在する場合、その MDI フレーム ウィンドウのメニュー バーと、アクティブな MDI 子ウィンドウのメニューが引き継がれます。 MDI アプリケーションは、グラフとワークシートのドキュメントなど、複数のドキュメント タイプをサポートしている場合、各型は、独自のメニューでは、メニュー バーをし、メイン フレーム ウィンドウのキャプションを変更します。

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) MDI アプリケーションの [ウィンドウ] メニューに表示される標準のコマンドの既定の実装を提供します。 具体的には、新しいフレーム ウィンドウと現在のドキュメントのビューを作成する、新しいウィンドウ コマンド (ID_WINDOW_NEW) が実装されます。 高度なカスタマイズが必要な場合にのみ、これらの実装をオーバーライドする必要があります。

同じドキュメントの種類の複数の MDI 子ウィンドウは、メニュー リソースを共有します。 同じのドキュメント テンプレートでは、いくつかの MDI 子ウィンドウが作成された場合、すべてを使用できます Windows システム リソースを保存して、同じメニュー リソース。

## <a name="managing-the-status-bar"></a>ステータス バーの管理

フレーム ウィンドウも、クライアント領域内のステータス バーを配置し、状態を管理バーのインジケーター。 フレーム ウィンドウのクリアしメッセージ領域、ステータス バーに必要に応じて更新し、」の説明に従って、ユーザーがメニュー項目やツールバーのボタンを選択すると表示文字列を表示[ステータス バーにコマンド情報を表示する方法](../mfc/how-to-display-command-information-in-the-status-bar.md)します。

## <a name="managing-accelerators"></a>アクセラレータの管理

各フレーム ウィンドウは、自動的に変換するためにアクセラレータ キーボードをオプションのアクセラレータ テーブルを保持します。 このメカニズムにより、簡単にメニュー コマンドを呼び出すことのアクセラレータ キー (ショートカット キーとも呼ばれます) を定義できます。

## <a name="see-also"></a>関連項目

[フレーム ウィンドウの使用](../mfc/using-frame-windows.md)
