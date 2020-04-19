---
title: フレームワークのダイアログ ボックス コンポーネント
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
ms.openlocfilehash: 15d01924be811a9c9ec8ea333870f444bf9aa61a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685832"
---
# <a name="dialog-box-components-in-the-framework"></a>フレームワークのダイアログ ボックス コンポーネント

MFC フレームワークのダイアログボックスには、次の2つのコンポーネントがあります。

- ダイアログボックスのコントロールとその配置を指定するダイアログテンプレートリソース。

   ダイアログリソースには、Windows によってダイアログウィンドウが作成されて表示されるダイアログテンプレートが格納されます。 このテンプレートでは、ダイアログボックスのサイズ、位置、スタイル、ダイアログボックスのコントロールの種類と位置など、ダイアログボックスの特性を指定します。 通常は、リソースとして格納されているダイアログテンプレートを使用しますが、独自のテンプレートをメモリに作成することもできます。

- ダイアログボックスを管理するためのプログラムインターフェイスを提供するための、 [CDialog](../mfc/reference/cdialog-class.md)から派生したダイアログクラス。

   ダイアログボックスはウィンドウであり、表示されると Windows のウィンドウに追加されます。 ダイアログウィンドウが作成されると、ダイアログボックスの子ウィンドウコントロールを作成するためのテンプレートとして、ダイアログテンプレートリソースが使用されます。

## <a name="see-also"></a>関連項目

[ダイアログ ボックス](../mfc/dialog-boxes.md)<br/>
[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)
