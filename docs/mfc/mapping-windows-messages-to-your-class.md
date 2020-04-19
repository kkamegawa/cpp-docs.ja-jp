---
title: ダイアログ クラスと Windows メッセージの対応
ms.date: 09/06/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
- Class Wizard [MFC]
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 0f1207faca56acd709db86478722eba85eeb284a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685608"
---
# <a name="mapping-windows-messages-to-your-class"></a>ダイアログ クラスと Windows メッセージの対応

Windows メッセージを処理するためのダイアログボックスが必要な場合は、適切なハンドラー関数をオーバーライドします。 これを行うには、**ソリューションエクスプローラー**の **[クラスビュー]** タブをクリックし、ダイアログボックスを表すクラスを右クリックして、[[クラスウィザード](reference/mfc-class-wizard.md)] を選択します。 ウィザードを使用して、メッセージをダイアログクラスに[マップ](../mfc/reference/mapping-messages-to-functions.md)します。 これにより、各メッセージのメッセージマップエントリが書き込まれ、メッセージハンドラーのメンバー関数がクラスに追加されます。 コードエディターを使用して、メッセージハンドラーにコードを記述します。

また、 [CDialog](../mfc/reference/cdialog-class.md)のメンバー関数とその基本クラス (特に[CWnd](../mfc/reference/cwnd-class.md)) をオーバーライドすることもできます。

## <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- [メッセージの処理とマッピング](../mfc/message-handling-and-mapping.md)

- [通常オーバーライドされるメンバー関数](../mfc/commonly-overridden-member-functions.md)

- [一般的に追加されるメンバー関数](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>関連項目

[ダイアログ ボックス](../mfc/dialog-boxes.md)<br/>
[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)
