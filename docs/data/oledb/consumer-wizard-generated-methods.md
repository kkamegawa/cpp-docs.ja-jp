---
title: コンシューマー ウィザードで生成されたメソッド
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, wizard-generated classes and methods
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
ms.openlocfilehash: 5d5c7aa680ca6b764e2ee9710e46cf6fa3af1c89
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707722"
---
# <a name="consumer-wizard-generated-methods"></a>コンシューマー ウィザードで生成されたメソッド

::: moniker range="vs-2019"

ATL OLE DB コンシューマー ウィザードは、Visual Studio 2019 以降では使用できません。 ただし、この機能を手動で追加することは可能です。

::: moniker-end

::: moniker range="<=vs-2017"

**ATL OLE DB コンシューマー ウィザード**と **MFC アプリケーション ウィザード**では、把握しておくべき特定の関数が生成されます。 一部のメソッドは、属性プロジェクトでは異なる方法で実装されるあります。そのため、各ケースにおける注意事項を以下で説明します。 挿入されたコードを表示する方法については、「 [挿入されたコードのデバッグ](/visualstudio/debugger/how-to-debug-injected-code)」を参照してください。

- `OpenAll` は、データ ソースと行セットを開き、利用可能な場合はブックマークを有効にします。

- `CloseAll` は、開いているすべての行セットを終了し、すべてのコマンドの実行を解放します。

- `OpenRowset` は `OpenAll` によって呼び出され、コンシューマーの行セットを開きます。

- `GetRowsetProperties` は、行セットのプロパティ セットへのポインターを取得します。このポインターを使用してプロパティを設定できます。

- `OpenDataSource` は、 **[データ リンク プロパティ]** ダイアログ ボックスで指定された初期化文字列を使用してデータ ソースを開きます。

- `CloseDataSource` は、適切な方法でデータ ソースを閉じます。

## <a name="openall-and-closeall"></a>OpenAll と CloseAll

```cpp
HRESULT OpenAll();

void CloseAll();
```

次の例は、同じコマンドを繰り返し実行する場合に `OpenAll` と `CloseAll` を呼び出す方法を示しています。 `CloseAll` の代わりに `Close` と `ReleaseCommand` を呼び出すバリエーションを示す [CCommand::Close](../../data/oledb/ccommand-close.md) のコード例と比べてみてください。

```cpp
int main(int argc, char* argv[])
{
   HRESULT hr;

   hr = CoInitialize(NULL);

   CCustOrdersDetail rs;      // Your CCommand-derived class
   rs.m_OrderID = 10248;      // Open order 10248
   hr = rs.OpenAll();         // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the first command execution
   rs.Close();

   rs.m_OrderID = 10249;      // Open order 10249 (a new order)
   hr = rs.Open();            // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the second command execution;
   // Instead of rs.CloseAll() you could call
   // rs.Close() and rs.ReleaseCommand():
   rs.CloseAll();

   CoUninitialize();
   return 0;
}
```

### <a name="remarks"></a>解説

`HasBookmark` メソッドを定義すると、`OpenAll` コードによって `DBPROP_IRowsetLocate` プロパティが設定されます。これを行う場合、プロバイダーでこのプロパティがサポートされていることを確認してください。

## <a name="openrowset"></a>OpenRowset

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);
```

`OpenAll` はこのメソッドを呼び出して、コンシューマーの行セットを開きます。 複数のデータ ソース/セッション/行セットを使用する場合を除き、通常は `OpenRowset` を呼び出す必要はありません。 `OpenRowset` は、コマンドまたはテーブル クラスのヘッダー ファイルで宣言されます。

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)
{
   HRESULT hr = Open(m_session, NULL, pPropSet);
   #ifdef _DEBUG
   if(FAILED(hr))
      AtlTraceErrorRecords(hr);
   #endif
   return hr;
}
```

属性は、このメソッドを異なる方法で実装します。 このバージョンでは、セッション オブジェクトとコマンド文字列 (既定値は db_command で指定されたコマンド文字列) を取得しますが、別のものを渡すこともできます。 `HasBookmark` メソッドを定義すると、`OpenRowset` コードによって `DBPROP_IRowsetLocate` プロパティが設定されます。これを行う場合、プロバイダーでこのプロパティがサポートされていることを確認してください。

```cpp
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand=NULL)
{

   DBPROPSET *pPropSet = NULL;
   CDBPropSet propset(DBPROPSET_ROWSET);
   __if_exists(HasBookmark)

   {
      propset.AddProperty(DBPROP_IRowsetLocate, true);
      pPropSet= &propset;
      }
...
}
```

## <a name="getrowsetproperties"></a>GetRowsetProperties

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet);
```

このメソッドは、行セットのプロパティ セットへのポインターを取得します。このポインターを使用して `DBPROP_IRowsetChange` などのプロパティを設定できます。 `GetRowsetProperties` は、次のようにユーザー レコード クラスで使用されます。 このコードを変更し、行セットの追加のプロパティを設定することができます。

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="remarks"></a>解説

グローバルな `GetRowsetProperties` メソッドは、ウィザードによって定義されるメソッドと競合する可能性があるため、定義しないでください。 これは、テンプレート プロジェクトと属性プロジェクトとともに得られるウィザード生成メソッドであり、属性ではこのコードが挿入されません。

## <a name="opendatasource-and-closedatasource"></a>OpenDataSource と CloseDataSource

```cpp
HRESULT OpenDataSource();

void CloseDataSource();
```

### <a name="remarks"></a>解説

ウィザードがメソッド `OpenDataSource` と `CloseDataSource` を定義します。`OpenDataSource` は [CDataSource::OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) を呼び出します。

::: moniker-end

## <a name="see-also"></a>関連項目

[ウィザードを使用した OLE DB コンシューマーの作成](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)