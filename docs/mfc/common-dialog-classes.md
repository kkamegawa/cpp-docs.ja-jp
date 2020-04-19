---
title: コモン ダイアログ クラス
ms.date: 11/04/2016
helpviewer_keywords:
- dialog classes [MFC]
- dialog boxes [MFC], Windows common dialogs
- common dialog boxes [MFC], common dialog classes
- common dialog classes [MFC]
- MFC dialog boxes [MFC], Windows common dialogs
- Windows common dialogs [MFC]
- dialog classes [MFC], common
- common dialog boxes [MFC]
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
ms.openlocfilehash: d11d0978763d9599b0471a8e994f15a267f7cb8f
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685555"
---
# <a name="common-dialog-classes"></a>コモン ダイアログ クラス

MFC では、クラス[CDialog](../mfc/reference/cdialog-class.md)に加えて、一般的に使用されるダイアログボックスをカプセル化する `CDialog` から派生した複数のクラスが用意されています。次の表を参照してください。 カプセル化されたダイアログボックスは、"コモンダイアログボックス" と呼ばれ、Windows コモンダイアログライブラリ (COMMDLG) の一部です。DLL)。 これらのクラスのダイアログテンプレートリソースとコードは、Windows バージョン3.1 以降の一部である Windows コモンダイアログボックスに用意されています。

### <a name="common-dialog-classes"></a>コモン ダイアログ クラス

|派生ダイアログクラス|目的|
|--------------------------|-------------|
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|ユーザーが色を選択できるようにします。|
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|開くファイルまたは保存するファイル名をユーザーが選択できるようにします。|
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|ユーザーがテキストファイルで検索または置換操作を開始できるようにします。|
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|ユーザーがフォントを指定できるようにします。|
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|印刷ジョブの情報をユーザーが指定できるようにします。|
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Windows Print プロパティシート。|

コモンダイアログクラスの詳細については、 *MFC リファレンス*の個々のクラス名を参照してください。 MFC には、OLE に使用される標準ダイアログクラスも多数用意されています。 これらのクラスの詳細については、 *MFC リファレンス*の基本クラスである[COleDialog](../mfc/reference/coledialog-class.md)を参照してください。

MFC の他の3つのクラスには、ダイアログのような特性があります。 クラス[CFormView](../mfc/reference/cformview-class.md)、 [CRecordView](../mfc/reference/crecordview-class.md)、および[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)の詳細については、 *MFC リファレンス*のクラスを参照してください。 クラス[CDialogBar](../mfc/reference/cdialogbar-class.md)の詳細については、「[ダイアログバー](../mfc/dialog-bars.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ダイアログ ボックス](../mfc/dialog-boxes.md)<br/>
[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[OLE のダイアログ ボックス](../mfc/dialog-boxes-in-ole.md)
