---
title: 'レコードセット: 定義済みクエリのクラスの宣言 (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: 9ef95f4a2ebbc1bdf52e5631389f65391ce7cf8f
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707963"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>レコードセット: 定義済みクエリのクラスの宣言 (ODBC)

> [!NOTE] 
> MFC ODBC コンシューマー ウィザードは、Visual Studio 2019 以降では利用できません。 ただし、手動でコンシューマーを作成することはできます。

このトピックの内容は、MFC ODBC クラスに該当します。

このトピックでは、定義済みクエリ (Microsoft SQL Server のように、ストアド プロシージャとも呼ばれます) のレコードセット クラスを作成する方法について説明します。

> [!NOTE]
>  このトピックの内容は、バルク行フェッチが実装されていない `CRecordset` の派生オブジェクトを対象にしています。 バルク行フェッチが実装されている場合も、プロセスはとてもよく似ています。 バルク行フェッチが実装されているレコードセットとそうでないものとの違いを理解するには、「[Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)」 (レコードセット: レコードの一括フェッチ (ODBC)) を参照してください。

一部のデータベース管理システム (DBMS) を使用すると、定義済みクエリを作成し、関数のようにプログラムから呼び出すことができます。 クエリは、名前を持ち、パラメーターを受け取る場合があり、レコードを返す場合があります。 このトピックの手順では、レコードを返す (そして、おそらくはパラメーターを受け取る) 定義済みクエリを呼び出す方法について説明します。

データベース クラスでは、定義済みクエリの更新はサポートされていません。 スナップショット定義済みクエリとダイナセット定義済みクエリの違いは、更新可能かどうかではなく、他のユーザー (または、プログラム内の他のレコードセット) によって行われた変更が自分のレコードセットに表示されるかどうかです。

> [!TIP]
>  レコードを返さない定義済みクエリは、レコードセットがなくても呼び出すことができます。 以下で説明するように SQL ステートメントを準備しますが、それを実行するには `CDatabase` メンバー関数の [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) を呼び出します。

1 つのレコードセット クラスを作成して定義済みクエリの呼び出しを管理できますが、自分で作業しなければならないことがいくつかあります。 この目的専用のクラスの作成は、ウィザードではサポートされていません。

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>定義済みクエリ (ストアド プロシージャ) を呼び出すためのクラスを作成するには

1. **[クラスの追加]** から [MFC ODBC コンシューマー ウィザード](../../mfc/reference/adding-an-mfc-odbc-consumer.md)を使って、クエリによって返される列の最も多くに関係するテーブルのレコードセット クラスを作成します。 これにより始めることができます。

1. クエリによって返されますが、ウィザードで自動的には作成されなかった、すべてのテーブルのすべての列のフィールド データ メンバーを手動で追加します。

   たとえば、クエリによって 3 つの列が返され、それぞれに 2 つの追加テーブルがある場合は、クラスに (適切なデータ型の) 6 つのフィールド データ メンバーを追加します。

1. 追加する各フィールド データ メンバーのデータ型に対応する [RFX](../../data/odbc/record-field-exchange-rfx.md) 関数の呼び出しを、クラスの [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) メンバー関数に手作業で追加します。

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  結果セットで返される列のデータ型と順序がわかっている必要があります。 `DoFieldExchange` 内での RFX 関数の呼び出しの順序は、結果セットの列の順序と一致している必要があります。

1. レコードセット クラスのコンストラクターに、新しいフィールド データ メンバーの初期化を手作業で追加します。

   [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) データ メンバーの初期化の値を増分する必要もあります。 ウィザードで初期化は記述されますが、自動的に追加されるフィールド データ メンバーのものだけです。 次に例を示します。

    ```cpp
    m_nFields += 6;
    ```

   `CLongBinary` やバイト配列など、一部のデータ型はここでは初期化できません。

1. クエリがパラメーターを受け取る場合は、各パラメーターのパラメーター データ メンバー、それぞれに対する RFX 関数呼び出し、およびそれぞれの初期化を追加します。

