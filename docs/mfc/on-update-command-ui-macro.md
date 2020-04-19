---
title: ON_UPDATE_COMMAND_UI マクロ
ms.date: 09/06/2019
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: 2a3f097a44e96fc470719ce636cc1b73e676fb38
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095841"
---
# <a name="on_update_command_ui-macro"></a>ON_UPDATE_COMMAND_UI マクロ

コマンドターゲットオブジェクトのコマンド更新ハンドラーにユーザーインターフェイスオブジェクトを接続するには、**クラスビュー**を開き、ハンドラーを追加するクラスを右クリックして、 **[クラスウィザード]** を選択します。 左側の一覧でユーザーインターフェイスオブジェクトの ID を探し、右側のウィンドウで **[UPDATE_COMMAND_UI]** を選択し、 **[ハンドラーの追加]** をクリックします。 これにより、クラスにハンドラー関数が作成され、メッセージマップに適切なエントリが追加されます。 詳細については、「[関数へのメッセージのマッピング](../mfc/reference/mapping-messages-to-functions.md)」を参照してください。 **メッセージ**ウィンドウで、処理する追加のメッセージを指定できます。

たとえば、プログラムの [編集] メニューの [すべてクリア] コマンドを更新するには、**クラスウィザード**を使用して、選択したクラスのメッセージマップエントリ、クラス宣言で呼び出され`OnUpdateEditClearAll`たコマンド更新ハンドラーの関数宣言、および空のを追加します。クラスの実装ファイルの関数テンプレート。 関数プロトタイプは次のようになります。

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

すべてのハンドラーと同様に、関数宣言は**afx_msg**キーワードを示しています。 すべての更新ハンドラーと同様に、 `CCmdUI`オブジェクトへのポインターである1つの引数を受け取ります。

## <a name="see-also"></a>関連項目

[方法: ユーザー インターフェイス オブジェクトを更新する](../mfc/how-to-update-user-interface-objects.md)
