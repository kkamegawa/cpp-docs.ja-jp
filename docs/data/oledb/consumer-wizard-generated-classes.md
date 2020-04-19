---
title: コンシューマー ウィザードで生成されたクラス
ms.date: 05/09/2019
helpviewer_keywords:
- user record classes in OLE DB consumer
ms.assetid: dba0538f-2afe-4354-8cbb-f202ea8ade5a
ms.openlocfilehash: 3442ff484876aec9b2cd3fa93e95c4d503649ee9
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707750"
---
# <a name="consumer-wizard-generated-classes"></a>コンシューマー ウィザードで生成されたクラス


::: moniker range="vs-2019"

ATL OLE DB コンシューマー ウィザードは、Visual Studio 2019 以降では使用できません。 ただし、この機能を手動で追加することは可能です。

::: moniker-end

::: moniker range="<=vs-2017"

**ATL OLE DB コンシューマー ウィザード**を使用してコンシューマーを生成する場合、OLE DB テンプレートと OLE DB 属性のどちらかを使用するよう選択できます。 どちらの場合も、ウィザードによってコマンド クラスとユーザー レコード クラスが生成されます。 コマンド クラスには、ウィザードで指定したデータ ソースと行セットを開くためのコードが含まれています。 ユーザー レコード クラスには、選択したデータベース テーブルの列マップが含まれています。 ただし、生成されるコードはそれぞれ異なります。

- テンプレート コンシューマーを選択した場合、ウィザードはコマンド クラスとユーザー レコード クラスを生成します。 コマンド クラスは、ウィザードの **[クラス]** ボックスに入力した名前 (`CProducts` など) になり、ユーザー レコード クラスは、"*ClassName*Accessor" 形式の名前 (`CProductsAccessor` など) になります。 どちらのクラスも、コンシューマーのヘッダー ファイルに格納されます。

- 属性コンシューマーを選択した場合は、ユーザー レコード クラスのフォームは、"_*ClassName*Accessor" の名前で挿入されます。 つまり、テキスト エディターではコマンド クラスの表示のみが可能になり、ユーザー レコード クラスは挿入されたコードとして表示されます。 挿入されたコードを表示する方法については、「 [挿入されたコードのデバッグ](/visualstudio/debugger/how-to-debug-injected-code)」を参照してください。

次の例では、`Northwind` データベースの `Products` テーブルで作成されたコマンド クラスを使用して、コマンド クラスとユーザー レコード クラスに対してウィザードで生成されたコンシューマー コードの使用例を示します。

## <a name="templated-user-record-classes"></a>テンプレート化されたユーザー レコード クラス

OLE DB 属性ではなく、OLE DB テンプレートを使用して OLE DB コンシューマーを作成する場合、ウィザードは、このセクションで説明したコードを生成します。

### <a name="column-data-members"></a>列データ メンバー

ユーザー レコード クラスの最初の部分には、データ メンバーの宣言とそれぞれのデータ バインド列のステータスや長さデータ メンバーが含まれます。 これらのデータ メンバーについては、「 [ウィザードで生成されたアクセサーのフィールド ステータスのデータ メンバー](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)」を参照してください。

> [!NOTE]
> ユーザー レコード クラスを変更するか、独自のコンシューマーを作成する場合、データ変数は、ステータス変数と長さ変数よりも前に記述する必要があります。

> [!NOTE]
> ATL OLE DB コンシューマー ウィザードでは、`DB_NUMERIC` 型を使用して数値データ型をバインドします。 これまでは、`DBTYPE_VARNUMERIC` (`DB_VARNUMERIC` 型で説明される形式については、Oledb.h を参照) が使用されていました。 コンシューマーの作成にウィザードを使用しない場合は、`DB_NUMERIC` を使用することをお勧めします。

```cpp
// Products.H : Declaration of the CProducts class

class CProductsAccessor
{
public:
   // Column data members:
   LONG m_ProductID;
   TCHAR m_ProductName[41];
   LONG m_SupplierID;
   LONG m_CategoryID;
   TCHAR m_QuantityPerUnit[21];
   CURRENCY m_UnitPrice;
   SHORT m_UnitsInStock;
   SHORT m_UnitsOnOrder;
   SHORT m_ReorderLevel;
   VARIANT_BOOL m_Discontinued;

   // Column status data members:
   DBSTATUS m_dwProductIDStatus;
   DBSTATUS m_dwProductNameStatus;
   DBSTATUS m_dwSupplierIDStatus;
   DBSTATUS m_dwCategoryIDStatus;
   DBSTATUS m_dwQuantityPerUnitStatus;
   DBSTATUS m_dwUnitPriceStatus;
   DBSTATUS m_dwUnitsInStockStatus;
   DBSTATUS m_dwUnitsOnOrderStatus;
   DBSTATUS m_dwReorderLevelStatus;
   DBSTATUS m_dwDiscontinuedStatus;

   // Column length data members:
   DBLENGTH m_dwProductIDLength;
   DBLENGTH m_dwProductNameLength;
   DBLENGTH m_dwSupplierIDLength;
   DBLENGTH m_dwCategoryIDLength;
   DBLENGTH m_dwQuantityPerUnitLength;
   DBLENGTH m_dwUnitPriceLength;
   DBLENGTH m_dwUnitsInStockLength;
   DBLENGTH m_dwUnitsOnOrderLength;
   DBLENGTH m_dwReorderLevelLength;
   DBLENGTH m_dwDiscontinuedLength;
```

### <a name="rowset-properties"></a>行セット プロパティ

