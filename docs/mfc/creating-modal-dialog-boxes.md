---
title: モーダル ダイアログ ボックスの作成
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed0fe3b7ef8aeddea01f573bfe8e1c01a6b5b443
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685680"
---
# <a name="creating-modal-dialog-boxes"></a>モーダル ダイアログ ボックスの作成

モーダルダイアログボックスを作成するには、 [CDialog](../mfc/reference/cdialog-class.md)で宣言されている2つのパブリックコンストラクターのいずれかを呼び出します。 次に、呼び出すダイアログ オブジェクトの[DoModal](../mfc/reference/cdialog-class.md#domodal) ダイアログ ボックスを表示し、ユーザーが [ok] を選択するまで対話操作を管理またはキャンセルするメンバー関数。 この管理の `DoModal` は、ダイアログボックスがモーダルになることを意味します。 モーダルダイアログボックスの場合、`DoModal` はダイアログリソースを読み込みます。

## <a name="see-also"></a>関連項目

[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)
