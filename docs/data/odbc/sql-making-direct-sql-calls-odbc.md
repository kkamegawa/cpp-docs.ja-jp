---
title: SQL:SQL の直接呼び出し (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
ms.openlocfilehash: fd528e7abb713e4b3eb2bd5388a29958a1bb006c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329973"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL:SQL の直接呼び出し (ODBC)

このトピックでは、次の内容について説明します。

- SQL の直接使用するときに呼び出されます。

- [直接的な SQL を作成する方法、データ ソースへの呼び出し](#_core_making_direct_sql_function_calls)します。

> [!NOTE]
>  この情報は、MFC ODBC クラスに適用されます。 MFC DAO クラスを使用する場合は、"比較の Microsoft Jet データベース エンジン SQL と ANSI SQL"DAO ヘルプのトピックを参照してください。

##  <a name="_core_when_to_call_sql_directly"></a> SQL を直接呼び出すときに

新しいテーブルを作成する (削除) のテーブルを削除、既存のテーブルを変更、インデックスを作成および変更するその他の SQL 機能を実行、[データ ソース (ODBC)](../../data/odbc/data-source-odbc.md)スキーマ、データベースを使用してデータ ソースに直接 SQL ステートメントを発行する必要があります定義言語 (DDL)。 (デザイン時)、テーブルのレコード セットを作成するウィザードを使用する場合は、レコード セットを表すテーブルの列を選択できます。 列またはデータ ソースの別のユーザー テーブルに追加後、プログラムがコンパイルされた後にこれはできません。 データベース クラスは DDL を直接サポートされませんが、実行時に動的に、レコード セットに新しい列をバインドするコードを記述することもできます。 このバインディングを実行する方法については、次を参照してください。[レコード セット。動的に結びつける方法 (ODBC) のデータ列](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)します。

DBMS 自体を使用すると、スキーマ、または DDL の機能を実行できる他のツールを変更します。 レコードは返されません定義済みクエリ (ストアド プロシージャ) の呼び出しなどの SQL ステートメントを送信するための ODBC 関数呼び出しを使用することもできます。

##  <a name="_core_making_direct_sql_function_calls"></a> SQL 関数の呼び出しを直接

使用して SQL の呼び出しを直接実行できる、 [CDatabase クラス](../../mfc/reference/cdatabase-class.md)オブジェクト。 SQL ステートメントの文字列を設定 (通常はで、 `CString`) に渡すと、 [:executesql](../../mfc/reference/cdatabase-class.md#executesql)のメンバー関数、`CDatabase`オブジェクト。 通常、レコードを返す SQL ステートメントを送信する ODBC 関数呼び出しを使用する場合、レコードは無視されます。

## <a name="see-also"></a>関連項目

[SQL](../../data/odbc/sql.md)