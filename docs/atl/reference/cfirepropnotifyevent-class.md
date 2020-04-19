---
title: C焼討 Propnotifyevent クラス
ms.date: 11/04/2016
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
ms.openlocfilehash: 694127ceccc1d1b55e5da9abca799dff77dcfc60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496941"
---
# <a name="cfirepropnotifyevent-class"></a>C焼討 Propnotifyevent クラス

このクラスは、コントロールプロパティの変更についてコンテナーのシンクに通知するためのメソッドを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CFirePropNotifyEvent
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|雑音コントロールプロパティが変更されたことをコンテナーのシンクに通知します。|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|雑音コントロールプロパティが変更されようとしていることをコンテナーのシンクに通知します。|

## <a name="remarks"></a>Remarks

`CFirePropNotifyEvent`には、コントロールプロパティが変更されたか変更されようとしていることをコンテナーのシンクに通知する2つのメソッドがあります。

コントロールを実装しているクラスがから`IPropertyNotifySink` `CFirePropNotifyEvent`派生している場合は、また`FireOnRequestEdit`は`FireOnChanged`を呼び出すと、メソッドが呼び出されます。 コントロールクラスがから`IPropertyNotifySink`派生していない場合、これらの関数の呼び出しは S_OK を返します。

コントロールの作成の詳細については、 [ATL チュートリアル](../../atl/active-template-library-atl-tutorial.md)を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

##  <a name="fireonchanged"></a>  CFirePropNotifyEvent::FireOnChanged

指定されたオブジェクトのプロパティが変更されたことを、すべての接続された[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)インターフェイス (オブジェクトのすべての接続ポイント) に通知します。

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>パラメーター

*pUnk*<br/>
から通知を送信`IUnknown`するオブジェクトのへのポインター。

*dispID*<br/>
から変更されたプロパティの識別子。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

コントロールが接続ポイントをサポートしていない場合でも、この関数は安全に呼び出すことができます。

##  <a name="fireonrequestedit"></a>  CFirePropNotifyEvent::FireOnRequestEdit

指定されたオブジェクトプロパティが変更されようとしている、すべての接続されている[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)インターフェイス (オブジェクトのすべての接続ポイント) に通知します。

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>パラメーター

*pUnk*<br/>
から通知を送信`IUnknown`するオブジェクトのへのポインター。

*dispID*<br/>
から変更するプロパティの識別子。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

コントロールが接続ポイントをサポートしていない場合でも、この関数は安全に呼び出すことができます。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
