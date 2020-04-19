---
title: ダイアログ ボックスの作成と表示
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
ms.openlocfilehash: 6d23e4d2c9249ce248eb8092963036f2ba5cacac
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685739"
---
# <a name="creating-and-displaying-dialog-boxes"></a>ダイアログ ボックスの作成と表示

ダイアログオブジェクトの作成は、2フェーズ操作です。 まず、ダイアログオブジェクトを構築してから、ダイアログウィンドウを作成します。 モーダルおよびモードレスのダイアログボックスは、それらを作成および表示するために使用されるプロセスで多少異なります。 次の表に、モーダルおよびモードレスのダイアログボックスを通常作成して表示する方法を示します。

### <a name="dialog-creation"></a>ダイアログの作成

|ダイアログの種類|作成方法|
|-----------------|----------------------|
|[固定](../mfc/creating-modeless-dialog-boxes.md)|@No__t-0 を構築してから、`Create` メンバー関数を呼び出します。|
|[モード](../mfc/creating-modal-dialog-boxes.md)|@No__t-0 を構築してから、`DoModal` メンバー関数を呼び出します。|

必要に応じて、ダイアログテンプレートリソースからではなく、構築した[メモリ内ダイアログテンプレート](../mfc/using-a-dialog-template-in-memory.md)からダイアログボックスを作成できます。 ただし、これは高度なトピックです。

## <a name="see-also"></a>関連項目

[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)
