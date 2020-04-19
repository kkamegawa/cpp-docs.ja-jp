---
title: レコード ビューを利用するために必要な作業 (MFC データ アクセス)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
ms.openlocfilehash: c5c35208f654cff90e3cdf87e697e654bdfbe307
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153334"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>レコード ビューを利用するために必要な作業 (MFC データ アクセス)

次の表は、レコード ビューを使用するために通常必要となる作業と、フレームワークの役割を示しています。

### <a name="working-with-a-record-view-you-and-the-framework"></a>レコード ビューの操作。フレームワーク

|プログラマの役割|フレームワークの役割|
|---------|-------------------|
|Visual C++ ダイアログ エディターを使用して、フォームをデザインします。|コントロール付きのダイアログ テンプレート リソースを作成します。|
|使用して、 [MFC アプリケーション ウィザード](../mfc/reference/database-support-mfc-application-wizard.md)から派生したクラスを作成する[CRecordView](../mfc/reference/crecordview-class.md)と[CRecordset](../mfc/reference/crecordset-class.md)します。|派生クラスを作成します。|
|レコード ビューのコントロールをレコードセットのフィールド データ メンバーに対応付けます。|コントロールとレコードセット フィールド間で DDX を行います。|
||既定のコマンドに対するコマンド ハンドラーを提供します**Move First**、**最後に移動**、 **Move Next**と**Move Previous**メニューまたはツールバーからコマンドボタン。|
||データ ソースへの変更を反映します。|
|(省略可能) リスト ボックス、コンボ ボックスなどのコントロールにセカンド レコードセットのデータを設定するためのコードを記述します。||
|(省略可能) 特別な検証用のコードを記述します。||
|(省略可能) レコードを追加または削除するためのコードを記述します。||

フォーム ベースのプログラミングは、データベース操作の単なる 1 つの手法です。 ユーザー インターフェイスのないその他のユーザー インターフェイスを使用してアプリケーションについては、次を参照してください[MFC:。ドキュメントとビューを用いたデータベース クラス](../data/mfc-using-database-classes-with-documents-and-views.md)と[MFC:ドキュメントとビューを用いないデータベース クラスを使用して](../data/mfc-using-database-classes-without-documents-and-views.md)します。 データベースのレコードを表示するための代替アプローチは、クラスを参照してください。 [CListView](../mfc/reference/clistview-class.md)と[CTreeView](../mfc/reference/ctreeview-class.md)します。

## <a name="see-also"></a>関連項目

[レコード ビュー (MFC データ アクセス)](../data/record-views-mfc-data-access.md)<br/>
[ODBC ドライバーの一覧](../data/odbc/odbc-driver-list.md)