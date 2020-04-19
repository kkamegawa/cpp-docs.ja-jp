---
title: Iviewの Teximpl クラス
ms.date: 11/04/2016
f1_keywords:
- IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl::Draw
- ATLCTL/ATL::IViewObjectExImpl::Freeze
- ATLCTL/ATL::IViewObjectExImpl::GetAdvise
- ATLCTL/ATL::IViewObjectExImpl::GetColorSet
- ATLCTL/ATL::IViewObjectExImpl::GetExtent
- ATLCTL/ATL::IViewObjectExImpl::GetNaturalExtent
- ATLCTL/ATL::IViewObjectExImpl::GetRect
- ATLCTL/ATL::IViewObjectExImpl::GetViewStatus
- ATLCTL/ATL::IViewObjectExImpl::QueryHitPoint
- ATLCTL/ATL::IViewObjectExImpl::QueryHitRect
- ATLCTL/ATL::IViewObjectExImpl::SetAdvise
- ATLCTL/ATL::IViewObjectExImpl::Unfreeze
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
ms.openlocfilehash: 3aead41f317d175eac9dcb094aa2070d82dc6185
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495503"
---
# <a name="iviewobjecteximpl-class"></a>Iviewの Teximpl クラス

このクラスは`IUnknown`を実装し、 [iviewobject](/windows/win32/api/oleidl/nn-oleidl-iviewobject)、 [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)、および[IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)インターフェイスの既定の実装を提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`IViewObjectExImpl`派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|コントロールの表現をデバイスコンテキストに描画します。|
|[Iview: Teximpl:: Freeze](#freeze)|コントロールの描画された表現を固定して、が`Unfreeze`変更されないようにします。 ATL 実装は E_NOTIMPL を返します。|
|[Iviewの Teximpl:: GetAdvise](#getadvise)|コントロール上の既存のアドバイザリシンク接続がある場合は、それを取得します。|
|[Iviewの Teximpl:: GetColorSet](#getcolorset)|コントロールが描画に使用する論理パレットを返します。 ATL 実装は E_NOTIMPL を返します。|
|[Iviewの Teximpl:: GetExtent](#getextent)|コントロールクラスのデータメンバー [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)から、コントロールの表示サイズを HIMETRIC 単位 (1 ユニットあたり0.01 ミリメートル) で取得します。|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|ユーザーがオブジェクトのサイズを変更するときに使用するオブジェクトのコンテナーからサイズ変更のヒントを提供します。|
|[IViewObjectExImpl::GetRect](#getrect)|要求された描画の側面を記述する四角形を返します。 ATL 実装は E_NOTIMPL を返します。|
|[Iviewの Teximpl:: GetViewStatus](#getviewstatus)|オブジェクトの不透明度とサポートされている描画の側面に関する情報を返します。|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|指定した点が指定した四角形内にあるかどうかを確認`pHitResult`し、で[ヒット結果](/windows/win32/api/ocidl/ne-ocidl-hitresult)の値を返します。|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|コントロールの表示領域が、指定された位置の四角形内の任意の点と重なっている`pHitResult`かどうかをチェックし、でのヒット結果の値を返します。|
|[Iviewの Teximpl:: SetAdvise](#setadvise)|コントロールとアドバイズシンク間の接続を設定して、コントロールのビューの変更についてシンクに通知できるようにします。|
|[Iviewの Teximpl:: 凍結解除](#unfreeze)|コントロールの描画された表現を Unfreezes します。 ATL 実装は E_NOTIMPL を返します。|

## <a name="remarks"></a>Remarks

[Iviewobject](/windows/win32/api/oleidl/nn-oleidl-iviewobject)、 [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)、および[IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)インターフェイスを使用すると、コントロールを直接表示し、アドバイズシンクを作成および管理して、コントロールの表示で変更をコンテナーに通知することができます。 この`IViewObjectEx`インターフェイスでは、ちらつきなしの描画、四角形でない透明なコントロール、およびヒットテスト (コントロールでマウスクリックを閉じる方法など) の拡張コントロール機能がサポートされています。 クラス`IViewObjectExImpl`は、これらのインターフェイスの既定の実装`IUnknown`を提供し、デバッグビルドでダンプデバイスに情報を送信することによってを実装します。

## <a name="inheritance-hierarchy"></a>継承階層

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

##  <a name="draw"></a>  IViewObjectExImpl::Draw

コントロールの表現をデバイスコンテキストに描画します。

```
STDMETHOD(Draw)(
    DWORD dwDrawAspect,
    LONG lindex,
    void* pvAspect,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    LPCRECTL prcBounds,
    LPCRECTL prcWBounds,
    BOOL(_stdcall* /* pfnContinue*/) (DWORD_PTR dwContinue),
    DWORD_PTR /* dwContinue */);
```

### <a name="remarks"></a>Remarks

このメソッドは`CComControl::OnDrawAdvanced` 、このメソッドを呼び出して、コントロール`OnDraw`クラスのメソッドを呼び出します。 ATL コントロールウィザードを使用してコントロールを作成すると、コントロールクラスにメソッドが自動的に追加されます。`OnDraw` ウィザードの既定`OnDraw`では、"ATL 3.0" というラベルの四角形が描画されます。

Windows SDK の「 [Iviewobject::D raw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) 」を参照してください。

##  <a name="freeze"></a>  IViewObjectExImpl::Freeze

コントロールの描画された表現を固定して、が`Unfreeze`変更されないようにします。 ATL 実装は E_NOTIMPL を返します。

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [Iviewobject:: Freeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze) 」を参照してください。

##  <a name="getadvise"></a>  IViewObjectExImpl::GetAdvise

コントロール上の既存のアドバイザリシンク接続がある場合は、それを取得します。

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Remarks

アドバイザリシンクは、コントロールクラスのデータメンバー [CComControlBase:: m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)に格納されます。

Windows SDK の「 [Iviewobject:: GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) 」を参照してください。

##  <a name="getcolorset"></a>  IViewObjectExImpl::GetColorSet

コントロールが描画に使用する論理パレットを返します。 ATL 実装は E_NOTIMPL を返します。

```
STDMETHOD(GetColorSet)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    LOGPALETTE** /* ppColorSet */);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [Iviewobject:: GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) 」を参照してください。

##  <a name="getextent"></a>  IViewObjectExImpl::GetExtent

コントロールクラスのデータメンバー [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)から、コントロールの表示サイズを HIMETRIC 単位 (1 ユニットあたり0.01 ミリメートル) で取得します。

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IViewObject2:: GetExtent](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) 」を参照してください。

##  <a name="getnaturalextent"></a>  IViewObjectExImpl::GetNaturalExtent

ユーザーがオブジェクトのサイズを変更するときに使用するオブジェクトのコンテナーからサイズ変更のヒントを提供します。

```
STDMETHOD(GetNaturalExtent)(
    DWORD dwAspect,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```

### <a name="remarks"></a>Remarks

が`dwAspect` DVASPECT_CONTENT で*pExtentInfo-> dwExtentMode*が DVEXTENT_CONTENT の場合、は`psizel` * をコントロールクラスのデータメンバー [CComControlBase:: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)に設定します。 それ以外の場合は、エラー HRESULT を返します。

Windows SDK の「 [IViewObjectEx:: GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) 」を参照してください。

##  <a name="getrect"></a>  IViewObjectExImpl::GetRect

要求された描画の側面を記述する四角形を返します。 ATL 実装は E_NOTIMPL を返します。

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IViewObjectEx:: GetRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) 」を参照してください。

##  <a name="getviewstatus"></a>Iviewの Teximpl:: GetViewStatus

オブジェクトの不透明度とサポートされている描画の側面に関する情報を返します。

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Remarks

既定では、ATL `pdwStatus`は、コントロールが VIEWSTATUS_OPAQUE をサポートしていることを示すを設定します (可能な値は[viewstatus](/windows/win32/api/ocidl/ne-ocidl-viewstatus)列挙体にあります)。

Windows SDK の「 [IViewObjectEx:: GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) 」を参照してください。

##  <a name="queryhitpoint"></a>  IViewObjectExImpl::QueryHitPoint

指定した点が指定した四角形内にあるかどうかを確認`pHitResult`し、で[ヒット結果](/windows/win32/api/ocidl/ne-ocidl-hitresult)の値を返します。

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Remarks

値には、HITRESULT_HIT または HITRESULT_OUTSIDE のいずれかを指定できます。

が`dwAspect` [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)に等しい場合、メソッドは S_OK を返します。 それ以外の場合、メソッドは E_FAIL を返します。

Windows SDK の「 [IViewObjectEx:: Queryヒットポイント](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint)」を参照してください。

##  <a name="queryhitrect"></a>  IViewObjectExImpl::QueryHitRect

コントロールの表示領域が、指定された位置の四角形内の任意の点と重なっている`pHitResult`かどうかをチェックし、での[ヒット結果](/windows/win32/api/ocidl/ne-ocidl-hitresult)の値を返します。

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Remarks

値には、HITRESULT_HIT または HITRESULT_OUTSIDE のいずれかを指定できます。

が`dwAspect` [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)に等しい場合、メソッドは S_OK を返します。 それ以外の場合、メソッドは E_FAIL を返します。

Windows SDK の「 [IViewObjectEx:: Queryヒット長方形](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect)」を参照してください。

##  <a name="setadvise"></a>  IViewObjectExImpl::SetAdvise

コントロールとアドバイズシンク間の接続を設定して、コントロールのビューの変更についてシンクに通知できるようにします。

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Remarks

アドバイズシンクの[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)インターフェイスへのポインターは、コントロールクラスのデータメンバー [CComControlBase:: m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)に格納されます。

Windows SDK の「 [Iviewobject:: SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) 」を参照してください。

##  <a name="unfreeze"></a>Iviewの Teximpl:: 凍結解除

コントロールの描画された表現を Unfreezes します。 ATL 実装は E_NOTIMPL を返します。

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [Iviewobject:: 凍結解除](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze)」を参照してください。

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

このオブジェクトに関連付けられているハンドルを閉じるには、このメソッドを実装します。

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>パラメーター

*hHandle*<br/>
閉じるハンドル。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

このメソッドに渡されたハンドルは、 [CWorkerThread:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)を呼び出すことによって、以前にこのオブジェクトに関連付けられていました。

### <a name="example"></a>例

次のコードは、の`IWorkerThreadClient::CloseHandle`単純な実装を示しています。

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

このオブジェクトに関連付けられたハンドルがシグナル状態になったときにコードを実行するには、このメソッドを実装します。

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>パラメーター

*dwParam*<br/>
ユーザーパラメーター。

*hObject*<br/>
がシグナル状態になったハンドル。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

このメソッドに渡されたハンドルと DWORD/ポインターは、 [CWorkerThread:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)を呼び出すことによって、以前にこのオブジェクトに関連付けられていました。

### <a name="example"></a>例

次のコードは、の`IWorkerThreadClient::Execute`単純な実装を示しています。

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>関連項目

[CComControl クラス](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX コントロールインターフェイス](/windows/win32/com/activex-controls-interfaces)<br/>
[チュートリアル](../../atl/active-template-library-atl-tutorial.md)<br/>
[ATL プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
