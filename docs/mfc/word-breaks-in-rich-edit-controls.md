---
title: リッチ エディット コントロールでのワード区切り
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
ms.openlocfilehash: e71643350ced5b8ecff7c8ac7829741cc3e8493b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399539"
---
# <a name="word-breaks-in-rich-edit-controls"></a>リッチ エディット コントロールでのワード区切り

リッチ エディット コントロール ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))「という単語区切りプロシージャ」という名前の関数を呼び出して単語の区切り記号を検索し、行を壊すことを決定します。 コントロールは、ctrl キーを押しながら左と CTRL + → キーの組み合わせを処理するときに、ワード ラップ操作の実行時にこの情報を使用します。 アプリケーションは、単語区切りの情報を取得し、特定の文字がある行を決定する既定単語区切りプロシージャを置換するリッチ エディット コントロールにメッセージが送信できます。

## <a name="see-also"></a>関連項目

[CRichEditCtrl の使い方](../mfc/using-cricheditctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
