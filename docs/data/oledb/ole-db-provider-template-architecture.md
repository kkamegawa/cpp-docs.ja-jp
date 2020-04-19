---
title: OLE DB プロバイダー テンプレートのアーキテクチャ
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
ms.openlocfilehash: 65a7e5b8f169d06ca11d8d27ec99ce3db4b63014
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284002"
---
# <a name="ole-db-provider-template-architecture"></a>OLE DB プロバイダー テンプレートのアーキテクチャ

## <a name="data-sources-and-sessions"></a>データ ソースとセッション

OLE DB プロバイダーのアーキテクチャには、データ ソース オブジェクトと 1 つまたは複数のセッションが含まれています。 データ ソース オブジェクトは、すべてのプロバイダーのインスタンスを作成する必要があります最初のオブジェクトです。 コンシューマー アプリケーション、データを必要とは併置プロバイダーを起動するデータ ソース オブジェクトを作成します。 データ ソース オブジェクトは、セッション オブジェクトを作成します (を使用して、`IDBCreateSession`インターフェイス)、データ ソース オブジェクトに接続し、コンシューマーから。 ODBC プログラマは、データ ソース オブジェクトと同じ働きを考えることができます、`HENV`と同等のセッション オブジェクト、`HDBC`します。

![プロバイダー アーキテクチャ](../../data/oledb/media/vc4twb1.gif "プロバイダーのアーキテクチャ")

によって作成されたソース ファイルと共に、 **OLE DB プロバイダー ウィザード**、OLE DB テンプレートは、データ ソース オブジェクトを実装します。 セッションとは、OLE DB に対応するオブジェクト`TSession`します。

## <a name="mandatory-and-optional-interfaces"></a>必須および省略可能なインターフェイス

OLE DB プロバイダー テンプレートを提供する、必要なすべてのインターフェイスの実装をあらかじめパッケージ化されました。 必須および省略可能なインターフェイスは、OLE DB のいくつかの種類のオブジェクトによって定義されます。

- [データ ソース](../../data/oledb/data-source-object-interfaces.md)

- [セッション](../../data/oledb/session-object-interfaces.md)

- [行セット](../../data/oledb/rowset-object-interfaces.md)

- [コマンド](../../data/oledb/command-object-interfaces.md)

- [トランザクション](../../data/oledb/transaction-object-interfaces.md)

OLE DB プロバイダー テンプレートは、行と記憶域オブジェクトを実装していません。

次の表は、上記のオブジェクトの必須および省略可能なインターフェイスに従い、 [OLE DB 2.6 SDK ドキュメント](/previous-versions/windows/desktop/ms722784(v=vs.85))します。

