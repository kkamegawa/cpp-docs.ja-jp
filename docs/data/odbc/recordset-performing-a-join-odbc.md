---
title: レコード セット:結合 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
ms.openlocfilehash: 9e589f00ec0512794d14accc6bb33c0e7adbd378
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397732"
---
# <a name="recordset-performing-a-join-odbc"></a>レコード セット:結合 (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

## <a name="what-a-join-is"></a>どのような結合とは

結合操作、データ アクセスの一般的なタスクを使用して 1 つのレコード セット オブジェクトを使用して 1 つ以上のテーブルからデータを操作できます。 2 つ以上のテーブルを結合すると、各テーブルから列を含めることができますが、アプリケーションに 1 つのテーブルとして表示されるレコード セットが生成されます。 結合が、すべてのテーブルが、SQL のすべての列を使用することもあります**SELECT**結合句では、各テーブルの列の一部のみを使用します。 データベース クラスでは、読み取り専用の結合が、更新不可の結合をサポートします。

結合テーブルから列を含むレコードを選択するには、次のものが必要です。

- 結合されるすべてのテーブルの名前を含むテーブルの一覧。

- 参加しているすべての列の名前を含む列のリストです。 列の名前が同じ名前が異なるテーブルからは、テーブル名で修飾されます。

- フィルター (SQL **WHERE**句)、テーブルが参加している列を指定します。 このフィルターは"Table1.KeyCol = Table2.KeyCol"、実際には、結合を行うことができます。

同じ方法で 2 つ以上のテーブルを結合するには列の複数のペア、SQL キーワード、参加させる各ペアが等しいか調査して**AND**します。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: 定義済みクエリのクラスの宣言 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[レコードセット: テーブル用のクラスの宣言 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[レコードセット: レコードセットのクエリの再実行 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)
