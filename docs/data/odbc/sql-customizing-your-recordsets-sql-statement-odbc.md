---
title: SQL:レコード セットの SQL ステートメント (ODBC) のカスタマイズ
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
ms.openlocfilehash: eabaab019ee94b0c5617573c534d920ec710e9b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329934"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL:レコード セットの SQL ステートメント (ODBC) のカスタマイズ

このトピックでは、次の内容について説明します。

- フレームワークが SQL ステートメントを作成する方法

- SQL ステートメントを上書きする方法

> [!NOTE]
>  この情報は、MFC ODBC クラスに適用されます。 MFC DAO クラスを使用する場合は、"比較の Microsoft Jet データベース エンジン SQL と ANSI SQL"DAO ヘルプのトピックを参照してください。

## <a name="sql-statement-construction"></a>SQL ステートメントの作成

レコード セットが主に、SQL レコード選択**選択**ステートメント。 オーバーライド元のバージョンのウィザードを使用して、クラスを宣言するときに書き込む、`GetDefaultSQL`次のようなメンバー関数 (レコード セット クラスと呼ばれる`CAuthors`)。

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

既定では、この上書きは、ウィザードで指定したテーブル名を返します。 例では、テーブル名は「作成者」にします。 レコード セットの後で呼び出す`Open`メンバー関数は、`Open`最終を構築します**選択**形式のステートメント。

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

場所`table-name`を呼び出すことによって取得`GetDefaultSQL`と`rfx-field-list`では、RFX 関数の呼び出しから取得されます`DoFieldExchange`します。 これは、するため、**選択**ステートメントしない限りオーバーライド元のバージョンで、実行時に既定のステートメントをパラメーターやフィルターを変更することもできますが。

> [!NOTE]
>  スペースが含まれています (または含めたり) を列名を指定する場合は、角かっこで名前を囲む必要があります。 たとえば、名前「名」には、「[姓]」があります。

既定値をオーバーライドする**選択**ステートメントでは、文字列、完全なパス**選択**ステートメントを呼び出すとき`Open`します。 独自の既定の文字列を作成する代わりに、レコード セットを指定する文字列を使用します。 置換ステートメントが含まれている場合、**場所**句内のフィルターを指定しない`m_strFilter`ステートメントをフィルター処理し、必要がありますので、2 つ。 同様に、置換、ステートメントが含まれている場合、 **ORDER BY**句での並べ替えを指定しない`m_strSort`ステートメントで並べ替える 2 つがあるないようにします。

> [!NOTE]
>  フィルター (または、SQL ステートメントの他の部分) でリテラル文字列を使用する場合は、"を"引用する必要があります (指定された区切り記号で囲みます) このような文字列を DBMS に固有のリテラル プレフィックスを持つとリテラル サフィックス文字 (または文字)。

DBMS によって外部結合などの操作の特別な構文の要件を生じる可能性があります。 ODBC 関数を使用して、dbms、ドライバーからこの情報を取得します。 たとえば、`::SQLGetTypeInfo`特定のデータ型の場合など`SQL_VARCHAR`LITERAL_PREFIX と LITERAL_SUFFIX 文字を要求するには、します。 データベースに依存しないコードを記述する場合は、次を参照してください[付録 c:。SQL 文法](/sql/odbc/reference/appendixes/appendix-c-sql-grammar)で、 [ODBC プログラマ リファレンス](/sql/odbc/reference/odbc-programmer-s-reference)構文の詳細についてはします。

レコード セット オブジェクトは、カスタム SQL ステートメントを指定しないと、レコードを選択するために使用する SQL ステートメントを構築します。 主に渡す値に依存これを行う方法、 *lpszSQL*のパラメーター、`Open`メンバー関数。

SQL の一般的な形式**選択**ステートメントは。

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

追加する 1 つの方法、 **DISTINCT**レコード セットの SQL ステートメントにキーワードは、の最初の RFX 関数の呼び出しで、キーワードを埋め込む`DoFieldExchange`します。 例えば:

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
>  読み取り専用で開かれたレコード セットでのみ、この手法を使用します。

## <a name="overriding-the-sql-statement"></a>SQL ステートメントをオーバーライドします。

次の表に、さまざまな可能性、 *lpszSQL*パラメーター`Open`します。 次の表に、テーブル内のケースを説明します。

**LpszSQL パラメーターと結果の SQL 文字列**

|Case|LpszSQL を渡します|結果の SELECT ステートメント|
|----------|------------------------------|------------------------------------|
|1|NULL|**SELECT** *rfx-field-list* **FROM** *table-name*<br /><br /> `CRecordset::Open` 呼び出し`GetDefaultSQL`テーブル名を取得します。 結果の文字列がいずれかの内容に合わせてケース 2 ~ 5、`GetDefaultSQL`を返します。|
|2|テーブル名|**SELECT** *rfx-field-list* **FROM** *table-name*<br /><br /> フィールド一覧の RFX ステートメントから取得されます`DoFieldExchange`します。 場合`m_strFilter`と`m_strSort`空ではない、追加、**場所**や**ORDER BY**句。|
|3 \*|完全な**選択**ステートメントがない、**場所**または**ORDER BY**句|渡されました。 場合`m_strFilter`と`m_strSort`空ではない、追加、**場所**や**ORDER BY**句。|
|4 \*|完全な**選択**ステートメントを**場所**や**ORDER BY**句|渡されました。 `m_strFilter` や`m_strSort`する必要があります空、またはこの 2 つのフィルターや並べ替えステートメントが生成されます。|
|5 \*|ストアド プロシージャへの呼び出し|渡されました。|

