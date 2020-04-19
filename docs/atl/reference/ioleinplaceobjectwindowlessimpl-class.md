---
title: IOleInPlaceObjectWindowlessImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetDropTarget
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::OnWindowMessage
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::SetObjectRects
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::UIDeactivate
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
ms.openlocfilehash: fdd660daae109ac2a656519131dd9869ceaeaf4e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495744"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl クラス

このクラスは`IUnknown`を実装し、ウィンドウなしのコントロールがウィンドウメッセージを受信し、ドラッグアンドドロップ操作に参加できるようにするメソッドを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`IOleInPlaceObjectWindowlessImpl`派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|状況依存のヘルプを有効にします。 ATL 実装は E_NOTIMPL を返します。|
|[IOleInPlaceObjectWindowlessImpl:: GetDropTarget](#getdroptarget)|ドラッグアンドドロップをサポートする、埋め込み先のアクティブなウィンドウなしオブジェクトのインターフェイスを提供します。`IDropTarget` ATL 実装は E_NOTIMPL を返します。|
|[IOleInPlaceObjectWindowlessImpl:: GetWindow](#getwindow)|ウィンドウハンドルを取得します。|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|アクティブなインプレースコントロールを非アクティブにします。|
|[IOleInPlaceObjectWindowlessImpl:: OnWindowMessage](#onwindowmessage)|コンテナーから、アクティブな状態のウィンドウなしのコントロールにメッセージをディスパッチします。|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|以前に非アクティブにしたコントロールを再アクティブ化します。 ATL 実装は E_NOTIMPL を返します。|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|埋め込み先コントロールのどの部分を表示するかを示します。|
|[IOleInPlaceObjectWindowlessImpl:: Uide アクティブ化](#uideactivate)|インプレースアクティベーションをサポートするユーザーインターフェイスを非アクティブ化し、削除します。|

## <a name="remarks"></a>Remarks

[IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject)インターフェイスは、インプレースコントロールの再アクティブ化と非アクティブ化を管理し、コントロールのどの程度を表示するかを決定します。 [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)インターフェイスを使用すると、ウィンドウなしのコントロールでウィンドウメッセージを受信し、ドラッグアンドドロップ操作に参加できます。 クラス`IOleInPlaceObjectWindowlessImpl`は、および`IOleInPlaceObject` `IOleInPlaceObjectWindowless`の既定の実装を`IUnknown`提供し、デバッグビルドでダンプデバイスに情報を送信することによってを実装します。

**関連記事**Atl[チュートリアル](../../atl/active-template-library-atl-tutorial.md)、 [atl プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>継承階層

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

##  <a name="contextsensitivehelp"></a>IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

E_NOTIMPL を返します。

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IOleWindow:: ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) 」を参照してください。

##  <a name="getdroptarget"></a>IOleInPlaceObjectWindowlessImpl:: GetDropTarget

E_NOTIMPL を返します。

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IOleInPlaceObjectWindowless:: GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) 」を参照してください。

##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow

コンテナーは、この関数を呼び出して、コントロールのウィンドウハンドルを取得します。

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Remarks

現在ウィンドウに表示されている場合でも、一部のコンテナーはウィンドウなしで動作しません。 ATL の実装では、コントロールクラスのデータメンバー `m_bWasOnceWindowless`が TRUE の場合、関数は E_FAIL を返します。 それ以外の場合、 *phwnd*が NULL `GetWindow`でない場合、は*phwnd*をコントロールクラス`m_hWnd`のデータメンバーに設定\*し、S_OK を返します。

Windows SDK の「 [IOleWindow:: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) 」を参照してください。

##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

埋め込み先のアクティブなコントロールを非アクティブ化するために、コンテナーによって呼び出されます。

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Remarks

このメソッドは、コントロールの状態に応じて、完全な非アクティブ化または部分的な非アクティブ化を実行します。 必要に応じて、コントロールのユーザーインターフェイスが非アクティブ化され、コントロールのウィンドウがある場合は破棄されます。 コンテナーには、コントロールが現在アクティブではなくなったことが通知されます。 メニューと境界領域をネゴシエートするためにコンテナーによって使用されるインターフェイスが解放されます。`IOleInPlaceUIWindow`

Windows SDK の「 [IOleInPlaceObject:: Inplace deactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) 」を参照してください。

##  <a name="onwindowmessage"></a>IOleInPlaceObjectWindowlessImpl:: OnWindowMessage

コンテナーから、アクティブな状態のウィンドウなしのコントロールにメッセージをディスパッチします。

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IOleInPlaceObjectWindowless:: OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) 」を参照してください。

##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

E_NOTIMPL を返します。

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IOleInPlaceObject:: Re Andundo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) 」を参照してください。

##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects

サイズや位置が変更されたことをコントロールに通知するために、コンテナーによって呼び出されます。

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Remarks

コントロールの`m_rcPos`データメンバーとコントロールの表示を更新します。 クリップ領域と交差するコントロールの部分のみが表示されます。 コントロールの表示が既にクリップされていても、クリッピングが削除されている場合は、この関数を呼び出して、コントロールの完全なビューを再描画できます。

Windows SDK の「 [IOleInPlaceObject:: SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) 」を参照してください。

##  <a name="uideactivate"></a>IOleInPlaceObjectWindowlessImpl:: Uide アクティブ化

埋め込み先のアクティベーションをサポートするコントロールのユーザーインターフェイスを非アクティブ化し、削除します。

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Remarks

コントロールクラスのデータメンバー `m_bUIActive`を FALSE に設定します。 この関数の ATL 実装では、常に S_OK が返されます。

Windows SDK の「 [IOleInPlaceObject:: Uide activate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) 」を参照してください。

## <a name="see-also"></a>関連項目

[CComControl クラス](../../atl/reference/ccomcontrol-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
