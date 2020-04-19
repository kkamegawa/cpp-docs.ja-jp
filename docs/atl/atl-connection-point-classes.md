---
title: ATL 接続ポイント クラス
ms.date: 11/04/2016
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
ms.openlocfilehash: 8644fc087d7f0a651724c40d2868e96c9b6ec96a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491821"
---
# <a name="atl-connection-point-classes"></a>ATL 接続ポイント クラス

ATL では、次のクラスを使用して接続ポイントをサポートします。

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)は接続ポイントを実装します。 それが表す送信インターフェイスの IID は、テンプレートパラメーターとして渡されます。

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md)は、接続ポイントコンテナーを実装し、オブジェクト`IConnectionPointImpl`の一覧を管理します。

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)は、 [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)インターフェイスを表す接続ポイントを実装します。

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md)は、コネクションポイントとシンクの間の任意の数の接続を管理します。

- [CComUnkArray](../atl/reference/ccomunkarray-class.md)は、テンプレートパラメーターで指定された数の接続を管理します。

- [C焼討 Propnotifyevent](../atl/reference/cfirepropnotifyevent-class.md)は、オブジェクトのプロパティが変更されたか変更されようとしていることをクライアントのシンクに通知します。

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md)は ATL COM オブジェクトの接続ポイントのサポートを提供します。 これらのコネクションポイントは、COM オブジェクトによって提供されるイベントシンクマップにマップされます。

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)は、クラスのイベントシンクマップと組み合わせて、適切なハンドラー関数にイベントをルーティングします。

## <a name="see-also"></a>関連項目

[接続ポイント](../atl/atl-connection-points.md)
