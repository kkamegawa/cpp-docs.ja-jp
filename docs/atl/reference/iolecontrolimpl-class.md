---
title: IOleControlImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
ms.openlocfilehash: 3bdb501d8210c98ce982719358564c4937991e12
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495823"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl クラス

このクラスは、 `IOleControl`インターフェイスの既定の実装を提供し、を実装`IUnknown`します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`IOleControlImpl`派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IOleControlImpl:: FreezeEvents](#freezeevents)|コンテナーがコントロールのイベントを無視するか受け入れるかを示します。|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|コントロールのキーボード動作に関する情報を入力します。 ATL 実装は E_NOTIMPL を返します。|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|1つ以上のコンテナーのアンビエントプロパティが変更されたことをコントロールに通知します。 ATL 実装は S_OK を返します。|
|[IOleControlImpl:: OnMnemonic](#onmnemonic)|ユーザーが指定されたキーストロークを押したことをコントロールに通知します。 ATL 実装は E_NOTIMPL を返します。|

## <a name="remarks"></a>Remarks

クラス`IOleControlImpl`は、 [IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol)インターフェイスの既定の実装を提供`IUnknown`し、デバッグビルドでダンプデバイスに情報を送信することによってを実装します。

**関連記事**Atl[チュートリアル](../../atl/active-template-library-atl-tutorial.md)、 [atl プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>継承階層

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

##  <a name="freezeevents"></a>IOleControlImpl:: FreezeEvents

ATL の実装では`FreezeEvents` 、が TRUE の場合`m_nFreezeEvents` `bFreeze`はコントロールクラスのデータメンバーをインクリメント`m_nFreezeEvents`し`bFreeze` 、が FALSE の場合はデクリメントします。

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Remarks

`FreezeEvents`次に、S_OK を返します。

Windows SDK の「 [IOleControl:: FreezeEvents](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) 」を参照してください。

##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo

コントロールのキーボード動作に関する情報を入力します。

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IOleControl: Get Linfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) 」を参照してください。

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange

1つ以上のコンテナーのアンビエントプロパティが変更されたことをコントロールに通知します。

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>戻り値

S_OK を返します。

### <a name="remarks"></a>Remarks

Windows SDK の「 [IOleControl:: OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) 」を参照してください。

##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic

ユーザーが指定されたキーストロークを押したことをコントロールに通知します。

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

Windows SDK の「 [IOleControl:: OnMnemonic](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) 」を参照してください。

## <a name="see-also"></a>関連項目

[IOleObjectImpl クラス](../../atl/reference/ioleobjectimpl-class.md)<br/>
[ActiveX コントロールインターフェイス](/windows/win32/com/activex-controls-interfaces)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
