---
title: レコードセット (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, snapshots
- recordsets, creating
- dynamic recordsets
- forward-only recordsets
- recordsets, dynasets
- ODBC recordsets, CRecordset objects
- ODBC recordsets
- recordsets, about recordsets
- snapshots, ODBC recordsets
- dynasets
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
ms.openlocfilehash: b043b08e13611b87bbffbe9dfb3255d5520e3359
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707836"
---
# <a name="recordset-odbc"></a>レコードセット (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

[CRecordset](../../mfc/reference/crecordset-class.md) オブジェクトは、データ ソースから選択された 1 組のレコードセットです。 レコードのデータ ソース:

- テーブル。

- クエリ。

- 1 つまたは複数のテーブルにアクセスするストアド プロシージャ。

テーブルに基づくレコードセットの例は "all customers" です。これは Customer テーブルにアクセスします。 クエリの例は "all invoices for Joe Smith" です。 ストアド プロシージャ (事前定義クエリと呼ばれることもあります) に基づくレコードセットの例は、"all of the delinquent accounts" です。これは、バックエンド データベースでストアド プロシージャを呼び出します。 レコードセットでデータ ソースを同じくする 2 つ以上のテーブルを結合できますが、データ ソースの異なるテーブルは結合できません。

> [!NOTE]
>  一部の ODBC ドライバーでは、データベースのビューがサポートされます。 この意味でのビューは、SQL `CREATE VIEW` ステートメントでもともと作成されたクエリです。

##  <a name="_core_recordset_capabilities"></a> レコードセットの機能

すべてのレコードセット オブジェクトに次の機能があります。

- データ ソースが読み取り専用ではない場合、レコードセットに[更新可能](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)、[追加可能](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)、または読み取り専用を指定できます。 レコードセットが更新可能な場合、適切なロッキング サポートがドライバーから与えられるとき、ペシミスティックまたはオプティミスティックの[ロッキング](../../data/odbc/recordset-locking-records-odbc.md) メソッドを選択できます。 データ ソースが読み取り専用の場合、レコードセットは読み取り専用になります。

- メンバー関数を呼び出し、選択されているレコードを[スクロール](../../data/odbc/recordset-scrolling-odbc.md)しながら見ることができます。

- レコードに[フィルター](../../data/odbc/recordset-filtering-records-odbc.md)を適用し、利用できるレコードから選択されるレコードを絞り込むことができます。

- 1 つまたは複数の列に基づき、レコードを昇順または降順で[並べ替える](../../data/odbc/recordset-sorting-records-odbc.md)ことができます。

- レコードセットを[パラメーター化](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)し、実行時のレコードセット選択を修正できます。

##  <a name="_core_snapshots_and_dynasets"></a> スナップショットとダイナセット

レコードセットには、[スナップショット](../../data/odbc/snapshot.md)と[ダイナセット](../../data/odbc/dynaset.md)という 2 種類のプリンシパルがあります。 いずれもクラス `CRecordset` でサポートされています。 いずれにもすべてのレコードセットで共通の特性がありますが、さらにそれぞれのレコードセットにおいて独自の特別な方法でその共通機能が拡張されます。 スナップショットではデータが静的に表示され、レポートや、特定の時点でのデータを表示する必要がある他の状況で役に立ちます。 ダイナセットは、他のユーザーが行った更新をレコードセットに表示するときに便利です。レコードセットを再度問い合わせたり、更新したりする必要がありません。 スナップショットとダイナセットは更新可能か読み取り専用にすることができます。 他のユーザーが追加または削除したレコードを反映させるには、[CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery) を呼び出します。

`CRecordset` では、他にも 2 種類のレコードセット、動的レコードセットと前方スクロール専用レコードセットが許可されます。 動的レコードセットはダイナセットに似ていますが、動的レコードの場合、`CRecordset::Requery` を呼び出さなくても、追加または削除されたあらゆるレコードが反映されます。 そのため、動的レコードセットは DBMS の処理時間に関連し、一般的に高額になります。多くの ODBC ドライバーでサポートされていません。 対照的に、前方スクロール専用レコードセットの場合、更新や後方スクロールを必要としない、最も効率的な方法でレコードセットのデータにアクセスできます。 たとえば、前方スクロール専用レコードセットを使用し、データ ソース間でデータを移行します。前方にデータを動かすだけでこの移行は完了します。 前方スクロール専用レコードセットを使用するには、次の両方を行う必要があります。

- [Open](../../mfc/reference/crecordset-class.md#open) メンバー関数の *nOpenType* パラメーターとしてオプション `CRecordset::forwardOnly` を渡します。

- `Open` の *dwOptions* パラメーターに `CRecordset::readOnly` を指定します。

    > [!NOTE]
    >  ダイナセット サポートの ODBC ドライバー要件については、「[ODBC](../../data/odbc/odbc-basics.md)」を参照してください。 Visual C++ のこのバージョンに含まれている ODBC ドライバー一覧、および他のドライバーを取得する方法については、「[ODBC ドライバーの一覧](../../data/odbc/odbc-driver-list.md)」を参照してください。

##  <a name="_core_your_recordsets"></a> レコード セット

アクセスする個々のテーブル、ビュー、ストアド プロシージャごとに、通常、`CRecordset` から派生するクラスを定義します。 (例外はデータベース結合であり、その場合、1 つのレコードセットは 2 つ以上のテーブルからの列を表します。)レコードセット クラスを誘導するとき、レコード フィールド エクスチェンジ (RFX) メカニズムまたは一括レコード フィールド エクスチェンジ (一括 RFX) メカニズムを有効にします。これらのメカニズムは、ダイアログ データ エクスチェンジ (DDX) メカニズムに似ています。 RFX と一括 RFX では、データ ソースからレコードセットにデータを簡単に転送できます。RFX ではまた、レコードセットからデータ セットにデータが転送されます。 詳細については、「[レコード フィールド エクスチェンジ (RFX)](../../data/odbc/record-field-exchange-rfx.md)」と「[レコードセット:レコードの一括フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」を参照してください。

レコードセット オブジェクトからは、選択したすべてのレコードにアクセスする許可が与えられます。 `MoveNext` や `MovePrev` など、`CRecordset` メンバー関数を利用し、選択されている複数のレコードをスクロールして閲覧します。 レコードセット オブジェクトは同時に、選択されているレコードのうち 1 つだけ、現在のレコードを表します。 データベース クエリから結果的に生成されたテーブルまたはレコードの列に対応するレコードセット クラス メンバー変数を宣言することで、現在のレコードのフィールドを調べることができます。 レコードセット データ メンバーの詳細については、「[レコードセット:アーキテクチャ (ODBC)](../../data/odbc/recordset-architecture-odbc.md)」を参照してください。

次のトピックでは、レコードセット オブジェクトの使用について説明しています。 トピックの一覧は機能的なカテゴリに基づいて表示されており、順を追って読めるよう、自然な閲覧順になっています。

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>レコードセットを開き、読み、閉じるためのメカニズムに関するトピック

- [レコードセット: アーキテクチャ (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [レコードセット: テーブル用のクラスの宣言 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [レコードセット: レコードセットの作成成と破棄 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [レコードセット: スクロール (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [レコードセット: ブックマークと絶対位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [レコードセット: レコードのフィルター処理 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [レコードセット: レコードの並べ替え (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [レコードセット: レコードセットのパラメーター化 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>レコードセットの変更メカニズムに関するトピック

- [レコードセット: レコードの追加、更新、削除 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [レコードセット: レコードのロック (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [レコードセット: レコードセットのクエリの再実行 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>やや高度な手法に関するトピック

- [レコードセット: 結合の実行 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [レコードセット: 定義済みクエリのクラスの宣言 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [レコードセット: データ列の動的なバインド (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [レコードセット: レコードの一括フェッチ (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [レコードセット: 大きいデータ項目の処理 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [レコードセット: 合計とその他の集計結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>レコード セットのしくみに関するトピック

- [レコードセット: レコードセットでのレコード選択のしくみ (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [レコードセット: レコードセットでのレコード更新のしくみ (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>関連項目

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[MFC ODBC コンシューマー](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)