---
title: ダイアログ エディターを使用したコントロールの追加
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controls [MFC], adding to dialog boxes
- Dialog editor, creating controls
- common controls [MFC], adding
ms.assetid: d3f9f994-7e54-4656-a545-42c204557c36
ms.openlocfilehash: b88056d1c44e434e77f3f3b94976bf92516bbf3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411488"
---
# <a name="using-the-dialog-editor-to-add-controls"></a>ダイアログ エディターを使用したコントロールの追加

ダイアログ テンプレート リソースを作成する場合、[ダイアログ エディター](../windows/dialog-editor.md)、コントロール パレットからコントロールをドラッグし、ダイアログ ボックスにドロップします。 これにより、そのコントロール型の仕様がダイアログ テンプレート リソースを追加します。 ダイアログ オブジェクトと呼び出しを構築する際にその`Create`または`DoModal`メンバー関数は、フレームワークが Windows コントロールを作成し、画面のダイアログ ウィンドウに配置されます。

代わりにできます[コントロールを手動で作成](../mfc/adding-controls-by-hand.md)たい場合。 これより多くの作業です。

## <a name="see-also"></a>関連項目

[コントロールの作成方法と使い方](../mfc/making-and-using-controls.md)<br/>
[コントロール](../mfc/controls-mfc.md)