次に、ウィザードは行セット プロパティを設定します。 ATL OLE DB コンシューマー ウィザードで **[変更]** 、 **[挿入]** 、または **[削除]** を選択した場合、適切なプロパティがここで設定されます (DBPROP_IRowsetChange は常に設定され、それぞれの場合に DBPROPVAL_UP_CHANGE、DBPROPVAL_UP_INSERT、DBPROPVAL_UP_DELETE のいずれかが設定されます)。

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="command-or-table-class"></a>コマンドまたはテーブル クラス

コマンド クラスを指定すると、ウィザードはコマンド クラスを宣言します。テンプレート化されたコードの場合は、コマンドは以下のようになります。

```cpp
DEFINE_COMMAND_EX(CProductsAccessor, L" \
SELECT \
   ProductID, \
   ProductName, \
   SupplierID, \
   CategoryID, \
   QuantityPerUnit, \
   UnitPrice, \
   UnitsInStock, \
   UnitsOnOrder, \
   ReorderLevel, \
   Discontinued \
   FROM dbo.Products")
```

### <a name="column-map"></a>列マップ

ウィザードでは、列のバインドまたは列のマップが生成されます。 一部のプロバイダーで発生する問題を解決するため、下記のコードでの列のバインドの順序は、プロバイダーからの報告とは異なる場合があります。

```cpp
   BEGIN_COLUMN_MAP(CProductsAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_SupplierID, m_dwSupplierIDLength, m_dwSupplierIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(4, m_CategoryID, m_dwCategoryIDLength, m_dwCategoryIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(5, m_QuantityPerUnit, m_dwQuantityPerUnitLength, m_dwQuantityPerUnitStatus)
      _COLUMN_ENTRY_CODE(6, DBTYPE_CY, _SIZE_TYPE(m_UnitPrice), 0, 0, offsetbuf(m_UnitPrice), offsetbuf(m_dwUnitPriceLength), offsetbuf(m_dwUnitPriceStatus))
      COLUMN_ENTRY_LENGTH_STATUS(7, m_UnitsInStock, m_dwUnitsInStockLength, m_dwUnitsInStockStatus)
      COLUMN_ENTRY_LENGTH_STATUS(8, m_UnitsOnOrder, m_dwUnitsOnOrderLength, m_dwUnitsOnOrderStatus)
      COLUMN_ENTRY_LENGTH_STATUS(9, m_ReorderLevel, m_dwReorderLevelLength, m_dwReorderLevelStatus)
      _COLUMN_ENTRY_CODE(10, DBTYPE_BOOL, _SIZE_TYPE(m_Discontinued), 0, 0, offsetbuf(m_Discontinued), offsetbuf(m_dwDiscontinuedLength), offsetbuf(m_dwDiscontinuedStatus))
   END_COLUMN_MAP()
};
```

### <a name="class-declaration"></a>クラス宣言

最後に、ウィザードでは、次のようなコマンド クラス宣言が生成されます。

```cpp
class CProducts : public CCommand<CAccessor<CProductsAccessor>>
```

## <a name="attribute-injected-user-record-classes"></a>属性が挿入されたユーザー レコード クラス

データベース属性 ([db_command](../../windows/db-command.md) または [db_table](../../windows/db-table.md)) を使用して OLE DB コンシューマーを作成する場合、この属性によって "_*ClassName*Accessor" の形式の名前でユーザー レコード クラスが挿入されます。 たとえば、コマンド クラスに `COrders`と名前を付けると、ユーザー レコード クラスは `_COrdersAccessor`となります。 ユーザー レコード クラスは**クラス ビュー**に表示されますが、ダブルクリックすると、コマンドまたはヘッダー ファイルのテーブル クラスに移動します。 このような場合は、属性が挿入されたコードを表示すると、ユーザー レコード クラスの実際の宣言のみが表示されます。

属性付きコンシューマーでメソッドを追加またはオーバーライドすると、問題が発生することがあります。 たとえば、 `_COrdersAccessor` コンストラクターは `COrders` 宣言に追加できますが、実際には、このコンストラクターは挿入された `COrdersAccessor` クラスに追加されます。 このようなコンストラクターは列やパラメーターを初期化できますが、`COrdersAccessor` オブジェクトを直接インスタンス化できないため、この方法でコンストラクターのコピーを作成することはできません。 `COrders` クラス上で直接コンストラクター (またはその他のメソッド) が必要な場合は、`COrders` から派生した新しいクラスを定義し、そこに必要なメソッドを追加することをお勧めします。

次の例では、ウィザードがクラス `COrders` の宣言を生成していますが、ユーザー レコード クラス `COrdersAccessor` は属性によって挿入されるため表示されません。

```cpp
#define _ATL_ATTRIBUTES
#include <atlbase.h>
#include <atldbcli.h>
[
   db_source(L"your connection string"),
   db_command(L"Select ShipName from Orders;")
]
class COrders
{
public:

   // COrders()            // incorrect constructor name
   _COrdersAccessor()      // correct constructor name
   {
   }
      [db_column(1) ] TCHAR m_ShipName[41];
   };
```

挿入されたコマンド クラス宣言は次のようになります。

```cpp
class CProducts : public CCommand<CAccessor<_CProductsAccessor>>
```

挿入されたコードのほとんどは、テンプレート バージョンと同じか類似するものです。 主な相違点は、「 [コンシューマー ウィザード生成メソッド](../../data/oledb/consumer-wizard-generated-methods.md)」で説明されている挿入されたメソッドの部分です。

挿入されたコードを表示する方法については、「 [挿入されたコードのデバッグ](/visualstudio/debugger/how-to-debug-injected-code)」を参照してください。

::: moniker-end

## <a name="see-also"></a>関連項目

[ウィザードを使用した OLE DB コンシューマーの作成](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)