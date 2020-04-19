---
title: IPropertyNotifySinkCP クラス
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: 9838a48b078cbc59a5ae86669ad9f26792d9816e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495623"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP クラス

このクラスは、接続可能なオブジェクトの送信インターフェイスとして[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)インターフェイスを公開します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`IPropertyNotifySinkCP`派生したクラス。

*CDV*<br/>
コネクションポイントとシンクの間の接続を管理するクラス。 既定値は[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)で、無制限の接続を許可します。 固定数の接続を指定する[CComUnkArray](../../atl/reference/ccomunkarray-class.md)を使用することもできます。

## <a name="remarks"></a>Remarks

`IPropertyNotifySinkCP`基底クラス[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)を通じて、すべてのメソッドを継承します。

[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)インターフェイスを使用すると、シンクオブジェクトはプロパティの変更に関する通知を受け取ることができます。 クラス`IPropertyNotifySinkCP`は、このインターフェイスを接続可能なオブジェクトの送信インターフェイスとして公開します。 クライアントは、シンクに`IPropertyNotifySink`メソッドを実装する必要があります。

インターフェイス`IPropertyNotifySink`を表すコネクション`IPropertyNotifySinkCP`ポイントを作成する場合は、からクラスを派生させます。

ATL での接続ポイントの使用方法の詳細については、「[接続ポイント](../../atl/atl-connection-points.md)」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

## <a name="see-also"></a>関連項目

[IConnectionPointImpl クラス](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[IConnectionPointContainerImpl クラス](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