1. この手順のステップ 4 で追加フィールドに対して `m_nFields` で行ったのと同じように、追加するパラメーターごとに `m_nParams` を増分する必要があります。 詳細については、「[Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)」 (レコードセット: レコードセットのパラメーター化 (ODBC)) を参照してください。

1. 次の形式で SQL ステートメントの文字列を手作業で記述します。

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   **CALL** は ODBC のキーワードであり、**proc-name** はデータ ソースで認識されているクエリの名前です。"?" の項目は実行時にレコードセットに提供するパラメーター値のプレースホルダーです (ある場合)。 次の例では、1 つのパラメーターに対してプレースホルダーを準備しています。

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. レコードセットを開くコードで、レコードセットのパラメーター データ メンバーの値を設定した後、`Open` メンバー関数を呼び出して、*lpszSQL* パラメーターに SQL 文字列を渡します。 またはその代わりに、独自のクラスの `GetDefaultSQL` メンバー関数によって返される文字列を置き換えます。

次の例では、`Delinquent_Accts` という名前の定義済みクエリを呼び出す手順を示します。このクエリは販売地域番号のパラメーターを 1 つ受け取ります。 このクエリでは、3 つの列 `Acct_No`、`L_Name`、`Phone` が返されます。 すべての列は Customers テーブルからのものです。

次のレコードセットでは、クエリから返される列と、実行時に要求される販売地域番号のパラメーターに対する、フィールド データ メンバーが指定されています。

```cpp
class CDelinquents : public CRecordset
{
// Field/Param Data
    LONG m_lAcct_No;
    CString m_strL_Name;
    CString m_strPhone;
    LONG m_lDistParam;
    // ...
};
```

このクラスの宣言は、手作業で追加した `m_lDistParam` メンバーを除き、ウィザードによって記述されたとおりのものです。 他のメンバーはここでは示されていません。

次の例では、`CDelinquents` コンストラクターでのデータ メンバーの初期化を示します。

```cpp
CDelinquents::CDelinquents(CDatabase* pdb)
   : CRecordset(pdb)
{
    // Wizard-generated params:
    m_lAcct_No = 0;
    m_strL_Name = "";
    m_strPhone = "";
    m_nFields = 3;
    // User-defined params:
    m_nParams = 1;
    m_lDistParam = 0;
}
```

[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) と [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) に対する初期化に注意してください。 `m_nFields` はウィザードによる初期化で、`m_nParams` はユーザーによる初期化です。

次の例では、`CDelinquents::DoFieldExchange` での RFX 関数を示します。

```cpp
void CDelinquents::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Long(pFX, "Acct_No", m_lAcct_No);
    RFX_Text(pFX, "L_Name", m_strL_Name);
    RFX_Text(pFX, "Phone", m_strPhone);
    pFX->SetFieldType(CFieldExchange::param);
    RFX_Long(pFX, "Dist_No", m_lDistParam);
}
```

3 つの返される列に対して RFX 関数の呼び出しを行うだけでなく、このコードでは実行時に渡すパラメーターのバインドが管理されています。 パラメーターは、`Dist_No` (地域番号) 列に対応しています。

次の例では、SQL 文字列を設定する方法と、それを使ってレコードセットを開く方法を示します。

```cpp
// Construct a CDelinquents recordset object
CDelinquents rsDel( NULL );
CString strSQL = "{CALL Delinquent_Accts (?)}"
// Specify a parameter value (obtained earlier from the user)
rsDel.m_lDistParam = lDistrict;
// Open the recordset and run the query
if( rsDel.Open( CRecordset::snapshot, strSQL ) )
    // Use the recordset ...
```

このコードでは、スナップショットが作成され、前にユーザーから取得したパラメーターにそれが渡され、定義済みのクエリが呼び出されています。 クエリを実行すると、指定した販売地域のレコードが返されます。 各レコードには、アカウント番号、顧客の姓、および顧客の電話番号の列が含まれています。

> [!TIP]
>  ストアド プロシージャからの戻り値 (出力パラメーター) を処理することが必要な場合があります。 詳細と例については、「[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)」を参照してください。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: レコードセットのクエリの再実行 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[レコードセット: テーブル用のクラスの宣言 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[レコードセット: 結合の実行 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)