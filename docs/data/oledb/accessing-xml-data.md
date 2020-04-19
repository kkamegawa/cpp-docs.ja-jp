---
title: XML データへのアクセス
ms.date: 10/18/2018
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
ms.openlocfilehash: b5704c10393026a14ac66b632559fc376f008f8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284519"
---
# <a name="accessing-xml-data"></a>XML データへのアクセス

データ ソースから XML データを取得する 2 つの異なるメソッドがある: 1 つを使用して[CStreamRowset](../../data/oledb/cstreamrowset-class.md)とその他の使用法[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)します。

|機能|CStreamRowset|CXMLAccessor|
|-------------------|-------------------|------------------|
|転送されたデータ量|すべての列と行から一度にデータを取得します。|すべての列からデータが、一度に 1 つだけの行を取得します。 などのメソッドを使用して行を移動する必要があります`MoveNext`します。|
|文字列の書式設定|SQL Server では、XML 文字列を書式設定し、コンシューマーに送信します。|(プロバイダーが Unicode 文字列として送信要求) ネイティブ形式で行セットのデータを取得し、XML 形式でデータを保持している文字列を作成します。|
|書式設定の制御します。|SQL Server 2000 に固有のプロパティを設定して、XML 文字列の書式設定方法を制御のいくつかのレベルがあります。|生成された XML 文字列の形式の制御があるありません。|

中に`CStreamRowset`SQL Server 2000 でのみサポートされている XML 形式でのデータの取得の詳細の全体的な効率的な方法を提供します。

## <a name="retrieving-xml-data-using-cstreamrowset"></a>CStreamRowset を使用して XML データの取得

指定した[CStreamRowset](../../data/oledb/cstreamrowset-class.md)で行セットの種類として、`CCommand`または`CTable`宣言します。 で使用できます、独自のアクセサーまたはアクセサーはありません、たとえば。

```cpp
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;
```

- または -

```cpp
CCommand<CNoAccessor, CStreamRowset> myCmd;
```

通常どおり呼び出す`CCommand::Open`(指定すると、たとえば、`CRowset`として、`TRowset`クラス)、取得、`IRowset`ポインター。 `ICommand::Execute` 返します、`IRowset`ポインターに格納されている、`m_spRowset`のメンバー、`CRowset`オブジェクト。 などのメソッド`MoveFirst`、 `MoveNext`、および`GetData`ポインターを使用してデータを取得します。

これに対し、呼び出す`CCommand::Open`(指定しますが、`CStreamRowset`として、`TRowset`クラス)、`ICommand::Execute`を返します、`ISequentialStream`ポインターに格納されている、`m_spStream`データ メンバーの[CStreamRowset](../../data/oledb/cstreamrowset-class.md). 使用して、`Read`の XML 形式 (Unicode 文字列) のデータを取得します。 例えば:

```cpp
myCmd.m_spStream->Read()
```

SQL Server 2000 は XML 形式を設定し、すべての列と 1 つの XML 文字列として行セットのすべての行を返します。

使用例について、`Read`メソッドを参照してください**コンシューマーへの XML サポートの追加**で[単純なコンシューマーを実装する](../../data/oledb/implementing-a-simple-consumer.md)します。

> [!NOTE]
> XML の使用をサポート`CStreamRowset`SQL Server 2000 でのみ動作し、(MDAC と共にインストールされた) SQL Server 2000 の OLE DB プロバイダーが必要です。

## <a name="retrieving-xml-data-using-cxmlaccessor"></a>CXMLAccessor を使用して XML データの取得

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)データ ストアのスキーマの知識があるない場合に、文字列データとしてデータ ソースからデータをアクセスすることができます。 `CXMLAccessor` 同様に動作`CDynamicStringAccessorW`前者に XML 形式のタグ付きデータとしてデータ ストアからすべてのデータを変換する点が異なります。 XML タグ名では、データ ストアの列名が可能な限りと一致します。

使用`CXMLAccessor`の他のアクセサー クラスと、テンプレートのパラメーターとして渡す`CCommand`または`CTable`:

```cpp
CTable<CXMLAccessor, CRowset> rs;
```

使用[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)を一度に 1 行のテーブルからデータを取得しなどのメソッドを使用して行を移動します。`MoveNext`など。

```cpp
// Open data source, session, and rowset
hr = rs.MoveFirst();

while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
{
    CStringW strRowData;
    myCmd.GetXMLRowData(strRowData);

    printf_s( "%S\n", strRowData );

    hr = rs.MoveNext();
}
```

使用することができます[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) XML 形式の文字列データとして列 (データ型) の情報を取得します。

## <a name="see-also"></a>関連項目

[アクセサーの使用](../../data/oledb/using-accessors.md)