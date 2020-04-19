---
title: メッセージ ハンドラー
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
ms.openlocfilehash: 25805187f88c5423ea41cd7cbe346e44e7d7d36a
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907464"
---
# <a name="message-handlers"></a>メッセージ ハンドラー

MFC では、専用の*ハンドラー*関数が個々のメッセージを処理します。 メッセージハンドラー関数は、クラスのメンバー関数です。 このドキュメントでは、*メッセージハンドラーメンバー関数*、メッセージ*ハンドラー関数*、*メッセージハンドラー*、および*ハンドラー*という用語を使用します。 一部の種類のメッセージハンドラーは、"コマンドハンドラー" とも呼ばれます。

フレームワークアプリケーションの作成における作業の大部分に対するメッセージハンドラーアカウントの作成。 この記事ファミリでは、メッセージ処理機構のしくみについて説明します。

メッセージのハンドラーは、メッセージへの応答としてどのような処理を実行しますか。 クラスの[クラスウィザード](reference/mfc-class-wizard.md)を使用してハンドラーを作成し、ソースコードエディターを使用してハンドラーのコードを入力することができます。

Microsoft Visual C++と MFC のすべての機能を使用して、ハンドラーを記述できます。 すべてのクラスの一覧については、「 *MFC リファレンス*」の「[クラスライブラリの概要](../mfc/class-library-overview.md)」を参照してください。

## <a name="see-also"></a>関連項目

[フレームワークのメッセージとコマンド](../mfc/messages-and-commands-in-the-framework.md)
