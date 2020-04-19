---
title: IConnectionPointContainerImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
ms.openlocfilehash: 278ca6b1b9aac9539680d90b6fa0b18df22fc2f0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496024"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl クラス

このクラスは、 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)オブジェクトのコレクションを管理するための接続ポイントコンテナーを実装します。

## <a name="syntax"></a>構文

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`IConnectionPointContainerImpl`派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|接続可能オブジェクトでサポートされているコネクションポイントを反復処理する列挙子を作成します。|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|指定した IID をサポートするコネクションポイントへのインターフェイスポインターを取得します。|

## <a name="remarks"></a>Remarks

`IConnectionPointContainerImpl`[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)オブジェクトのコレクションを管理するための接続ポイントコンテナーを実装します。 `IConnectionPointContainerImpl`クライアントが接続可能なオブジェクトに関する詳細情報を取得するために呼び出すことができる2つのメソッドを提供します。

- `EnumConnectionPoints`オブジェクトがサポートする送信インターフェイスをクライアントが判断できるようにします。

- `FindConnectionPoint`オブジェクトが特定の送信インターフェイスをサポートしているかどうかをクライアントが判断できるようにします。

ATL での接続ポイントの使用の詳細については、「[接続ポイント](../../atl/atl-connection-points.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="enumconnectionpoints"></a>  IConnectionPointContainerImpl::EnumConnectionPoints

接続可能オブジェクトでサポートされているコネクションポイントを反復処理する列挙子を作成します。

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IConnectionPointContainer:: EnumConnectionPoints](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) 」を参照してください。

##  <a name="findconnectionpoint"></a>  IConnectionPointContainerImpl::FindConnectionPoint

指定した IID をサポートするコネクションポイントへのインターフェイスポインターを取得します。

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) 」を参照してください。

## <a name="see-also"></a>関連項目

[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
