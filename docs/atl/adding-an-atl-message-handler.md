---
title: ATL メッセージ ハンドラーの追加
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
ms.openlocfilehash: cc7631ac9e02891cee725b47133a273e756759d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223468"
---
# <a name="adding-an-atl-message-handler"></a>ATL メッセージ ハンドラーの追加

コントロールには、メッセージ ハンドラー (Windows メッセージを処理するメンバー関数) を追加するに最初に、クラス ビューでコントロールを選択します。 開き、**プロパティ**ウィンドウで、**メッセージ**アイコン、および反対の必要なメッセージ ボックス、ドロップダウン リストを制御 をクリックします。 これは、コントロールのヘッダー ファイルと、コントロールの .cpp ファイルのハンドラーのスケルトンの実装で、メッセージ ハンドラーの宣言を追加します。 メッセージ マップを追加し、ハンドラーのエントリを追加します。

ATL でのメッセージ ハンドラーを追加することは、MFC クラスへのメッセージ ハンドラーの追加に似ています。 参照してください[MFC メッセージ ハンドラーの追加](../mfc/reference/adding-an-mfc-message-handler.md)詳細についてはします。

ATL メッセージ ハンドラーを追加する場合のみ、次の条件が適用されます。

- メッセージ ハンドラーでは、MFC と同じ名前付け規則に従います。

- メイン メッセージ マップに新しいメッセージ マップ エントリが追加されます。 ウィザードでは、代替メッセージ マップおよびチェーンは認識されません。

## <a name="see-also"></a>関連項目

[ウィンドウの実装](../atl/implementing-a-window.md)
