---
title: 更新 (行セットを)
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
ms.openlocfilehash: e0ee5cf97170cd9293abcb9039771f8fe23962aa
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525300"
---
# <a name="updating-rowsets"></a>更新 (行セットを)

データベースの基本の操作は、データ ストアの更新、つまりデータの書き込みです。 OLE DB の更新機構は単純です。コンシューマー アプリケーションは、バインドされたデータ メンバーの値を設定し、これらの値を行セットに書き込みます。その後、コンシューマーはプロバイダーにデータ ストアの更新を要求します。

コンシューマーが行セット データに対して実行できる更新の種類は、行内の列値の設定、行の挿入、行の削除です。 これらの操作を実行するために、OLE DB テンプレート クラスの [CRowset](../../data/oledb/crowset-class.md) は、[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) インターフェイスを実装し、次のインターフェイス メソッドをオーバーライドします。

- [SetData](../../data/oledb/crowset-setdata.md) は行セットの行の列値を変更します。これは SQL の UPDATE コマンドに相当します。

- [Insert](../../data/oledb/crowset-insert.md) は行を行セットに挿入します。これは SQL の INSERT コマンドに相当します。

- [Delete](../../data/oledb/crowset-delete.md) は行を行セットから削除します。これは SQL の DELETE コマンドに相当します。

## <a name="supporting-update-operations"></a>更新操作のサポート

> [!NOTE]
> ATL OLE DB コンシューマー ウィザードは、Visual Studio 2019 以降では使用できません。 ただし、この機能を手動で追加することは可能です。 詳細については、「[ウィザードを使用しないコンシューマーの作成](creating-a-consumer-without-using-a-wizard.md)」をご覧ください。

**ATL OLE DB コンシューマー ウィザード**を使用してコンシューマーを作成する場合、 **[変更]** 、 **[挿入]** 、 **[削除]** の 3 つのチェック ボックスのうちの 1 つ以上をオンにすれば、更新操作をサポートできます。 これらのオプションを選択すると、ウィザードによってコードが適宜変更され、選んだ変更の種類がサポートされます。 ただし、ウィザードを使用しない場合、更新をサポートするには次の行セット プロパティを `VARIANT_TRUE` に設定する必要があります。

- `DBPROPVAL_UP_CHANGE` では、行のデータ値を変更できます。

- `DBPROPVAL_UP_INSERT` では、行を挿入できます。

- `DBPROPVAL_UP_DELETE` では、行を削除できます。

プロパティを次のように設定します。

```cpp
CDBPropSet ps(DBPROPSET_ROWSET);

ps.AddProperty(DBPROP_IRowsetChange, true);
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
```

1 つ以上の列が書き込み禁止になっている場合は、変更、挿入、または削除の操作が失敗することがあります。 この問題を修正するには、カーソル マップを変更します。

## <a name="setting-data-in-rows"></a>行のデータの設定

[CRowset::SetData](../../data/oledb/crowset-setdata.md) は、現在の行の 1 つ以上の列にデータ値を設定します。 次のコードは、テーブル `Products` の列 `Name` および `Units in Stock` にバインドされたデータ メンバーの値を設定してから、`SetData` を呼び出して、行セットの 100 行目にこれらの値を書き込みます。

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_UnitsInStock = 10000;

// Set the data
HRESULT hr = product.SetData();
```

## <a name="inserting-rows-into-rowsets"></a>行セットへの行の挿入

[CRowset::Insert](../../data/oledb/crowset-insert.md) は、アクセサーのデータを使用して新しい行を作成し、初期化します。 `Insert` は、現在の行の後にまったく新しい行を作成します。現在の行を次の行にインクリメントするか、そのまま変更しないでおくかを指定する必要があります。 これを指定するには、 *bGetRow* パラメーターを設定します。

```cpp
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)
```

- **false** (既定値) は、現在の行を次の行にインクリメントして、挿入された行を指すように指定します。

- **true** は、現在の行をそのままの場所に残すように指定します。

次のコードは、`Products` テーブルの列にバインドされたデータ メンバーの値を設定してから、`Insert` を呼び出して、これらの値を持つ新しい行を行セットの 100 行目の後に挿入します。 定義されていないデータが新しい行に含まれないように、すべての列値を設定することをお勧めします。

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Set the column values for a row of the Product table, then insert the row
product.m_ProductID = 101;
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_SupplierID = 27857;
product.m_CategoryID = 372;
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit, _T( "Pack of 10" ) );

product.m_UnitPrice = 20;
product.m_UnitsInStock = 10000;
product.m_UnitsOnOrder = 5201;
product.m_ReorderLevel = 5000;
product.m_Discontinued = false;

// You must also initialize the status and length fields before setting/inserting data
// Set the column status values
m_dwProductIDStatus = DBSTATUS_S_OK;
m_dwProductNameStatus = DBSTATUS_S_OK;
m_dwSupplierIDStatus = DBSTATUS_S_OK;
m_dwCategoryIDStatus = DBSTATUS_S_OK;
m_dwQuantityPerUnitStatus = DBSTATUS_S_OK;
m_dwUnitPriceStatus = DBSTATUS_S_OK;
m_dwUnitsInStockStatus = DBSTATUS_S_OK;
m_dwUnitsOnOrderStatus = DBSTATUS_S_OK;
m_dwReorderLevelStatus = DBSTATUS_S_OK;
m_dwDiscontinuedStatus = DBSTATUS_S_OK;

// Set the column length value for column data members that are not fixed-length types.
// The value should be the length of the string that you are setting.
m_dwProductNameLength = 6;             // "Candle" has 6 characters
m_dwQuantityPerUnitLength = 10;        // "Pack of 10" has 10 characters

// Insert the data
HRESULT hr = product.Insert();
```

