---
title: 更新ハンドラーが呼び出されるタイミング
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- command routing [MFC], update commands
- toolbar buttons [MFC], enabling
- disabling toolbar buttons
- menus [MFC], initializing
- update handlers [MFC]
- disabling menu items
- toolbars [MFC], updating
- menus [MFC], updating as context changes
- toolbar controls [MFC], updated during OnIdle method [MFC]
- menu items, enabling
- command routing [MFC], update handlers
- update handlers, calling
ms.assetid: 7359f6b1-4669-477d-bd99-690affed08d9
ms.openlocfilehash: 4a52c147d1abf02b7c5e89abf868f87a07ab32cc
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346062"
---
# <a name="when-update-handlers-are-called"></a>更新ハンドラーが呼び出されるタイミング

たとえば、ユーザーがマウスのポインターのメッセージを生成します [ファイル] メニューをクリックします。 ユーザーが確認できるように、メニューをドロップダウンする前に、フレームワークの更新メカニズムはまとめてファイル メニューのすべての項目を更新します。

これを行うには、フレームワークのルートは、すべてのメニュー項目の標準コマンド ルーティングに沿って、ポップアップ メニューのコマンドを更新します。 ルーティング上のコマンド ターゲットを適切なメッセージ マップ エントリと update コマンドを照合することでメニュー項目を更新する機会があります (フォームの`ON_UPDATE_COMMAND_UI`)、「更新ハンドラー」関数を呼び出すとします。 そのため、6 つのメニュー項目を含むメニューの 6 つの update コマンドが送信されます。メニュー項目のコマンド ID の更新ハンドラーが存在する場合は、更新を行う呼び出されます。 ない場合、フレームワーク コマンド ID のハンドラーの有無を確認し、により、または適切なメニュー項目を無効にします。

フレームワークが見つからない場合、`ON_UPDATE_COMMAND_UI`コマンド ルーティング中にエントリを自動的に有効にしたユーザー インターフェイス オブジェクトがある場合、`ON_COMMAND`同じコマンド ID に置き換えますどこかのエントリ。 それ以外の場合、ユーザー インターフェイス オブジェクトが無効にします。 そのため、ユーザー インターフェイス オブジェクトが有効にするためには、オブジェクトを生成するコマンドのハンドラーを指定または、更新ハンドラーを指定します。 トピックの図を参照してください。[ユーザー インターフェイス オブジェクトとコマンド Id](../mfc/user-interface-objects-and-command-ids.md)します。

ユーザー インターフェイス オブジェクトの既定の無効化を無効にすることになります。 詳細については、次を参照してください。、 [m_bAutoMenuEnable](../mfc/reference/cframewnd-class.md#m_bautomenuenable)クラスのメンバー`CFrameWnd`で、 *MFC リファレンス*します。

メニューの初期化は、アプリケーションがポインター メッセージを受信する際に発生、フレームワークでは、自動です。 アイドル状態のループの中には、フレームワークは、コマンドのルーティングをボタンの更新ハンドラーのと同じようにメニューの場合と同様を検索します。

## <a name="see-also"></a>関連項目

[方法: ユーザー インターフェイス オブジェクトを更新する](../mfc/how-to-update-user-interface-objects.md)
