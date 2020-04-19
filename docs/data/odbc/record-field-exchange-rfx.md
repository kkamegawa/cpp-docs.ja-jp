---
title: レコード フィールド エクスチェンジ (RFX)
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
ms.openlocfilehash: 8630fab11728b0c0cd16eee5035df028a8382706
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395717"
---
# <a name="record-field-exchange-rfx"></a>レコード フィールド エクスチェンジ (RFX)

MFC ODBC データベース クラスは、データ ソース間のデータの移動を自動化し、 [recordset](../../data/odbc/recordset-odbc.md)オブジェクト。 クラスを派生する[CRecordset](../../mfc/reference/crecordset-class.md)レコード フィールド エクス (チェンジ RFX) メカニズムによってデータが転送される、バルク行フェッチを使用しないでください。

> [!NOTE]
>  派生にバルク行フェッチを実装している場合`CRecordset`クラス、データを転送するには使用、バルク レコード フィールド エクス チェンジ (Bulk RFX) メカニズムをフレームワーク。 詳細については、次を参照してください。[レコード セット。(ODBC) バルク行フェッチ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)します。

Rfx 関数は、ダイアログ データ エクス (チェンジ DDX) と似ています。 データ ソースとレコード セットのフィールド データ メンバーのデータを移動するには、レコード セットの複数の呼び出しが必要です[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)フレームワーク間の関数の相互作用と[ODBC](../../data/odbc/odbc-basics.md). RFX メカニズムがタイプ セーフし、などの ODBC 関数を呼び出すことの作業を保存する`::SQLBindCol`します。 DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

RFX は意識する必要はほとんどの場合です。 MFC アプリケーション ウィザードを使用して、レコード セット クラスを宣言したかどうかまたは**クラスの追加**(」の説明に従って[MFC ODBC コンシューマーの追加](../../mfc/reference/adding-an-mfc-odbc-consumer.md))、RFX がそれらに自動的に組み込まれています。 レコード セット クラスは基底クラスから派生する必要があります`CRecordset`framework によって提供されます。 MFC アプリケーション ウィザードでは、最初のレコード セット クラスを作成できます。 **クラスを追加**必要に応じて、他のレコード セット クラスを追加することができます。 詳細と例については、次を参照してください。 [MFC ODBC コンシューマーの追加](../../mfc/reference/adding-an-mfc-odbc-consumer.md)します。

場合に、3 つのケースで少量の rfx 関数のコードを追加する必要があります手動で。

- パラメーター化クエリを使用します。 詳細については、次を参照してください。[レコード セット。レコード セット (ODBC) をパラメーター化](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)します。

- 結合 (2 つ以上のテーブルの列の 1 つのレコード セットの使用) を実行します。 詳細については、次を参照してください。[レコード セット。結合 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)します。

- データ列を動的にバインドします。 これは、パラメーター化よりもまれです。 詳細については、次を参照してください。[レコード セット。動的に結びつける方法 (ODBC) のデータ列](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)します。

RFX の高度な知識が必要な場合は、次を参照してください。[レコード フィールド エクス チェンジ。RFX のしくみ](../../data/odbc/record-field-exchange-how-rfx-works.md)します。

次のトピックでは、レコード セット オブジェクトの使用の詳細について説明します。

- [レコード フィールド エクスチェンジ: RFX の使い方](../../data/odbc/record-field-exchange-using-rfx.md)

- [レコード フィールド エクスチェンジ: RFX 関数の使い方](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [レコード フィールド エクスチェンジ: RFX の動作のしくみ](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>関連項目

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[MFC ODBC コンシューマーします。](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[[データベース サポート] (MFC アプリケーション ウィザード)](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)