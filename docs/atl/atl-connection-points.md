---
title: ATL コネクション ポイント
ms.date: 11/04/2016
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
ms.openlocfilehash: df69496a6d245702a9598d684b25122ca55b1e6d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491809"
---
# <a name="atl-connection-points"></a>ATL コネクション ポイント

接続可能オブジェクトは、着信インターフェイスをサポートしているオブジェクトです。 着信インターフェイスにより、オブジェクトはクライアントと通信できます。 着信インターフェイスごとに、接続可能なオブジェクトは接続ポイントを公開しています。 各着信インターフェイスは、シンクと呼ばれるオブジェクト上のクライアントによって実装されます。

![接続ポイント](../atl/media/vc2zw31.gif "接続ポイント")

各接続ポイントは、 [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)インターフェイスをサポートしています。 接続可能なオブジェクトは、 [IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)インターフェイスを使用してクライアントへの接続ポイントを公開します。

## <a name="in-this-section"></a>このセクションの内容

[ATL コネクション ポイント クラス](../atl/atl-connection-point-classes.md)<br/>
接続ポイントをサポートする ATL クラスを簡単に説明します。

[オブジェクトへの接続ポイントの追加](../atl/adding-connection-points-to-an-object.md)<br/>
オブジェクトに接続ポイントを追加するためのステップについて説明します。

[ATL コネクション ポイントの例](../atl/atl-connection-point-example.md)<br/>
接続ポイントの宣言の例を示します。

## <a name="related-sections"></a>関連項目

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Active Template Library を使用してプログラミングする方法に関する概念説明のトピックへのリンクを提供します。

## <a name="see-also"></a>関連項目

[概念](../atl/active-template-library-atl-concepts.md)