|コンポーネント|Interface|コメント|
|---------------|---------------|-------------|
|[データ ソース](../../data/oledb/data-source-object-interfaces.md)([CDataSource](../../data/oledb/cdatasource-class.md))|[mandatory] `IDBCreateSession`<br /><br /> [mandatory] `IDBInitialize`<br /><br /> [mandatory] `IDBProperties`<br /><br /> [mandatory] `IPersist`<br /><br /> [省略可能] `IConnectionPointContainer`<br /><br /> [省略可能] `IDBAsynchStatus`<br /><br /> [省略可能] `IDBDataSourceAdmin`<br /><br /> [省略可能] `IDBInfo`<br /><br /> [省略可能] `IPersistFile`<br /><br /> [省略可能] `ISupportErrorInfo`|コンシューマーからプロバイダーへの接続。 オブジェクトは、ユーザー ID、パスワード、およびデータ ソース名などの接続のプロパティを指定に使用されます。 オブジェクトがデータ ソースを管理することもできます (作成、更新、削除、テーブル、およびなど)。|
|[セッション](../../data/oledb/session-object-interfaces.md)([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md))|[mandatory] `IGetDataSource`<br /><br /> [mandatory] `IOpenRowset`<br /><br /> [mandatory] `ISessionProperties`<br /><br /> [省略可能] `IAlterIndex`<br /><br /> [省略可能] `IAlterTable`<br /><br /> [省略可能] `IBindResource`<br /><br /> [省略可能] `ICreateRow`<br /><br /> [省略可能] `IDBCreateCommand`<br /><br /> [省略可能] `IDBSchemaRowset`<br /><br /> [省略可能] `IIndexDefinition`<br /><br /> [省略可能] `ISupportErrorInfo`<br /><br /> [省略可能] `ITableCreation`<br /><br /> [省略可能] `ITableDefinition`<br /><br /> [省略可能] `ITableDefinitionWithConstraints`<br /><br /> [省略可能] `ITransaction`<br /><br /> [省略可能] `ITransactionJoin`<br /><br /> [省略可能] `ITransactionLocal`<br /><br /> [省略可能] `ITransactionObject`|セッション オブジェクトは、コンシューマーとプロバイダー間の 1 つのメッセージ交換です。 ODBC に似ています`HSTMT`がアクティブにできる多くの同時セッションでします。<br /><br /> セッション オブジェクトは、OLE DB の機能を取得するプライマリ リンクです。 コマンド、トランザクション、または行セット オブジェクトを取得するには、セッション オブジェクトを移動します。|
|[行セット](../../data/oledb/rowset-object-interfaces.md)([CRowset](../../data/oledb/crowset-class.md))|[mandatory] `IAccessor`<br /><br /> [mandatory] `IColumnsInfo`<br /><br /> [mandatory] `IConvertType`<br /><br /> [mandatory] `IRowset`<br /><br /> [mandatory] `IRowsetInfo`<br /><br /> [省略可能] `IChapteredRowset`<br /><br /> [省略可能] `IColumnsInfo2`<br /><br /> [省略可能] `IColumnsRowset`<br /><br /> [省略可能] `IConnectionPointContainer`<br /><br /> [省略可能] `IDBAsynchStatus`<br /><br /> [省略可能] `IGetRow`<br /><br /> [省略可能] `IRowsetChange`<br /><br /> [省略可能] `IRowsetChapterMember`<br /><br /> [省略可能] `IRowsetCurrentIndex`<br /><br /> [省略可能] `IRowsetFind`<br /><br /> [省略可能] `IRowsetIdentity`<br /><br /> [省略可能] `IRowsetIndex`<br /><br /> [省略可能] `IRowsetLocate`<br /><br /> [省略可能] `IRowsetRefresh`<br /><br /> [省略可能] `IRowsetScroll`<br /><br /> [省略可能] `IRowsetUpdate`<br /><br /> [省略可能] `IRowsetView`<br /><br /> [省略可能] `ISupportErrorInfo`<br /><br /> [省略可能] `IRowsetBookmark`|行セット オブジェクトは、データ ソースからデータです。 オブジェクトは、そのデータとデータで基本的な操作 (更新プログラム、fetch、移動、および他のユーザー) のバインドに使用されます。 常にデータを保持および操作の行セット オブジェクトがあります。|
|[コマンド](../../data/oledb/command-object-interfaces.md)([CCommand](ccommand-class.md))|[mandatory] `IAccessor`<br /><br /> [mandatory] `IColumnsInfo`<br /><br /> [mandatory] `ICommand`<br /><br /> [mandatory] `ICommandProperties`<br /><br /> [mandatory] `ICommandText`<br /><br /> [mandatory] `IConvertType`<br /><br /> [省略可能] `IColumnsRowset`<br /><br /> [省略可能] `ICommandPersist`<br /><br /> [省略可能] `ICommandPrepare`<br /><br /> [省略可能] `ICommandWithParameters`<br /><br /> [省略可能] `ISupportErrorInfo`<br /><br /> [省略可能] `ICommandStream`|コマンド オブジェクトは、クエリなどのデータの操作を処理します。 パラメーター化または非パラメーター化ステートメントを処理できます。<br /><br /> コマンド オブジェクトで、パラメーターと出力列のバインドを処理するためも担当します。 バインディングは、行セット内の列を取得する方法に関する情報を含む構造です。 序数、データ型、長さ、および状態などの情報が含まれています。|
|[トランザクション](../../data/oledb/transaction-object-interfaces.md)(省略可能)|[mandatory] `IConnectionPointContainer`<br /><br /> [mandatory] `ITransaction`<br /><br /> [省略可能] `ISupportErrorInfo`|トランザクション オブジェクトは、データ ソース上の作業のアトミック単位を定義し、それらの作業単位が相互に関連付ける方法を決定します。 このオブジェクトは、直接 OLE DB プロバイダー テンプレートではサポートされません (独自のオブジェクトを作成する、)。|

詳細については、次のトピックを参照してください。

- [プロパティ マップ](../../data/oledb/property-maps.md)

- [ユーザー レコード](../../data/oledb/user-record.md)

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB インターフェイス](/previous-versions/windows/desktop/ms709709(v=vs.85))<br/>
