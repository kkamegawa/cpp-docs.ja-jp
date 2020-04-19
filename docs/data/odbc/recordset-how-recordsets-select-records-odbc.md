---
title: 'レコードセット: レコードセットでのレコード選択のしくみ (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
ms.openlocfilehash: 41542e3e11d304bd9ad8b81c0a1b9c6504e156a7
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707894"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>レコードセット: レコードセットでのレコード選択のしくみ (ODBC)

> [!NOTE] 
> MFC ODBC コンシューマー ウィザードは、Visual Studio 2019 以降はご利用いただけなくなります。 引き続き、コンシューマーを手動で作成することはできます。

このトピックの内容は、MFC ODBC クラスに該当します。

このトピックでは、次の内容について説明します。

- [ロールとレコード選択のオプション](#_core_your_options_in_selecting_records)。

- [レコードセットでの SQL ステートメントの作成およびレコードの選択方法](#_core_how_a_recordset_constructs_its_sql_statement)。

- [選択をカスタマイズするためにできること](#_core_customizing_the_selection)。

レコードセットでは、SQL ステートメントを ODBC ドライバーに送信することによって、そのドライバーを介してデータ ソースからレコードを選択します。 送信される SQL は、レコードセット クラスをどのように設計して開くかによって異なります。

##  <a name="_core_your_options_in_selecting_records"></a>レコード選択のオプション

次の表に、レコードを選択する際のオプションを示します。

### <a name="how-and-when-you-can-affect-a-recordset"></a>レコードセットに影響を与えることができる方法とタイミング

|次のとき|できます|
|--------------|-------------|
|**クラスの追加**ウィザードでレコードセット クラスを宣言する|どのテーブルから選択するかを指定します。<br /><br /> どの列を含めるかを指定します。<br /><br /> 「[MFC ODBC コンシューマーの追加](../../mfc/reference/adding-an-mfc-odbc-consumer.md)」を参照してください。|
|レコードセット クラスの実装を完了する|`OnSetOptions` (アドバンスト) などのメンバー関数をオーバーライドして、アプリケーション固有のオプションを設定するか、既定値を変更します。 パラメーター化されたレコードセットが必要な場合は、パラメーター データ メンバーを指定します。|
|レコードセット オブジェクトを作成する (`Open` を呼び出す前に)|レコードをフィルターする **WHERE** 句で使用する検索条件 (場合によっては複合) を指定します。 「[レコードセット: レコードのフィルター処理 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)」を参照してください。<br /><br /> レコードを並べ替える **ORDER BY** 句で使用するための並べ替え順序を指定します。 「[レコードセット: レコードの並べ替え (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)」を参照してください。<br /><br /> クラスに追加した任意のパラメーターのパラメーター値を指定します。 「[レコードセット: レコードセットのパラメーター化 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)」を参照してください。|

|`Open` を呼び出してレコードセットのクエリを実行する|ウィザードによって設定された既定の SQL 文字列を置き換えるカスタム SQL 文字列を指定します。 "*クラス ライブラリ リファレンス*" の [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) と、「[SQL: レコードセットの SQL ステートメントのカスタマイズ (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)」を参照してください。|

|`Requery` を呼び出し、データ ソース上の最新の値を持つレコードセットの再クエリを実行する|新しいパラメーター、フィルター、または並べ替えを指定します。 「[レコードセット: レコードセットのクエリの再実行 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)」を参照してください。|

##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a>レコードセットでの SQL ステートメントの作成方法

レコードセット オブジェクトの [Open](../../mfc/reference/crecordset-class.md#open) メンバー関数を呼び出すとき、`Open` によって、以下の要素の一部またはすべてを使用して SQL ステートメントが作成されます。

- `Open` に渡された *lpszSQL* パラメーター。 このパラメーター (NULL でない場合) には、カスタム SQL 文字列またはその一部分を指定します。 フレームワークにより、文字列が解析されます。 文字列が SQL の **SELECT** ステートメントまたは ODBC の **CALL** ステートメントである場合、文字列はフレームワークによってレコードセットの SQL ステートメントとして使用されます。 文字列が "SELECT" または "{CALL" で始まっていない場合、フレームワークでは提供されたものを使用して SQL **FROM** 句が作成されます。

- [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) によって返された文字列。 これは、既定ではウィザードでレコードセット用に指定したテーブルの名前ですが、関数から返されたものを変更できます。 フレームワークによって `GetDefaultSQL` が呼び出されます。文字列が "SELECT" または "{CALL" で始まっていない場合はテーブル名と見なされ、それが SQL 文字列を作成するために使用されます。


- テーブルの特定の列にバインドされる、レコードセットのフィールド データ メンバー。 フレームワークによってレコード列がこれらのメンバーのアドレスにバインドされ、それらがバッファーとして使用されます。 フレームワークによって、レコードセットの [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) または [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) メンバー関数での [RFX](../../data/odbc/record-field-exchange-using-rfx.md) または Bulk RFX 関数呼び出しからのテーブル列に対する、フィールド データ メンバーの相関関係が決定されます。

- [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) データ メンバーに含まれている、レコードセット用の[フィルター](../../data/odbc/recordset-filtering-records-odbc.md) (もしあれば)。 フレームワークでは、この文字列を使用して、SQL の **WHERE** 句が作成されます。

- [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) データ メンバーに含まれている、レコードセットの[並べ替え](../../data/odbc/recordset-sorting-records-odbc.md)順序 (もしあれば)。 フレームワークでは、この文字列を使用して、SQL の **ORDER BY** 句が作成されます。

   > [!TIP]
   > SQL の **GROUP BY** 句 (および場合によって **HAVING** 句) を使用するには、フィルター文字列の末尾に句を追加します。

- クラスに指定する任意の[パラメーター データ メンバー](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)の値。 `Open` または `Requery` を呼び出す直前にパラメーター値を設定します。 パラメーター値はフレームワークによって、SQL 文字列内の "?" プレースホルダーにバインドされます。 コンパイル時に、プレースホルダーを含む文字列を指定します。 実行時に、渡したパラメーター値に基づいてフレームワークによって詳細が入力されます。

`Open` によって、これらの要素から SQL の **SELECT** ステートメントが作成されます。 フレームワークによって要素がどのように使用されるかについて詳しくは、「[選択のカスタマイズ](#_core_customizing_the_selection)」を参照してください。

ステートメント作成後、`Open` から ODBC ドライバー マネージャー (およびメモリ内にある場合は ODBC カーソル ライブラリ) に SQL が送信され、ODBC ドライバー マネージャーによって SQL は特定の DBMS の ODBC ドライバーに送信されます。 ドライバーと DBMS との通信によってデータ ソース上で選択が実行され、最初のレコードがフェッチされます。 フレームワークによってレコードがレコードセットのフィールド データ メンバーに読み込まれます。

これらの手法の組み合わせを使用して、[テーブル](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)を開き、複数のテーブルの[結合](../../data/odbc/recordset-performing-a-join-odbc.md)に基づいてクエリを作成できます。 追加のカスタマイズにより、[定義済みクエリ](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (ストアド プロシージャ) を呼び出し、設計時点で不明なテーブル列を選択して、それらをレコードセット フィールドに[バインド](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)することや、他のほとんどのデータ アクセス タスクを実行することができます。 レコードセットをカスタマイズしても達成できないタスクは、[ODBC API 関数を呼び出す](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)か、[CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)を使用して SQL ステートメントを直接実行することで達成できます。

##  <a name="_core_customizing_the_selection"></a>選択のカスタマイズ

レコードセットの選択をカスタマイズするために、フィルター、並べ替え順序、またはパラメーターを指定すること以外に、次の操作を実行できます。

- レコードセットに対して [ Open](../../mfc/reference/crecordset-class.md#open) を呼び出すときに、*lpszSQL* でカスタム SQL 文字列を渡します。 *lpsqSQL* で渡したものはすべて、[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) メンバー関数から返されるものよりも優先されます。

   詳細については、「[SQL: レコードセットの SQL ステートメントのカスタマイズ (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)」を参照してください。`Open` に渡すことができる SQL ステートメント (または部分ステートメント) の種類と、それらを使用してフレームワークによって行われることについて説明しています。

    > [!NOTE]
    >  渡したカスタム文字列が "SELECT" または "{CALL" で始まっていない場合、MFC ではそれにテーブル名が含まれていると見なされます。 これは、次の項目にも適用されます。

- ウィザードによってレコードセットの `GetDefaultSQL` メンバー関数に書き込まれる文字列を変更します。 返されるものを変更するには関数のコードを編集します。 既定では、ウィザードによって、1 つのテーブル名を返す `GetDefaultSQL` 関数が作成されます。

   *lpszSQL* パラメーターで `Open` に渡すことができる任意の項目を `GetDefaultSQL` から返すことができます。 *lpszSQL* でカスタム SQL 文字列を渡さなかった場合、`GetDefaultSQL` から返された文字列がフレームワークによって使用されます。 `GetDefaultSQL` からは少なくとも 1 つのテーブル名が返される必要があります。 しかし、複数のテーブル名、完全な **SELECT** ステートメント、ODBC の **CALL** ステートメントなどが返されるようにすることができます。 *lpszSQL* に渡すことができる (または `GetDefaultSQL` から返すことができる) ものの一覧を確認するには、「[SQL: レコードセットの SQL ステートメントのカスタマイズ (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)」を参照してください。

   2 つ以上のテーブルの結合を実行している場合は、`GetDefaultSQL` を書き換えて、SQL の **FROM** 句で使用されるテーブルのリストをカスタマイズします。 詳細については、「[レコードセット: 結合の実行 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)」を参照してください。


- 実行時にデータ ソースのスキーマについて取得した情報などに基づいて、追加のフィールド データ メンバーを手動でバインドします。 フィールド データ メンバーは、レコードセット クラス、フィールド データ メンバーに対する [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) または [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) メンバー関数への [RFX](../../data/odbc/record-field-exchange-using-rfx.md) または Bulk RFX 関数呼び出し、クラス コンストラクター内のデータ メンバーの初期化に追加できます。 詳細については、「[レコードセット: データ列の動的なバインド (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)」を参照してください。

- `OnSetOptions` などのレコードセット メンバー関数をオーバーライドして、アプリケーション固有のオプションを設定するか、既定値をオーバーライドします。

複雑な SQL ステートメントをレコードセットのベースにする場合は、これらのカスタマイズ手法のいくつかの組み合わせを使用する必要があります。 たとえば、レコードセットによって直接サポートされていない SQL の句とキーワードを使用する場合や、複数のテーブを結合する場合などです。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: レコードセットでのレコード更新のしくみ (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[ODBC の基礎](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[レコードセット: レコードのロック (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)