---
title: ダイアログ ボックスの初期化
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
ms.openlocfilehash: 14cdf94bef79f254b4aaa2c1c0dfba6c88b7498b
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685628"
---
# <a name="initializing-the-dialog-box"></a>ダイアログ ボックスの初期化

ダイアログボックスとそのすべてのコントロールが作成された後、ダイアログボックス (どちらかの種類) が画面に表示される直前に、ダイアログオブジェクトの[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)メンバー関数が呼び出されます。 モーダルダイアログボックスの場合は、`DoModal` の呼び出し中に発生します。 モードレスダイアログボックスの場合、`Create` が呼び出されると `OnInitDialog` が呼び出されます。 通常、エディットボックスの初期テキストの設定など、ダイアログボックスのコントロールを初期化するには、`OnInitDialog` をオーバーライドします。 `OnInitDialog` のオーバーライドから、基底クラスの `CDialog`の `OnInitDialog` メンバー関数を呼び出す必要があります。

ダイアログボックスの背景色 (およびアプリケーション内の他のすべてのダイアログボックスの背景色) を設定する場合は、「[ダイアログボックスの背景色を設定](../mfc/setting-the-dialog-boxs-background-color.md)する」を参照してください。

## <a name="see-also"></a>参照

[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)
