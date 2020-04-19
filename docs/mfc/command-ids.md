---
title: コマンド ID
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: 76071105e72f1ca4a851b9cdb76d5f1a96f44edb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219900"
---
# <a name="command-ids"></a>コマンド ID

コマンドが、コマンド ID だけで完全に説明されている (でエンコードされた、 **WM_COMMAND**メッセージ)。 この ID は、コマンドを生成するユーザー インターフェイス オブジェクトに割り当てられます。 通常、Id に割り当てられているユーザー インターフェイス オブジェクトの機能の名前です。

たとえば、編集 メニューで すべてクリア項目割り当てられる可能性が ID など**ID_EDIT_CLEAR_ALL**します。 クラス ライブラリは特に、フレームワークを処理するなどのコマンドの場合、何らかの Id が組み込まれて**ID_EDIT_CLEAR_ALL**または**ID_FILE_OPEN**します。 その他のコマンド Id 自分で作成します。

ビジュアルで独自のメニューを作成するときC++クラス ライブラリに従うことをお勧めの名前付け規則のようには、そのメニュー エディター、 **ID_FILE_OPEN**します。 [標準コマンド](../mfc/standard-commands.md)クラス ライブラリによって定義される標準のコマンドについて説明します。

## <a name="see-also"></a>関連項目

[ユーザー インターフェイス オブジェクトとコマンド ID](../mfc/user-interface-objects-and-command-ids.md)
