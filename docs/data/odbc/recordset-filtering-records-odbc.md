---
title: レコード セット:レコードのフィルター処理 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
ms.openlocfilehash: 050524df840be28d661da89d04b685a44238f88c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397862"
---
# <a name="recordset-filtering-records-odbc"></a>レコード セット:レコードのフィルター処理 (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

このトピックでは、使用可能なレコードの特定のサブセットのみを選択するように、レコード セットをフィルター処理する方法について説明します。 たとえば、MATH101 などの特定のコースのクラスのセクションのみを選択します。 フィルターは、SQL の内容で定義された検索条件**WHERE**句。 フレームワークは、レコード セットの SQL ステートメントを追加するとき、**WHERE**句は、選択範囲を制限します。

呼び出す前に、オブジェクトを構築した後は、レコード セット オブジェクトのフィルターを確立する必要があります、`Open`メンバー関数 (または呼び出す前に、`Requery`メンバー関数の既存のレコード セット オブジェクト`Open`メンバー関数には、既に呼び出されています)。

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>レコード セット オブジェクトのフィルターを指定するには

1. 新しいレコード セット オブジェクトを作成する (またはを呼び出す準備`Requery`既存のオブジェクト)。

1. オブジェクトの値を設定[か](../../mfc/reference/crecordset-class.md#m_strfilter)データ メンバー。

   フィルターは、SQL の**WHERE**句の内容を含み、キーワードの**WHERE**を含まない、NULL で終わる文字列です。 たとえば、次のように使用します。

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  上記の 1 つの引用符リテラル文字列"MATH101"が表示されます。 ODBC の仕様では、単一引用符は、文字の文字列リテラルを表すために使用されます。 このような状況で、DBMS の引用符の要件については、ODBC ドライバーのマニュアルを確認します。 この構文は説明もさらに、このトピックの最後の方です。

1. 並べ替え順序、ロックのモード、またはパラメーターなどの必要なその他のオプションを設定します。 パラメーターを指定すると、特に便利です。 フィルターをパラメーター化の詳細については、次を参照してください。[レコード セット。レコード セット (ODBC) をパラメーター化](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)します。

1. 呼び出す`Open`に新しいオブジェクト (または`Requery`既に開かれているオブジェクト)。

> [!TIP]
>  パラメーターを使用して、フィルターでは、レコードを取得するための最も効率的な方法があります。

> [!TIP]
>  レコード セットのフィルター[への参加](../../data/odbc/recordset-performing-a-join-odbc.md)テーブルを使用するため、[パラメーター](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)情報を取得または実行時に計算に基づいて。

レコード セットは、指定した検索条件を満たすレコードだけを選択します。 たとえば、コースのフィルターを指定する前に説明した (変数と仮定すると`strCourseID`現在に設定されて、たとえば、"MATH101")、次の操作を行います。

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

レコード セットには、MATH101 のクラスのセクションではすべてのレコードが含まれています。

フィルター文字列を文字列変数を使用して、上記の例で設定した方法に注意してください。 これは、一般的な使用方法です。 コース ID のリテラル値 100 を指定するとしますが、 次のコードでは、リテラル値で正しくフィルター文字列を設定する方法を示します。

```
m_strFilter = "StudentID = '100'";   // correct
```

単一引用符文字の使用に注意してください。フィルター文字列を直接設定する場合、フィルター文字列は**いない**:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

上記の引用符、ODBC 仕様に準拠していますが、一部の Dbms が他の引用符文字を必要があります。 詳細については、次を参照してください[SQL:。レコード セットの SQL ステートメント (ODBC) のカスタマイズ](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)します。

> [!NOTE]
>  独自の SQL 文字列を渡すことによって、レコード セットの既定の SQL 文字列を上書きする場合`Open`、カスタム文字列がある場合にフィルターを設定しないでください、**WHERE**句。 既定の SQL をオーバーライドする方法についての詳細については、次を参照してください[SQL:。レコード セットの SQL ステートメント (ODBC) のカスタマイズ](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)します。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[レコードセット: レコードの並べ替え (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[レコードセット: レコードセットでのレコード選択のしくみ (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[レコードセット: レコードセットでのレコード更新のしくみ (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[レコードセット: レコードのロック (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
