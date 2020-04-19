---
title: OLE DB コンシューマー テンプレート リファレンス
ms.date: 11/04/2016
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc.templates.ole
- vc-attr.db_source
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
ms.openlocfilehash: fb0b24798b3f2682bbbec7624df34b40a2a9f4cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361491"
---
# <a name="ole-db-consumer-templates-reference"></a>OLE DB コンシューマー テンプレート リファレンス

OLE DB コンシューマー テンプレートには、次のクラスが含まれます。 参考資料のトピックも含まれます、 [OLE DB コンシューマー テンプレート用マクロ](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)します。

## <a name="session-classes"></a>セッション クラス

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
データ ソースとの接続を管理します。 これは、必要なオブジェクト (データ ソースとセッション) とデータ ソースに接続するときに行う必要がある作業の一部をカプセル化するためにクライアントを作成するための便利なクラスです。

[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
データ ソースへのプロバイダー経由の接続を表す、OLE DB データ ソース オブジェクトに対応します。 1 つまたは複数データベース セッションで各表される、`CSession`オブジェクト、1 つの接続で実行できます。

[CEnumerator](../../data/oledb/cenumerator-class.md)<br/>
使用可能なデータ ソースについては、行セットを取得します。 OLE DB 列挙子オブジェクトに対応します。

[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
使用される`CEnumerator`列挙子の行セットからデータにアクセスします。 この行セットは、データ ソースと現在の列挙子から見えるの列挙子で構成されます。

[CSession](../../data/oledb/csession-class.md)<br/>
1 つのデータベース アクセスのセッションを表します。 1 つまたは複数のセッションが互いに関連付けることができます`CDataSource`オブジェクト。

## <a name="accessor-classes"></a>アクセサー クラス

[CAccessor](../../data/oledb/caccessor-class.md)<br/>
データ ソースに静的にバインドされているレコードを使用します。 データ ソースの構造がわかっている場合は、このアクセサー クラスを使用します。

[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
すべてのアクセサー クラスの基本クラス。

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
行セットの列の情報に基づいて、実行時に作成するアクセサー。 このクラスを使用すると、データ ソースの構造がわからない場合は、データを取得します。

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
コマンドの種類が不明な場合に使用できるアクセサー。 呼び出してパラメーター情報を取得、`ICommandWithParameters`インターフェイスをプロバイダーが、インターフェイスをサポートしている場合。

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
データベースの基になる構造の知識があるない場合にデータ ソースにアクセスすることができます。

[CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
ような`CDynamicStringAccessor`する点を除いて、このクラスは、ANSI 文字列データとしてデータ ストアからデータを要求します。

[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
ような`CDynamicStringAccessor`する点を除いて、このクラスは、UNICODE 文字列データとしてデータ ストアからデータを要求します。

[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
コマンドのパラメーターと列の両方を処理するメソッドとアクセサー。 このクラスは、プロバイダーは、型を変換できる限り、任意のデータ型を使用できます。

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
パラメーターをサポートまたは列を出力するクラスしたくない場合は、テンプレート引数として使用できます。

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)<br/>
ような`CDynamicStringAccessor`このクラスは、XML 形式のタグ付きデータとしてデータ ストアからすべてのデータを変換する点が異なります。

## <a name="rowset-classes"></a>行セット クラス

[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)<br/>
行セットと関連付けられているそのアクセサーをカプセル化します。

[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
配列の構文を使用して行セットの要素にアクセスするために使用します。

[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
フェッチし、単一の呼び出しで複数の行ハンドルを取得することによって行を一括でを操作するために使用します。

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
コマンドが行セットを返さない場合は、テンプレート引数として使用できます。

[cRestrictions](../../data/oledb/crestrictions-class.md)<br/>
スキーマ行セットの制限を指定するために使用します。

[CRowset](../../data/oledb/crowset-class.md)<br/>
操作、セット、および行セットのデータを取得するために使用します。

[CStreamRowset](../../data/oledb/cstreamrowset-class.md)<br/>
返します、`ISequentialStream`行セットではなくオブジェクトは、使用し、 `Read` XML 形式でデータを取得します。 (SQL Server 2000 は、書式設定。 この機能が SQL Server 2000 でのみ動作ことに注意してください)。

[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
ダミー実装を提供`IRowsetNotify`、空の関数を含む、`IRowsetNotify`メソッド`OnFieldChange`、 `OnRowChange`、および`OnRowsetChange`します。

[スキーマ行セット クラスと Typedef クラス](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)

OLE DB テンプレートは、一連の OLE DB スキーマ行セットに対応するクラスを提供します。

## <a name="command-classes"></a>コマンド クラス

[CCommand](../../data/oledb/ccommand-class.md)<br/>
設定して、パラメーター ベースの OLE DB コマンドを実行するために使用します。 単純な行セットを開くだけで、使用`CTable`代わりにします。

[CMultipleResults](../../data/oledb/cmultipleresults-class.md)<br/>
テンプレート引数として使用される、`CCommand`コマンドで複数の結果セットを処理するときにテンプレート。

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
などのテンプレート クラスでは、テンプレート引数として使用`CCommand`と`CTable`、アクセサー クラスの引数を受け取る。 使用`CNoAccessor`パラメーターをサポートまたは列を出力するクラスしたくない場合。

[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)<br/>
テンプレート引数として使用される、`CCommand`コマンドで 1 つの行セットを処理するときにテンプレート。 `CNoMultipleResults` テンプレート引数の既定値です。

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
テンプレート引数として使用される`CCommand`または`CTable`コマンドまたはテーブルに行セットが返されない場合。

[CTable](../../data/oledb/ctable-class.md)<br/>
パラメーターなしの単純な行セットにアクセスするために使用します。

## <a name="property-classes"></a>プロパティ クラス

[CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
プロパティの Id をコンシューマーがプロパティ情報の配列を渡すために使用します。 プロパティは、1 つのプロパティ セットに属しています。

[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
プロバイダーのプロパティを設定するために使用します。

## <a name="bookmark-class"></a>ブックマーク クラス

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
行セット内のデータにアクセスするためのインデックスとして使用します。

## <a name="error-class"></a>Error クラス

[CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)<br/>
OLE DB エラー情報を取得するために使用します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート リファレンス](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB テンプレート](../../data/oledb/ole-db-templates.md)