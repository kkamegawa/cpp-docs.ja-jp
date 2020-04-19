---
title: OLE DB テンプレート、属性、およびその他の実装
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 0e6b5dbc97f6a7bea1df342d6a792ea43907ca33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283890"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>OLE DB テンプレート、属性、およびその他の実装

## <a name="atl-ole-db-templates"></a>ATL OLE DB テンプレート

OLE DB テンプレート、ATL (Active Template Library) の一部である、高性能な OLE DB のデータベース テクノロジを使いやすく、一般的に使用される OLE DB インターフェイスの多くを実装するクラスを提供することで。 このテンプレートと共にライブラリは、OLE DB のスターター アプリケーションを作成するためのウィザード サポートです。

このテンプレート ライブラリには、2 つの部分が含まれています。

- **OLE DB コンシューマー テンプレート**OLE DB (コンシューマー) のクライアント アプリケーションを実装するために使用します。

- **OLE DB プロバイダー テンプレート**OLE DB サーバー (プロバイダー) アプリケーションを実装するために使用します。

OLE DB テンプレートを使用するには、C++ テンプレート、COM、および OLE DB インターフェイスに関する知識が必要です。 OLE DB を知らない場合は、次を参照してください。 [OLE DB プログラマーズ リファレンス](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)します。

詳細については、次の操作を実行できます。

- に関するトピックを参照して、 [OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)または[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)します。

- 作成、 [OLE DB コンシューマー](../../data/oledb/creating-an-ole-db-consumer.md)または[OLE DB プロバイダー](../../data/oledb/creating-an-ole-db-provider.md)します。

- 一覧を参照してください。 [OLE DB コンシューマー クラス](../../data/oledb/ole-db-consumer-templates-reference.md)または[OLE DB プロバイダー クラス](../../data/oledb/ole-db-provider-templates-reference.md)します。

- 一覧を参照してください。 [OLE DB テンプレート サンプル](https://github.com/Microsoft/VCSamples)します。

- 参照してください[OLE DB プログラマーズ リファレンス](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)(、Windows SDK) にします。

## <a name="ole-db-attributes"></a>OLE DB 属性します。

[OLE DB コンシューマー属性](../../windows/ole-db-consumer-attributes.md)OLE DB コンシューマーを作成する便利な手段を提供します。 OLE DB 属性に基づくコードの挿入、 [OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-reference.md)して OLE DB コンシューマーとプロバイダーを作成します。 属性でサポートされていない機能を指定する必要がある場合は、コードで属性と組み合わせて OLE DB テンプレートを使用することができます。

## <a name="mfc-ole-db-classes"></a>MFC の OLE DB クラス

MFC ライブラリの 1 つのクラス ライブラリが[COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)コントロールでのデータベース レコードを表示します。 ビューが、フォーム ビューに直接接続されている、`CRowset`オブジェクトし、のフィールドが表示されます、`CRowset`ダイアログ テンプレートのコントロール内のオブジェクト。 移動するための既定の実装も提供に、最初次、前、または最後のレコードとインターフェイス ビューで現在のレコードを更新します。 詳細については、「 `COleDBRecordView` 」を参照してください。

## <a name="ole-db-sdk-interfaces"></a>OLE DB SDK インターフェイス

OLE DB テンプレートが OLE DB の機能をサポートしない場合、OLE DB インターフェイス自体を使用する必要があります。 詳細については、次を参照してください。 [OLE DB プログラマーズ リファレンス](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)Windows SDK に含まれています。

## <a name="see-also"></a>関連項目

[OLE DB プログラミング](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB プログラミングの概要](../../data/oledb/ole-db-programming-overview.md)