---
title: MFC でのダイアログボックスの操作
ms.date: 09/27/2019
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: ad15250cf9a8dd663072cf9423263260bbb40a0e
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685723"
---
# <a name="working-with-dialog-boxes-in-mfc"></a>MFC でのダイアログボックスの操作

ダイアログボックスのライフサイクル中に、ユーザーはダイアログボックスを起動します。通常は、ダイアログオブジェクトを作成して初期化するコマンドハンドラー内で、ユーザーがダイアログボックスを操作し、ダイアログボックスが閉じます。

モーダルダイアログボックスでは、ダイアログボックスを閉じると、ユーザーが入力したデータがハンドラーによって収集されます。 ダイアログオブジェクトはダイアログウィンドウが閉じられた後に存在するため、ダイアログクラスのメンバー変数を使用してデータを抽出できます。

モードレスダイアログボックスの場合、ダイアログボックスがまだ表示されている間に、ダイアログオブジェクトからデータを抽出することがよくあります。 ある時点で、ダイアログオブジェクトが破棄されます。このような状況が発生するのは、コードによって異なります。

## <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- [ダイアログボックスの作成と表示](../mfc/creating-and-displaying-dialog-boxes.md)

- [モーダルダイアログボックスの作成](../mfc/creating-modal-dialog-boxes.md)

- [モードレスダイアログボックスの作成](../mfc/creating-modeless-dialog-boxes.md)

- [メモリでダイアログテンプレートを使用する](../mfc/using-a-dialog-template-in-memory.md)

- [ダイアログボックスの背景色の設定](../mfc/setting-the-dialog-boxs-background-color.md)

- [ダイアログボックスの初期化](../mfc/initializing-the-dialog-box.md)

- [ダイアログボックスでの Windows メッセージの処理](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [ダイアログオブジェクトからのデータの取得](../mfc/retrieving-data-from-the-dialog-object.md)

- [ダイアログボックスを閉じる](../mfc/closing-the-dialog-box.md)

- [ダイアログボックスの破棄](../mfc/destroying-the-dialog-box.md)

- [ダイアログデータエクスチェンジ (DDX) と検証 (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [プロパティシートのダイアログボックス](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>関連項目

[ダイアログ ボックス](../mfc/dialog-boxes.md)
