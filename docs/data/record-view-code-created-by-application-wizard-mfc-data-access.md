---
title: アプリケーション ウィザードで作成されたレコード ビューのコード (MFC データ アクセス)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: e25ca9cad1390dd11ab7328ffefed31badf6fc0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152684"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>アプリケーション ウィザードで作成されたレコード ビューのコード (MFC データ アクセス)

[MFC アプリケーション ウィザード](../mfc/reference/database-support-mfc-application-wizard.md)上書きビューの`OnInitialUpdate`と`OnGetRecordset`メンバー関数。 このフレームワークによってフレーム ウィンドウ、ドキュメント、およびビューが作成された後、`OnInitialUpdate` が呼び出されてビューが初期化されます。 `OnInitialUpdate` は、レコードセットへのポインターをドキュメントから取得します。 基底クラスへの呼び出し[:oninitialupdate](../mfc/reference/cview-class.md#oninitialupdate)関数は、レコード セットを開きます。 次のコードに対して、このプロセスを示しています、 `CRecordView`:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

レコードセットが開くと、レコードが選択されます。 [:Open](../mfc/reference/crecordset-class.md#open) DDX にデータを移動、レコード セットのフィールド データ メンバーから、対応するコントロールをフォーム ビューで、現在のレコードは、最初のレコードを使用します。 RFX の詳細については、次を参照してください。[レコード フィールド エクス チェンジ (RFX)](../data/odbc/record-field-exchange-rfx.md)します。 DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../mfc/dialog-data-exchange-and-validation.md)」を参照してください。 ドキュメント/ビューの作成手順については、次を参照してください。 [Windows のアプリケーションを記述するクラスを使用して](../mfc/using-the-classes-to-write-applications-for-windows.md)します。

> [!NOTE]
>  エンド ユーザーには、レコードセットからレコード ビュー コントロールを更新するための機能を提供する必要があります。 この機能がないと、ユーザーがコントロールの値を無効な値に変更した場合に、現在のレコードを一切操作できなくなる可能性があります。 呼び出すコントロールを更新する、`CWnd`メンバー関数は[UpdateData](../mfc/reference/cwnd-class.md#updatedata) FALSE のパラメーターを持つ。

## <a name="see-also"></a>関連項目

[レコード ビューの使用](../data/using-a-record-view-mfc-data-access.md)