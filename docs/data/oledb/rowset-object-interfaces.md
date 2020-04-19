---
title: 行セット オブジェクト インターフェイス
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
ms.openlocfilehash: 1f3e6066af4b6870c5fa90f7bde373bb7be476ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243979"
---
# <a name="rowset-object-interfaces"></a>行セット オブジェクト インターフェイス

次の表では、行セット オブジェクトの OLE DB で定義されている必須および省略可能なインターフェイスを示します。

|Interface|必須?|OLE DB テンプレートによって実装されるでしょうか。|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))|必須|はい|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|必須|はい|
|[IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))|必須|はい|
|[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))|必須|はい|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|必須|はい|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180(v=vs.85))|Optional|いいえ|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953(v=vs.85))|Optional|いいえ|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657(v=vs.85))|Optional|いいえ|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|はい (ATL) を使用|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832(v=vs.85))|Optional|いいえ|
|[IGetRow](/previous-versions/windows/desktop/ms718047(v=vs.85))|Optional|いいえ|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))|Optional|[はい]|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430(v=vs.85))|Optional|いいえ|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700(v=vs.85))|Optional|いいえ|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221(v=vs.85))|Optional|いいえ|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85))|(ただし、レベル 0 のプロバイダーに必要) (省略可能)|はい|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604(v=vs.85))|Optional|いいえ|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))|Optional|はい|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892(v=vs.85))|Optional|いいえ|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984(v=vs.85))|Optional|いいえ|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))|Optional|[はい]|
|[IRowsetView](/previous-versions/windows/desktop/ms709755(v=vs.85))|Optional|いいえ|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Optional|はい|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246(v=vs.85))|Optional|いいえ|

ウィザードで生成された行セット オブジェクトを実装して`IAccessor`、`IRowset`と`IRowsetInfo`継承を使用します。 `IAccessorImpl`両方の出力列をバインドします。 `IRowset`インターフェイスは、行のフェッチとデータを処理します。 `IRowsetInfo`インターフェイスは、行セット プロパティを処理します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
