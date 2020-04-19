---
title: CCustomSession (CustomSess.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidersession
- myprovidersess.h
- ccustomsession
- customsess.h
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
- CCustomSession class in CustomSess.H
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
ms.openlocfilehash: 5cb462aba671e79450e9ee7b8447410252f8edc9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230582"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*カスタム*Sess.H には、宣言と OLE DB セッション オブジェクトの実装が含まれています。 データ ソース オブジェクトは、セッション オブジェクトを作成し、コンシューマーとプロバイダー間のメッセージ交換を表します。 複数の同時セッションは、1 つのデータ ソース用に開かれることができます。 継承リストに`CCustomSession`に従います。

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSession
class ATL_NO_VTABLE CCustomSession : 
   public CComObjectRootEx<CComSingleThreadModel>,
   public IGetDataSourceImpl<CCustomSession>,
   public IOpenRowsetImpl<CCustomSession>,
   public ISessionPropertiesImpl<CCustomSession>,
   public IObjectWithSiteSessionImpl<CCustomSession>,
   public IDBSchemaRowsetImpl<CCustomSession>,
   public IDBCreateCommandImpl<CCustomSession, CCustomCommand>
```

セッション オブジェクトから継承`IGetDataSource`、 `IOpenRowset`、 `ISessionProperties`、および`IDBCreateCommand`します。 `IGetDataSource`インターフェイスでは、セッションを作成したデータ ソースを取得できます。 これは、作成したデータ ソースまたはデータ ソースを提供するその他の情報のプロパティを取得する必要がある場合に便利です。 `ISessionProperties`インターフェイスは、セッションのすべてのプロパティを処理します。 `IOpenRowset`と`IDBCreateCommand`インターフェイスは、データベース処理のために使用します。 実装されているプロバイダーでは、コマンドをサポートするか、`IDBCreateCommand`インターフェイス。 コマンドを実行できるコマンド オブジェクトの作成に使用されます。 常に、プロバイダーを実装する、`IOpenRowset`オブジェクト。 プロバイダーからの行セットの生成に使用されます。 既定の行セットが (たとえば、 `"select * from mytable"`) プロバイダーからです。

ウィザードでは、次の 3 つのセッション クラスも生成されます: `CCustomSessionColSchema`、 `CCustomSessionPTSchema`、および`CCustomSessionTRSchema`します。 スキーマ行セットでは、これらのセッションが使用されます。 スキーマ行セットには、プロバイダーがコンシューマーのデータのクエリまたはフェッチを実行することがなく、コンシューマーにメタデータを返すことができるようにします。 メタデータをフェッチしていますが、プロバイダーの機能の検索よりも高速に実行できます。

OLE DB 仕様では、する必要がありますを実装するプロバイダー、`IDBSchemaRowset`インターフェイス スキーマ行セットの型を 3 つのサポート。DBSCHEMA_COLUMNS、DBSCHEMA_PROVIDER_TYPES、および DBSCHEMA_TABLES です。 ウィザードでは、各スキーマ行セットの実装を生成します。 ウィザードによって生成される各クラスが含まれています、`Execute`メソッド。 この`Execute`メソッドをサポートするどのテーブル、列、およびデータ型について、プロバイダーにデータを返すことができます。 このデータは、コンパイル時に呼ばれます。

## <a name="see-also"></a>関連項目

[プロバイダー ウィザードで生成されたファイル](../../data/oledb/provider-wizard-generated-files.md)<br/>