詳しい例については、「 [CRowset::Insert](../../data/oledb/crowset-insert.md)」をご覧ください。

ステータスや長さのデータ メンバーを設定する方法について詳しくは、「 [ウィザードで生成されたアクセサーのフィールド ステータスのデータ メンバー](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)」をご覧ください。

## <a name="deleting-rows-from-rowsets"></a>行セットからの行の削除

[CRowset::Delete](../../data/oledb/crowset-delete.md) は、行セットから現在の行を削除します。 次のコードは、`Delete` を呼び出して、行セットの 100 行目を削除します。

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Delete the row
HRESULT hr = product.Delete();
```

## <a name="immediate-and-deferred-updates"></a>即時更新と遅延更新

特に指定しない限り、`SetData`、`Insert`、`Delete` の各メソッドを呼び出すと、データ ストアがすぐに更新されます。 しかし、すべての変更をコンシューマーがローカル キャッシュに格納しておき、次の更新メソッドの 1 つが呼び出されたらそれらをデータ ストアに転送するという方法で、更新を遅らせることができます。

- [CRowset::Update](../../data/oledb/crowset-update.md) は、最後のフェッチまたは `Update` 呼び出し以降に行われた現在の行に対する保留中のあらゆる変更を転送します。

- [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md) は、最後のフェッチまたは `Update` 呼び出し以降に行われたすべての行に対する保留中のあらゆる変更を転送します。

更新メソッドで使用される "更新" には、"コマンド上の変更" という特有の意味があります。これを SQL の **UPDATE** コマンドと混同しないようにしてください (`SetData` が SQL の **UPDATE** コマンドに相当します)。

遅延更新は、銀行の一連のトランザクションのような場面で役立ちます。最後の変更がコミットされるまでは一連の変更が送信されないため、1 つのトランザクションがキャンセルされた場合、変更を元に戻すことができます。 また、プロバイダーが変更を 1 つのネットワーク呼び出しにまとめられるので、効率が良くなります。

遅延更新をサポートするには、「**更新操作のサポート**」で説明したプロパティに加えて、`DBPROP_IRowsetChange` プロパティを設定する必要があります。

```cpp
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);
```

`Update` または `UpdateAll` を呼び出すと、これらのメソッドはローカル キャッシュからデータ ストアに変更を転送し、ローカル キャッシュをクリアします。 更新は現在の行に対する変更のみを転送するため、アプリケーションでどの行をどの時点で更新するかを追跡することが重要になります。 連続する 2 つの行を更新する方法を次の例に示します。

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Wick" ) );

product.m_UnitsInStock = 10000;

HRESULT hr = product.SetData();  // No changes made to row 100 yet
product.Update();                 // Update row 100 now

// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table
product.MoveNext();

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName _T( "Wax" ) );

product.m_UnitsInStock = 500;

HRESULT hr = product.SetData();  // No changes made to row 101 yet
product.Update();                 // Update row 101 now
```

保留中の変更が確実に転送されるようにするには、別の行に移動する前に `Update` を呼び出す必要があります。 ただし、アプリケーションで数百行も更新する必要がある場合など、この処理では時間がかかって非効率的な場合は、 `UpdateAll` を使用してすべての行を一度に更新できます。

たとえば、上記のコードの最初の `Update` 呼び出しがない場合は、100 行目は変更されないままになり、101 行目が変更されます。 100 行目が更新されるには、その後で、アプリケーションが `UpdateAll` を呼び出すか、100 行目に戻って `Update` を呼び出す必要があります。

変更を遅延させる主な理由は、変更を元に戻すことができるようにするためです。 [CRowset::Undo](../../data/oledb/crowset-undo.md) を呼び出すと、ローカル変更キャッシュの状態が、保留中の変更が作成される前のデータ ストアの状態にロールバックされます。 `Undo` は、ローカル キャッシュの状態を 1 ステップだけ (最後の変更の直前の状態に) ロールバックするのではないことにご注意ください。この処理を実行すると、その行のローカル キャッシュがクリアされます。 また、`Undo` は現在の行のみに影響します。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレートの操作](../../data/oledb/working-with-ole-db-consumer-templates.md)<br/>
[CRowset クラス](../../data/oledb/crowset-class.md)<br/>
[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))<br/>
