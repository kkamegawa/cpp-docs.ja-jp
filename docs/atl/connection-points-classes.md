---
title: コネクションポイントクラス (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
ms.openlocfilehash: 0dba06b072e1e9ca545ccbea196fcfe371b02157
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492447"
---
# <a name="connection-points-classes"></a>コネクションポイントクラス

次のクラスは、接続ポイントのサポートを提供します。

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md)コネクションポイントコンテナーを実装します。

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)コネクションポイントを実装します。

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)インターフェイスを表す接続ポイントを実装します。

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md)コネクションポイントとそのシンクとの間の無制限の接続を管理します。

- [CComUnkArray](../atl/reference/ccomunkarray-class.md)コネクションポイントとシンク間の接続の固定数を管理します。

- [C焼討 Propnotifyevent](../atl/reference/cfirepropnotifyevent-class.md)オブジェクトのプロパティが変更されたか変更されようとしていることをクライアントのシンクに通知します。

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md)ATL COM オブジェクトの接続ポイントのサポートを提供します。 これらのコネクションポイントは、COM オブジェクトによって提供されるイベントシンクマップにマップされます。

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)は、クラスのイベントシンクマップと連携して、適切なハンドラー関数にイベントをルーティングします。

## <a name="related-articles"></a>関連トピック

[接続ポイント](../atl/atl-connection-points.md)

[イベント処理と ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>関連項目

[クラスの概要](../atl/atl-class-overview.md)<br/>
[接続ポイントに関するマクロ](../atl/reference/connection-point-macros.md)<br/>
[コネクション ポイントに関するグローバル関数](../atl/reference/connection-point-global-functions.md)
