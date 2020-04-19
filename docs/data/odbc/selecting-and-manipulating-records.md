---
title: レコードの選択と操作
ms.date: 05/09/2019
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: 745c0c35e42426242d92d720d5dcd3de631fb17b
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707805"
---
# <a name="selecting-and-manipulating-records"></a>レコードの選択と操作

> [!NOTE] 
> MFC ODBC コンシューマー ウィザードは、Visual Studio 2019 以降はご利用いただけなくなります。 引き続き、コンシューマーを手動で作成することはできます。

通常、SQL **SELECT** ステートメントを使用してデータ ソースからレコードを選択すると、テーブルまたはクエリからの一連のレコードである、結果セットが与えられます。 データベース クラスでは、レコードセット オブジェクトを使用し、結果セットを選択し、それにアクセスします。 これは、クラス [CRecordset](../../mfc/reference/crecordset-class.md) から誘導するアプリケーション固有クラスのオブジェクトです。 レコードセット クラスを定義するとき、それを関連付けるデータ ソース、使用するテーブル、テーブルの列を指定します。 MFC アプリケーション ウィザードまたは **[クラスの追加]** (「[MFC ODBC コンシューマーの追加](../../mfc/reference/adding-an-mfc-odbc-consumer.md)」で説明されています) により、特定のデータ ソースに接続するクラスが作成されます。 ウィザードによりクラス `CRecordset` の [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) メンバー関数が記述され、テーブル名が返されます。

実行時に [CRecordset](../../mfc/reference/crecordset-class.md) オブジェクトを使用することでできること:

- 現在のレコードのデータ フィールドを調べる。

- レコードセットをフィルターで絞り込むか、並べ替える。

- 既定の SQL **SELECT** ステートメントをカスタマイズする。

- スクロールして選択されたレコードを閲覧する。

- レコードを追加、更新、削除する (データ ソースもレコードセットも更新できる場合)。

- レコードセットで再度問い合わせできるかテストし、レコードセットの内容を更新する。

レコードセットの使用が終わったら、それを閉じて破棄します。 レコードセットの詳細については、「[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ODBC と MFC](../../data/odbc/odbc-and-mfc.md)