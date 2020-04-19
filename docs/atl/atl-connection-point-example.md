---
title: ATL 接続ポイントの例
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: f33364cee65031c358fb546312f3fe2b7ae854d3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491792"
---
# <a name="atl-connection-point-example"></a>ATL 接続ポイントの例

次の例は、送信インターフェイスとして[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)をサポートするオブジェクトを示しています。

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

を送信`IPropertyNotifySink`インターフェイスとして指定する場合は、の`IConnectionPointImpl`代わりに[IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)クラスを使用できます。 例えば:

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>関連項目

[接続ポイント](../atl/atl-connection-points.md)
