---
title: OLE DB プロバイダー テンプレート リファレンス
ms.date: 11/04/2016
f1_keywords:
- vc.templates.ole
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
ms.openlocfilehash: e1d6be9687085361edd9141d8fb471e21b6f6376
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283862"
---
# <a name="ole-db-provider-templates-reference"></a>OLE DB プロバイダー テンプレート リファレンス

クラスと OLE DB プロバイダー テンプレート用のインターフェイスは、次のカテゴリにグループ化できます。 参考資料に関する情報も含まれます、 [OLE DB プロバイダー テンプレート用マクロ](../../data/oledb/macros-for-ole-db-provider-templates.md)します。

クラスは、次の名前付け規則を使用して、: パターンを持つという名前のクラス`IWidgetImpl`インターフェイスの実装を提供するよう`IWidget`します。

## <a name="session-classes"></a>セッション クラス

[IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
データ ソース オブジェクトから新しいセッションを作成し、新しく作成されたセッションで要求されたインターフェイスを返します。 データ ソース オブジェクトの必須のインターフェイスです。

[ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
プロパティ セットのマップによって定義された静的関数を呼び出すことによって、セッションのプロパティを実装します。 セッション クラスでは、プロパティ セットのマップを指定する必要があります。 セッションの必須インターフェイス。

## <a name="rowset-classes"></a>行セット クラス

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)

多くの実装インターフェイスの多重継承を必要とせず、標準の OLE DB 行セットの実装を提供します。 唯一のメソッドの実装を提供する必要があります`Execute`します。

[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
使用されている行ハンドルの既定の実装を提供します、`IRowsetImpl`クラス。 行ハンドルは、論理的に結果の行の一意のタグです。 `IRowsetImpl` 新たに作成`CSimpleRow`で要求されたすべての行の`IRowsetImpl::GetNextRows`します。

[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB プロバイダーを実装するを必要とする`HACCESSOR`、タグの配列には`DBBINDING`構造体。 提供`HACCESSOR`のアドレスを s、`BindType`構造体。 行セットおよびコマンドには必須です。

[IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
プロバイダーの列マップによって定義される静的関数にデリゲートします。 行セットとコマンドの必須のインターフェイスです。

[IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)<br/>
コマンドまたは行セットでは、型変換の可用性に関する情報を示します。 コマンド、行セット、およびインデックスの行セットでは必須です。 実装、 `IConvertType` OLE DB によって提供される変換オブジェクトへの委任でのインターフェイス。

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
実装、`IDBSchemaRowset`インターフェイスと、テンプレート化された作成関数`CreateSchemaRowset`します。

[IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)<br/>
開き、1 つのベース テーブルまたはインデックスからすべての行が含まれる行セットを返します。 セッション オブジェクトの必須のインターフェイスです。

[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
OLE DB 実装[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))インターフェイスで、行を削除して、新しい行を挿入する既存の行の列の値の更新が可能です。

[IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
このクラスから継承[IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite)と上書き[IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite)します。 `IRowsetCreatorImpl` 同じ機能を実行します。`IObjectWithSite`もにより、OLE DB プロパティが`DBPROPCANSCROLLBACKWARDS`と`DBPROPCANFETCHBACKWARDS`します。

[IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)<br/>
実装、`IRowsetIdentity`インターフェイスで、2 つの行のデータが同一かどうかどうかを比較することができます。

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
実装を提供、`IRowset`インターフェイスで、行セットの基本インターフェイスです。

[IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)<br/>
プロパティを使用して行セット プロパティの実装では、コマンド クラスで定義されているマップを設定します。 行セットの必須のインターフェイスです。

[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
OLE DB 実装[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))インターフェイスで、行セットから任意の行がフェッチされます。 で行セットの OLE DB のブックマークをサポートするには、このクラスから継承する行セットを確認します。

[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
実装は、接続ポイント上のリスナーに通知する関数をブロードキャスト`IID_IRowsetNotify`の行セットの内容の変更。 通知を処理するコンシューマーの実装[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))そのコネクション ポイントでそれを登録します。

[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
OLE DB 実装[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))インターフェイスに加えられた変更の送信を遅延するコンシューマー [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))をデータ ソースし、データ転送する前に変更を元に戻します。

## <a name="command-classes"></a>コマンド クラス

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
`ICommand` インターフェイスの実装を提供します。 このインターフェイスは表示されませんが、によって処理されます`ICommandTextImpl`します。 コマンド オブジェクトの必須インターフェイス。

[ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
この実装の`ICommandProperties`インターフェイスがによって定義された静的関数によって提供される、`BEGIN_PROPSET_MAP`マクロ。 コマンドでは必須です。

[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
設定、格納、およびコマンド テキストを返します。 コマンドでは必須です。

[IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
セッション オブジェクトから、新しいコマンドを作成し、新しく作成されたコマンドに対して要求されたインターフェイスを返します。 セッション オブジェクトの省略可能なインターフェイスです。

その他のコマンド クラスは、`IColumnsInfoImpl`と`IAccessorImpl`前の行セット クラスのセクションで説明します。

## <a name="data-source-classes"></a>データ ソース クラス

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
作成し、コンシューマーとの接続を削除します。 データ ソース オブジェクトと列挙子の省略可能なインターフェイスで必須のインターフェイスです。

[IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` データ ソース オブジェクトに必要なインターフェイスと列挙子のオプションのインターフェイスです。 ただし、列挙子を公開する場合`IDBInitialize`、それを公開する必要があります`IDBProperties`(データ ソースのプロパティ)。

[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)<br/>
データ ソース オブジェクトへのインターフェイス ポインターを取得します。 セッションの必須のインターフェイスです。

## <a name="other-classes"></a>その他のクラス

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
OLE DB プロパティのインターフェイスのさまざまなプロパティを実装する (たとえば、 `IDBProperties`、 `ISessionProperties`、および`IRowsetInfo`)。

[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)

OLE DB 実装[IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85))インターフェイスにレコードを追加して、データ メンバーからレコードを取得します。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB テンプレート](../../data/oledb/ole-db-templates.md)