---
title: ウィザードで生成されたアクセサーのフィールド ステータスのデータ メンバー
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: a6623cb02f14650d92e4adabed749b0b37725d45
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707557"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>ウィザードで生成されたアクセサーのフィールド ステータスのデータ メンバー

::: moniker range="vs-2019"

ATL OLE DB コンシューマー ウィザードは、Visual Studio 2019 以降では使用できません。 ただし、この機能を手動で追加することは可能です。 詳細については、「[ウィザードを使用しないコンシューマーの作成](creating-a-consumer-without-using-a-wizard.md)」を参照してください。

::: moniker-end

::: moniker range="<=vs-2017"

**ATL OLE DB コンシューマー ウィザード**を使用してコンシューマーを作成する場合、列マップで指定したフィールドごとにユーザー レコード クラスのデータ メンバーが生成されます。 各データ メンバーは `DWORD` 型で、それぞれのフィールドに対応するステータス値が含まれています。

たとえば、データ メンバー *m_OwnerID* に対しては、フィールド ステータスが (*dwOwnerIDStatus*) のデータ メンバーと、フィールド長が (*dwOwnerIDLength*) のデータ メンバーが追加で生成されます。 また、COLUMN_ENTRY_LENGTH_STATUS エントリを含む列マップも生成されます。

これを次のコードに示します。

```cpp
class CAuthorsAccessor
{
public:
   LONG m_AuID;
   TCHAR m_Author[53];
   LONG m_YearBorn;

   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;

   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;

    DEFINE_COMMAND_EX(CAuthorsAccessor, L" \
    SELECT \
        AuID, \
        Author, \
        YearBorn \
        FROM dbo.Authors")

    BEGIN_COLUMN_MAP(CAuthorsAccessor)
       COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)
       COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)
    END_COLUMN_MAP()
...
```

> [!NOTE]
> ユーザー レコード クラスを変更するか、独自のコンシューマーを作成する場合、データ変数は、ステータス変数と長さ変数よりも前に記述する必要があります。

ステータス値はデバッグ目的で使用できます。 **ATL OLE DB コンシューマー ウィザード**で生成したコードで DB_S_ERRORSOCCURRED や DB_E_ERRORSOCCURRED などのコンパイル エラーが生成される場合は、最初にフィールド ステータスのデータ メンバーの現在の値を調べてください。 0 以外の値を持つものが、問題のある列に対応しています。

ステータス値を使用して、特定のフィールドに NULL 値を設定することもできます。 これは、フィールドの値を 0 ではなく NULL として区別する場合に役立ちます。 NULL を有効な値と特殊な値のどちらにするか、また、それをアプリケーションでどのように処理するかは、自由に決めることができます。 OLE DB は、汎用的な NULL 値を指定する適切な手段として、DBSTATUS_S_ISNULL を定義します。 コンシューマーがデータを読み取り、その値が null であった場合、ステータス フィールドが DBSTATUS_S_ISNULL に設定されます。 コンシューマーが NULL 値を設定する場合、そのコンシューマーは、ステータス値を DBSTATUS_S_ISNULL に設定してからプロバイダーを呼び出します。

次に、Oledb.h を開いて DBSTATUSENUM を検索します。 その後、DBSTATUSENUM 列挙値に対して、0 以外のステータスを表す数値を照合できます。 列挙名から問題を特定できない場合は、「[OLE DB プログラマ ガイド](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)」の**データ値のバインド**に関するセクションで**ステータス**に関するトピックを参照してください。 このトピックには、データを取得または設定するときに使用されるステータス値の表が含まれています。 長さの値については、同じセクションの**長さ**に関するトピックを参照してください。

## <a name="retrieving-the-length-or-status-of-a-column"></a>列の長さまたはステータスを取得する

可変長の列の長さ、または列のステータスを取得できます (たとえば、DBSTATUS_S_ISNULL を調べるために)。

- 長さを取得するには、COLUMN_ENTRY_LENGTH マクロを使用します。

- ステータスを取得するには、COLUMN_ENTRY_STATUS マクロを使用します。

- 両方を取得するには、次のように COLUMN_ENTRY_LENGTH_STATUS を使用します。

    ```cpp
    class CProducts
    {
    public:
       char      szName[40];
       long      nNameLength;
       DBSTATUS   nNameStatus;

    BEGIN_COLUMN_MAP(CProducts)
    // Bind the column to CProducts.m_ProductName.
    // nOrdinal is zero-based, so the column number of m_ProductName is 1.
       COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)
    END_COLUMN_MAP()
    };
    ```

- その後、次のように長さまたはステータスにアクセスします。

    ```cpp
    CTable<CAccessor<CProducts >> product;
    CSession session;

    product.Open(session, "Product");

    while (product.MoveNext() == S_OK)
    {
       // Check the product name isn't NULL before tracing it
       if (product.nNameStatus == DBSTATUS_S_OK)
          ATLTRACE("%s is %d characters\n", product.szName, product.nNameLength);
    }
    ```

`CDynamicAccessor` を使用すると、長さとステータスが自動的にバインドされます。 長さとステータスの値を取得するには、メンバー関数 `GetLength` と `GetStatus` を使用します。

::: moniker-end

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレートの操作](../../data/oledb/working-with-ole-db-consumer-templates.md)