\* `m_nFields` 指定された列の数以下である必要があります、**選択**ステートメント。 指定された各列のデータ型、**選択**ステートメントには、rfx 関数の対応する出力列のデータ型と同じである必要があります。

### <a name="case-1---lpszsql--null"></a>ケース 1 lpszSQL = NULL

レコード セットの選択が何に依存`GetDefaultSQL`時に返す`CRecordset::Open`は関数を呼び出します。 2 ~ 5 の場合は、可能性のある文字列について説明します。

### <a name="case-2---lpszsql--a-table-name"></a>ケース 2 テーブル名を =

レコード セットでは、レコード フィールド エクス (チェンジ RFX) を使用して、レコード セット クラスのオーバーライドで関数を呼び出す、RFX で提供される列名から列リストをビルドする`DoFieldExchange`します。 この場合に、レコード セット クラスを宣言するウィザードを使用して (ウィザードで指定した同じテーブル名を渡す) が提供できる 1 の場合と同じ結果が。 クラスを作成するウィザードを使用しない場合、SQL ステートメントを作成する最も簡単な方法は、ケース 2。

次の例では、MFC データベース アプリケーションからレコードを選択する SQL ステートメントを作成します。 フレームワークを呼び出すと、`GetDefaultSQL`メンバー関数は、関数が、テーブルの名前を返します`SECTION`します。

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

SQL の列の名前を取得する**選択**ステートメントでは、フレームワークによって、`DoFieldExchange`メンバー関数。

```cpp
void CEnrollSet::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Text(pFX, "CourseID", m_strCourseID);
    RFX_Text(pFX, "InstructorID", m_strInstructorID);
    RFX_Text(pFX, "RoomNo", m_strRoomNo);
    RFX_Text(pFX, "Schedule", m_strSchedule);
    RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

完了すると、SQL ステートメントがようになります。

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>ケース 3 = SELECT ステートメントから/

列の一覧は、RFX を自動的に頼ることがなく手動でを指定します。 この場合に実行する場合があります。

- 指定する、 **DISTINCT**キーワードの後**選択**します。

   内に列挙されている、列の一覧を列名と同じ順序で型が一致`DoFieldExchange`します。

- 手動で ODBC 関数を使用して列の値を取得する理由がある`::SQLGetData`RFX をバインドし、列を取得するのに頼ることがなく。

   など、アプリケーションの配布された後は、データベース テーブルに、アプリケーションの顧客が追加された新しい列に対応することができます。 ウィザードを使用して、クラスを宣言したときに認識されたありませんこれら追加のフィールド データ メンバーを追加する必要があります。

   内に列挙されている、列の一覧を列名と同じ順序で型が一致`DoFieldExchange`、その後に、手動でバインドされた列の名前。 詳細については、次を参照してください。[レコード セット。動的に結びつける方法 (ODBC) のデータ列](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)します。

- 複数のテーブルを指定することでテーブルを結合する、 **FROM**句。

   情報と例では、次を参照してください。[レコード セット。結合 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)します。

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>ケース 4 = 選択/から Plus、または ORDER BY

すべてのものを指定する: 列の一覧 (で rfx 関数の呼び出しに基づく`DoFieldExchange`)、テーブルのリストとの内容を**場所**や、 **ORDER BY**句。 指定した場合、**場所**や**ORDER BY**句、この方法は使用しないでください`m_strFilter`や`m_strSort`します。

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>ケース 5 = ストアド プロシージャ コール

記述する必要があります (Microsoft SQL Server データベースでストアド プロシージャ) などの定義済みのクエリを呼び出す必要がある場合、**呼び出す**に渡す文字列内のステートメント*lpszSQL*します。 ウィザードは、定義済みのクエリを呼び出すためのレコード セット クラスの宣言をサポートしていません。 定義済みのすべてのクエリでは、レコードが返されます。

定義済みのクエリがレコードを返さない場合は使用できます、`CDatabase`メンバー関数は`ExecuteSQL`直接します。 レコードが返されますが、定義済みクエリの記述する必要ありますも手動で呼び出し、RFX`DoFieldExchange`プロシージャは、列を返します。 Rfx 関数の呼び出しは、同じ順序であるし、定義済みのクエリと同じ型を返す必要があります。 詳細については、次を参照してください。[レコード セット。クラスの定義済みクエリ (ODBC) 宣言](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)します。

## <a name="see-also"></a>関連項目

[SQL: SQL と C++ のデータ型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL: SQL の直接呼び出し (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
