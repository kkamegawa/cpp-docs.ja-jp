---
title: レコード ビューのデータ交換 (MFC データ アクセス)
ms.date: 11/19/2018
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
ms.openlocfilehash: a7c6714218b5891e078e750a974faed274e113c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397997"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>レコード ビューのデータ交換 (MFC データ アクセス)

使用すると[クラスの追加](../mfc/reference/adding-an-mfc-odbc-consumer.md)レコード ビューのダイアログ テンプレート リソース内のコントロールをレコード セットのフィールドにマップするには、フレームワークは双方向のデータ交換を管理 — コントロールをレコード セットとレコード セットへのコントロールから。 DDX 機構を使用すると、データを双方向で転送するコードを自分で記述する必要がなくなります。

レコード ビューの DDX はと共に動作[RFX](../data/odbc/record-field-exchange-rfx.md)クラスのレコード セット`CRecordset`(ODBC)。  Rfx 関数は、データ ソースの現在のレコードとレコード セット オブジェクトのフィールド データ メンバーの間のデータを移動します。 DDX は、フィールド データ メンバーからフォーム内のコントロールにデータを移動します。 このように組み合わせると、フォーム コントロールに初期値が設定され、ユーザーがレコード間を移動したときにも値が設定されます。 更新されたデータをレコードセットに戻し、さらにデータ ソースまで移動することもできます。

次の図は、レコード ビューの DDX と RFX 間のリレーションシップを示します。

![ダイアログ&#45;データ交換およびレコード&#45;フィールド エクス チェンジ](../data/media/vc37xt1.gif "ダイアログ&#45;データ交換およびレコード&#45;フィールド エクス チェンジ")<br/>
ダイアログ データ エクスチェンジ (DDX) とレコード フィールド エクスチェンジ (RFX)

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../mfc/dialog-data-exchange-and-validation.md)」を参照してください。 RFX の詳細については、次を参照してください。[レコード フィールド エクス チェンジ (RFX)](../data/odbc/record-field-exchange-rfx.md)します。

## <a name="see-also"></a>関連項目

[レコード ビュー (MFC データ アクセス)](../data/record-views-mfc-data-access.md)<br/>
[ODBC ドライバーの一覧](../data/odbc/odbc-driver-list.md)