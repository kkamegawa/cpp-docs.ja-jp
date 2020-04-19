---
title: IPointerInactiveImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
ms.openlocfilehash: 6fb5d9f2bcbdeda61f32947bf339d134c4924b72
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495653"
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl クラス

このクラスは`IUnknown` 、および[iポインター非アクティブ](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)インターフェイスメソッドを実装します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`IPointerInactiveImpl`派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|オブジェクトの現在のアクティブ化ポリシーを取得します。 ATL 実装は E_NOTIMPL を返します。|
|[IPointerInactiveImpl:: OnInactiveMouseMove](#oninactivemousemove)|マウスポインターがその上に移動したことをオブジェクトに通知し、オブジェクトがマウスイベントを発生させることができることを示します。 ATL 実装は E_NOTIMPL を返します。|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|非アクティブなオブジェクトのマウスポインターを設定します。 ATL 実装は E_NOTIMPL を返します。|

## <a name="remarks"></a>Remarks

非アクティブなオブジェクトとは、単に読み込まれるか、または実行されるオブジェクトのことです。 アクティブなオブジェクトとは異なり、非アクティブなオブジェクトは Windows のマウスおよびキーボードメッセージを受け取ることができません。 したがって、非アクティブなオブジェクトは使用するリソースが減り、通常はより効率的です。

[Iポインタ inactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)インターフェイスを使用すると、オブジェクトは最小限のマウス操作をサポートしながら、非アクティブな状態を維持できます。 この機能は、特にコントロールに役立ちます。

クラス`IPointerInactiveImpl`は、 `IPointerInactive` E_NOTIMPL を返すだけでメソッドを実装します。 ただし、デバッグビルド`IUnknown`のダンプデバイスに情報を送信することによってが実装されます。

**関連記事**Atl[チュートリアル](../../atl/active-template-library-atl-tutorial.md)、 [atl プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>継承階層

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

##  <a name="getactivationpolicy"></a>  IPointerInactiveImpl::GetActivationPolicy

オブジェクトの現在のアクティブ化ポリシーを取得します。

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

Windows SDK の「 [Iポインター inactive:: GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) 」を参照してください。

##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove

マウスポインターがその上に移動したことをオブジェクトに通知し、オブジェクトがマウスイベントを発生させることができることを示します。

```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

Windows SDK の「 [Iポインター inactive:: OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) 」を参照してください。

##  <a name="oninactivesetcursor"></a>  IPointerInactiveImpl::OnInactiveSetCursor

非アクティブなオブジェクトのマウスポインターを設定します。

```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

Windows SDK の「 [Iポインター inactive:: OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) 」を参照してください。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
