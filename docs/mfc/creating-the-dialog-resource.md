---
title: ダイアログ リソースの作成
ms.date: 11/04/2016
helpviewer_keywords:
- dialog resources
- MFC dialog boxes [MFC], creating
- dialog templates [MFC], creating dialog resource
- templates [MFC], creating
- resources [MFC], creating dialog boxes
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 0b83bd33-14d3-4611-8129-fccdae18053e
ms.openlocfilehash: 7b1e6c81a0f4bd6983c2a76baf6148941a4fa21d
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685635"
---
# <a name="creating-the-dialog-resource"></a>ダイアログ リソースの作成

ダイアログ[ボックス](../mfc/dialog-boxes.md)をデザインし、ダイアログリソースを作成するには、[ダイアログエディター](../windows/dialog-editor.md)を使用します。 ダイアログエディターでは、次のことができます。

- ダイアログボックスが表示されるときのサイズと位置を調整します。

- コントロールパレットからさまざまな種類のコントロールをドラッグし、ダイアログボックスで必要な位置にドロップします。

- ツールバーの配置ボタンを使用してコントロールを配置します。

- プログラムに表示される外観と動作をシミュレートして、ダイアログボックスをテストします。 テストモードでは、テキストボックスにテキストを入力したり、プッシュボタンをクリックしたりして、ダイアログボックスのコントロールを操作できます。

完了すると、ダイアログテンプレートリソースがアプリケーションのリソーススクリプトファイルに格納されます。 必要に応じて後で編集できます。 ダイアログリソースを作成および編集する方法の詳細については、「[ダイアログエディター](../windows/dialog-editor.md)のトピック」を参照してください。 この手法は、 [CFormView](../mfc/reference/cformview-class.md)クラスおよび[CRecordView](../mfc/reference/crecordview-class.md)クラスのダイアログテンプレートリソースを作成するためにも使用されます。

ダイアログボックスが表示されたら、「[コードウィザードを使用してダイアログクラスを作成](../mfc/creating-a-dialog-class-with-code-wizards.md)する」で説明されているように、ダイアログクラスを作成し、メッセージをマップします。

## <a name="see-also"></a>関連項目

[ダイアログ ボックス](../mfc/dialog-boxes.md)<br/>
[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)
