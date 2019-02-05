---
title: CComControlBase クラス
ms.date: 11/04/2016
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
ms.openlocfilehash: 67d2be23aa6209c36b1a72eca3322efd1e977447
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894433"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase クラス

このクラスは、作成および ATL のコントロールを管理するためのメソッドを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|場合は、オーバーライド、`m_nAppearance`ストック プロパティは、型の**短い**します。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|コンストラクターです。|
|[CComControlBase:: ~ CComControlBase](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|要求されたインターフェイスへのポインターを取得します。|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|確認します、 *iVerb*で使用されるパラメーター`IOleObjectImpl::DoVerb`コントロールのユーザー インターフェイスをアクティブにするか (*iVerb* OLEIVERB_UIACTIVATE に等しい)、ユーザーがダブルクリックしたときに実行されるアクションを定義します、。コントロール (*iVerb* OLEIVERB_PRIMARY に等しい)、コントロールを表示します (*iVerb*でに等しい)、またはコントロールをアクティブに (*iVerb* OLEIVERB に等しい_INPLACEACTIVATE)。|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|確認、 *iVerb*で使用されるパラメーター`IOleObjectImpl::DoVerb`をアクティブ化するコントロールのユーザー インターフェイスを発生し、TRUE を返します。|
|[CComControlBase::DoVerbProperties](#doverbproperties)|コントロールのプロパティ ページが表示されます。|
|[CComControlBase::FireViewChange](#fireviewchange)|コントロールを再描画するコンテナーを確認するには、このメソッドを呼び出すか、コントロールのビューが変更された登録されているアドバイズ シンクに通知します。|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|示す、コントロールの設定の現在の外観を取得します。フラットから 3D 用の 1 は 0 です。|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|DISPID_AMBIENT_AUTOCLIP、コンテナーがコントロールの表示領域の自動のクリッピングをサポートしているかどうかを示すフラグを取得します。|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|DISPID_AMBIENT_BACKCOLOR、コンテナーで定義されているすべてのコントロールのアンビエント背景色を取得します。|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|DISPID_AMBIENT_CHARSET、アンビエント文字コンテナーによって定義されているすべてのコントロールのセットを取得します。|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|DISPID_AMBIENT_CODEPAGE、アンビエント文字コンテナーによって定義されているすべてのコントロールのセットを取得します。|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|DISPID_AMBIENT_DISPLAYASDEFAULT、したがってボタン コントロールを描画自体太くフレームを使用して、コンテナーには、既定のボタンを使用するには、このサイト内のコントロールがマークされている場合は TRUE であるフラグを取得します。|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|DISPID_AMBIENT_DISPLAYNAME、コンテナーがコントロールに指定された名前を取得します。|
|[CComControlBase::GetAmbientFont](#getambientfont)|取得、コンテナーへのポインターのアンビエント`IFont`インターフェイス。|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|取得、コンテナーへのポインターのアンビエント`IFontDisp`ディスパッチ インターフェイス。|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|DISPID_AMBIENT_FORECOLOR、コンテナーで定義されているすべてのコントロールのアンビエント前景色を取得します。|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|DISPID_AMBIENT_LOCALEID、コンテナーによって使用される言語の識別子を取得します。|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|DISPID_AMBIENT_MESSAGEREFLECT、コンテナーがイベントとして (WM_DRAWITEM) などのウィンドウ メッセージを受信するかどうかを示すフラグを取得します。|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|コンテナーの HPALETTE へのアクセスに使用される DISPID_AMBIENT_PALETTE を取得します。|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|指定されたコンテナーのプロパティを取得*id*します。|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|DISPID_AMBIENT_RIGHTTOLEFT、コンテナーによってコンテンツを表示する方向を取得します。|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|DISPID_AMBIENT_SCALEUNITS のラベルが表示されます (インチやセンチメートル) などのコンテナーのアンビエント単位を取得します。|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|DISPID_AMBIENT_SHOWGRABHANDLES、コンテナーがアクティブなときにハンドルを表示するコントロールを許可するかどうかを示すフラグを取得します。|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|DISPID_AMBIENT_SHOWHATCHING、コンテナーが、UI がアクティブのとき、ハッチ パターンで自体を表示するコントロールを許可するかどうかを示すフラグを取得します。|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|DISPID_AMBIENT_SUPPORTSMNEMONICS、コンテナーがキーボードのニーモニックをサポートしているかどうかを示すフラグを取得します。|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|DISPID_AMBIENT_TEXTALIGN、コンテナーが推奨するテキストの配置を取得します。標準の配置 (数値、テキスト左) の場合は 0、左揃えの場合は 1、2 を中央揃え、および右揃えの 3。|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|DISPID_AMBIENT_TOPTOBOTTOM、コンテナーによってコンテンツを表示する方向を取得します。|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|DISPID_AMBIENT_UIDEAD、コンテナーに、コントロール ユーザー インターフェイスの操作に応答するかどうかを示すフラグを取得します。|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|DISPID_AMBIENT_USERMODE、コンテナーが実行モード (TRUE)、またはデザイン モード (FALSE) かどうかを示すフラグを取得します。|
|[CComControlBase::GetDirty](#getdirty)|データ メンバーの値を返します`m_bRequiresSave`します。|
|[CComControlBase::GetZoomInfo](#getzoominfo)|X と y を取得します。 値の分子と分母ズームの倍率の有効なコントロールのインプレース編集します。|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|により、動詞の状態を非アクティブ状態からに移行コントロール*iVerb*を示します。|
|[CComControlBase::InternalGetSite](#internalgetsite)|識別されたインターフェイスへのポインターのコントロールのサイトを照会するには、このメソッドを呼び出します。|
|[CComControlBase::OnDraw](#ondraw)|コントロールを描画するには、このメソッドをオーバーライドします。|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|既定の`OnDrawAdvanced`描画、正規化されたデバイス コンテキストを準備し、コントロール クラスの`OnDraw`メソッド。|
|[CComControlBase::OnKillFocus](#onkillfocus)|コントロールは、インプレース アクティブと有効なコントロール サイトを持つそのコンテナーにコントロールがフォーカスを失ったことを通知を確認します。|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|UI がユーザー モードでは、し、コントロールをアクティブにすることを確認します。|
|[CComControlBase::OnPaint](#onpaint)|描画するため、コンテナーを準備し、コントロールのクライアント領域を取得、コントロール クラスの`OnDraw`メソッド。|
|[CComControlBase::OnSetFocus](#onsetfocus)|コントロールは、インプレース アクティブと有効なコントロール サイトを持つそのコンテナー コントロールに通知の確認がフォーカスを取得します。|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|独自のキーボード アクセラレータのハンドラーを提供するには、このメソッドをオーバーライドします。|
|[CComControlBase::SendOnClose](#sendonclose)|コントロールが閉じられているアドバイズ ホルダーに登録されているすべてのアドバイズ シンクに通知します。|
|[CComControlBase::SendOnDataChange](#sendondatachange)|コントロールのデータが変更されたアドバイズ ホルダーに登録されているすべてのアドバイズ シンクに通知します。|
|[CComControlBase::SendOnRename](#sendonrename)|コントロールに、新しいモニカーがあること、advise 所有者に登録されているすべてのアドバイズ シンクに通知します。|
|[CComControlBase::SendOnSave](#sendonsave)|コントロールが保存されているアドバイズ ホルダーに登録されているすべてのアドバイズ シンクに通知します。|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|登録されているすべてのコントロールのビューが変更されたアドバイズ シンクに通知します。|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|設定またはコントロールとの間にキーボード フォーカスを削除します。|
|[CComControlBase::SetDirty](#setdirty)|データ メンバーを設定`m_bRequiresSave`の値に*bDirty*します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|コントロールが他の任意のサイズを示すフラグします。|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|示すフラグ`IDataObjectImpl::GetData`と`CComControlBase::GetZoomInfo`からコントロールのサイズを設定する必要があります`m_sizeNatural`からではなく`m_sizeExtent`します。|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|示すフラグ`IDataObjectImpl::GetData`描画するときに HIMETRIC ユニットと単位を使用する必要があります。|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|コントロールがアクティブであることを示すフラグです。|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|コンテナー サポートを示すフラグ、`IOleInPlaceSiteEx`インターフェイスと OCX96 およびちらつきなしのコントロールなどの機能を制御します。|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|(ちらつきのないとウィンドウなしコントロールなど)、OCX96 コントロールの機能のサポートのコンテナーとコントロールがネゴシエートするかどうかと、コントロールは、ウィンドウまたはウィンドウなしかどうかを示すフラグします。|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|コンテナー コントロールの表示サイズが変更されたときに、プレゼンテーションを再構成するために、コントロールを示すフラグします。|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|最後に保存された後、コントロールが変更を示すフラグします。|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|コントロールでは、自然なエクステント (スケーリングされていない物理サイズ) のサイズを変更することを示すフラグ、コンテナーにコントロールの表示サイズが変更されたとき。|
|[CComControlBase::m_bUIActive](#m_buiactive)|メニューやツールバーなどのコントロールのユーザー インターフェイスを示すフラグはアクティブです。|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|コンテナーが指定したウィンドウ領域を使用して、コントロールを示すフラグします。|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|ウィンドウなし、されましたが、可能性があります、またはできない可能性がありますウィンドウなしようになりましたコントロールを示すフラグです。|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|コンテナー ウィンドウなしのコントロールをサポートしている場合でも、ウィンドウ表示するコントロールを示すフラグです。|
|[CComControlBase::m_bWndLess](#m_bwndless)|コントロールがウィンドウなしを示すフラグします。|
|[CComControlBase::m_hWndCD](#m_hwndcd)|コントロールに関連付けられているウィンドウ ハンドルへの参照が含まれています。|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|回数の合計数、コンテナーは、イベント (イベントの受け入れ) の間の凍結解除せずイベント (イベントを拒否しました) をフリーズがします。|
|[CComControlBase::m_rcPos](#m_rcpos)|コンテナーの座標で表された、コントロールの位置を (ピクセル単位)。|
|[この](#m_sizeextent)|特定のディスプレイの HIMETRIC 単位 (各単位は 0.01 ミリメートル) 内のコントロールの範囲。|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|HIMETRIC 単位 (各単位は 0.01 ミリメートル) コントロールの物理サイズ。|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|コンテナーのアドバイザリ コネクションを直接ポインター (コンテナーの[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink))。|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|A`CComDispatchDriver`オブジェクトを取得し、コンテナーのプロパティを設定することができます、`IDispatch`ポインター。|
|[CComControlBase::m_spClientSite](#m_spclientsite)|コンテナー内のコントロールのクライアントのサイトへのポインター。|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|標準的なデータ オブジェクト間のアドバイザリ コネクションをアドバイズ シンクすることを意味を提供します。|
|[は](#m_spinplacesite)|コンテナーへのポインター[ビュー](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)、[この](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)、または[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)インターフェイス ポインター。|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|アドバイザリ コネクションを保持するための標準的な実装を提供します。|

## <a name="remarks"></a>Remarks

このクラスは、作成および ATL のコントロールを管理するためのメソッドを提供します。 [CComControl クラス](../../atl/reference/ccomcontrol-class.md)から派生した`CComControlBase`します。 ATL コントロール ウィザードを使用して、標準のコントロールまたは DHTML コントロールを作成するときに、ウィザードが自動的にからクラスを派生`CComControlBase`します。

コントロールの作成の詳細については、次を参照してください。、 [ATL チュートリアル](../../atl/active-template-library-atl-tutorial.md)します。 ATL プロジェクト ウィザードの詳細については、記事を参照してください。 [ATL プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)です。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl.h

##  <a name="appearancetype"></a>  CComControlBase::AppearanceType

場合は、オーバーライド、`m_nAppearance`ストック プロパティは、型の**短い**します。

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Remarks

ATL コントロール ウィザードの追加`m_nAppearance`ストック short 型のプロパティ。 オーバーライド`AppearanceType`別のデータ型を使用する場合。

##  <a name="ccomcontrolbase"></a>  CComControlBase::CComControlBase

コンストラクターです。

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
コントロールに関連付けられているウィンドウのハンドル。

### <a name="remarks"></a>Remarks

コントロールのサイズを HIMETRIC 単位の 5080 × 5080 を初期化します ("2"X 2) を初期化し、`CComControlBase`データ メンバーの値を NULL または FALSE にします。

##  <a name="dtor"></a>  CComControlBase:: ~ CComControlBase

デストラクターです。

```
~CComControlBase();
```

### <a name="remarks"></a>Remarks

コントロールがウィンドウを持つ場合は`~CComControlBase`それを呼び出すことで破壊[DestroyWindow](/windows/desktop/api/winuser/nf-winuser-destroywindow)します。

##  <a name="controlqueryinterface"></a>  CComControlBase::ControlQueryInterface

要求されたインターフェイスへのポインターを取得します。

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
要求されているインターフェイスの GUID です。

*ppv*<br/>
によって識別されるインターフェイス ポインターへのポインター *iid*インターフェイスが見つからない場合は null です。

### <a name="remarks"></a>Remarks

COM マップ テーブル内のインターフェイスのみを処理します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>  CComControlBase::DoesVerbActivate

確認します、 *iVerb*で使用されるパラメーター`IOleObjectImpl::DoVerb`コントロールのユーザー インターフェイスをアクティブにするか (*iVerb* OLEIVERB_UIACTIVATE に等しい)、ユーザーがダブルクリックしたときに実行されるアクションを定義します、。コントロール (*iVerb* OLEIVERB_PRIMARY に等しい)、コントロールを表示します (*iVerb*でに等しい)、またはコントロールをアクティブに (*iVerb* OLEIVERB に等しい_INPLACEACTIVATE)。

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>パラメーター

*iVerb*<br/>
によって実行されるアクションを示す値`DoVerb`します。

### <a name="return-value"></a>戻り値

場合に TRUE を返します*iVerb* OLEIVERB_UIACTIVATE、OLEIVERB_PRIMARY で、または OLEIVERB_INPLACEACTIVATE と等しい。 それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

独自のライセンス認証の動詞を定義するには、このメソッドをオーバーライドできます。

##  <a name="doesverbuiactivate"></a>  CComControlBase::DoesVerbUIActivate

確認、 *iVerb*で使用されるパラメーター`IOleObjectImpl::DoVerb`をアクティブ化するコントロールのユーザー インターフェイスを発生し、TRUE を返します。

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>パラメーター

*iVerb*<br/>
によって実行されるアクションを示す値`DoVerb`します。

### <a name="return-value"></a>戻り値

場合に TRUE を返します*iVerb* OLEIVERB_UIACTIVATE、OLEIVERB_PRIMARY で、または OLEIVERB_INPLACEACTIVATE と等しい。 それ以外の場合、FALSE を返します。

##  <a name="doverbproperties"></a>  CComControlBase::DoVerbProperties

コントロールのプロパティ ページが表示されます。

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>パラメーター

*prcPosRec*<br/>
予約済み。

*hwndParent*<br/>
コントロールを含むウィンドウのハンドル。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>  CComControlBase::FireViewChange

コントロールを再描画するコンテナーを確認するには、このメソッドを呼び出すか、コントロールのビューが変更された登録されているアドバイズ シンクに通知します。

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

コントロールがアクティブな場合 (コントロール クラスのデータ メンバー [CComControlBase::m_bInPlaceActive](#m_binplaceactive) true)、コントロール全体を再描画するコンテナーに通知します。 コントロールがアクティブでない場合は、コントロールの登録済みに通知しますアドバイズ シンク (コントロール クラスのデータ メンバーを介して[アドバイズ](#m_spadvisesink)) コントロールのビューが変更されました。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>  CComControlBase::GetAmbientAppearance

示す、コントロールの設定の現在の外観を取得します。フラットから 3D 用の 1 は 0 です。

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>パラメーター

*nAppearance*<br/>
プロパティを示すです。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>  CComControlBase::GetAmbientAutoClip

DISPID_AMBIENT_AUTOCLIP、コンテナーがコントロールの表示領域の自動のクリッピングをサポートしているかどうかを示すフラグを取得します。

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>パラメーター

*bAutoClip*<br/>
DISPID_AMBIENT_AUTOCLIP プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getambientbackcolor"></a>  CComControlBase::GetAmbientBackColor

DISPID_AMBIENT_BACKCOLOR、コンテナーで定義されているすべてのコントロールのアンビエント背景色を取得します。

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>パラメーター

*背景色*<br/>
DISPID_AMBIENT_BACKCOLOR プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getambientcharset"></a>  CComControlBase::GetAmbientCharSet

DISPID_AMBIENT_CHARSET、アンビエント文字コンテナーによって定義されているすべてのコントロールのセットを取得します。

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>パラメーター

*bstrCharSet*<br/>
DISPID_AMBIENT_CHARSET プロパティ。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="getambientcodepage"></a>  CComControlBase::GetAmbientCodePage

DISPID_AMBIENT_CODEPAGE、コンテナーで定義されているすべてのコントロールの周囲のコード ページを取得します。

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>パラメーター

*ulCodePage*<br/>
プロパティことにあります。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="getambientdisplayasdefault"></a>  CComControlBase::GetAmbientDisplayAsDefault

DISPID_AMBIENT_DISPLAYASDEFAULT、したがってボタン コントロールを描画自体太くフレームを使用して、コンテナーには、既定のボタンを使用するには、このサイト内のコントロールがマークされている場合は TRUE であるフラグを取得します。

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>パラメーター

*bDisplayAsDefault*<br/>
DISPID_AMBIENT_DISPLAYASDEFAULT プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getambientdisplayname"></a>  CComControlBase::GetAmbientDisplayName

DISPID_AMBIENT_DISPLAYNAME、コンテナーがコントロールに指定された名前を取得します。

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>パラメーター

*bstrDisplayName*<br/>
DISPID_AMBIENT_DISPLAYNAME プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getambientfont"></a>  CComControlBase::GetAmbientFont

取得、コンテナーへのポインターのアンビエント`IFont`インターフェイス。

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>パラメーター

*ppFont*<br/>
コンテナーのアンビエント[IFont](/windows/desktop/api/ocidl/nn-ocidl-ifont)インターフェイス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

プロパティが NULL の場合、ポインターが NULL です。 ポインターが NULL でない場合、呼び出し元は、ポインターを解放する必要があります。

##  <a name="getambientfontdisp"></a>  CComControlBase::GetAmbientFontDisp

取得、コンテナーへのポインターのアンビエント`IFontDisp`ディスパッチ インターフェイス。

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>パラメーター

*ppFont*<br/>
コンテナーのアンビエント[IFontDisp](/windows/desktop/api/ocidl/nn-ocidl-ifontdisp)ディスパッチ インターフェイス。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

プロパティが NULL の場合、ポインターが NULL です。 ポインターが NULL でない場合、呼び出し元は、ポインターを解放する必要があります。

##  <a name="getambientforecolor"></a>  CComControlBase::GetAmbientForeColor

DISPID_AMBIENT_FORECOLOR、コンテナーで定義されているすべてのコントロールのアンビエント前景色を取得します。

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>パラメーター

*前景色*<br/>
DISPID_AMBIENT_FORECOLOR プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getambientlocaleid"></a>  CComControlBase::GetAmbientLocaleID

DISPID_AMBIENT_LOCALEID、コンテナーによって使用される言語の識別子を取得します。

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>パラメーター

*lcid*<br/>
DISPID_AMBIENT_LOCALEID プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

コントロールは、そのユーザー インターフェイスを異なる言語を適応させる、この識別子を使用できます。

##  <a name="getambientmessagereflect"></a>  CComControlBase::GetAmbientMessageReflect

DISPID_AMBIENT_MESSAGEREFLECT、コンテナーは、ウィンドウ メッセージを受信するかどうかを示すフラグを取得します (など`WM_DRAWITEM`) イベントとして。

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>パラメーター

*bMessageReflect*<br/>
DISPID_AMBIENT_MESSAGEREFLECT プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getambientpalette"></a>  CComControlBase::GetAmbientPalette

コンテナーの HPALETTE へのアクセスに使用される DISPID_AMBIENT_PALETTE を取得します。

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>パラメーター

*hPalette*<br/>
DISPID_AMBIENT_PALETTE プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getambientproperty"></a>  CComControlBase::GetAmbientProperty

指定されたコンテナーのプロパティを取得*dispid*します。

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>パラメーター

*dispid*<br/>
取得するコンテナーのプロパティの識別子。

*var*<br/>
プロパティを受信する変数。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

ATL には、一連の特定のプロパティを取得するヘルパー関数が提供されている[用意されています](#getambientbackcolor)します。 使用して、適切なメソッドがない場合、`GetAmbientProperty`します。

##  <a name="getambientrighttoleft"></a>  CComControlBase::GetAmbientRightToLeft

DISPID_AMBIENT_RIGHTTOLEFT、コンテナーによってコンテンツを表示する方向を取得します。

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>パラメーター

*bRightToLeft*<br/>
DISPID_AMBIENT_RIGHTTOLEFT プロパティ。 FALSE の場合はコンテンツが右から左に表示されている場合は TRUE に設定して、右側に左が表示されます。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="getambientscaleunits"></a>  CComControlBase::GetAmbientScaleUnits

DISPID_AMBIENT_SCALEUNITS のラベルが表示されます (インチやセンチメートル) などのコンテナーのアンビエント単位を取得します。

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>パラメーター

*bstrScaleUnits*<br/>
DISPID_AMBIENT_SCALEUNITS プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getambientshowgrabhandles"></a>  CComControlBase::GetAmbientShowGrabHandles

DISPID_AMBIENT_SHOWGRABHANDLES、コンテナーがアクティブなときにハンドルを表示するコントロールを許可するかどうかを示すフラグを取得します。

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>パラメーター

*bShowGrabHandles*<br/>
DISPID_AMBIENT_SHOWGRABHANDLES プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getambientshowhatching"></a>  CComControlBase::GetAmbientShowHatching

DISPID_AMBIENT_SHOWHATCHING、コンテナーがコントロールのユーザー インターフェイスがアクティブなとき、ハッチ パターンで自体を表示するコントロールを許可するかどうかを示すフラグを取得します。

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>パラメーター

*bShowHatching*<br/>
DISPID_AMBIENT_SHOWHATCHING プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getambientsupportsmnemonics"></a>  CComControlBase::GetAmbientSupportsMnemonics

DISPID_AMBIENT_SUPPORTSMNEMONICS、コンテナーがキーボードのニーモニックをサポートしているかどうかを示すフラグを取得します。

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>パラメーター

*bSupportsMnemonics*<br/>
DISPID_AMBIENT_SUPPORTSMNEMONICS プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getambienttextalign"></a>  CComControlBase::GetAmbientTextAlign

DISPID_AMBIENT_TEXTALIGN、コンテナーが推奨するテキストの配置を取得します。標準の配置 (数値、テキスト左) の場合は 0、左揃えの場合は 1、2 を中央揃え、および右揃えの 3。

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>パラメーター

*nTextAlign*<br/>
DISPID_AMBIENT_TEXTALIGN プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getambienttoptobottom"></a>  CComControlBase::GetAmbientTopToBottom

DISPID_AMBIENT_TOPTOBOTTOM、コンテナーによってコンテンツを表示する方向を取得します。

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>パラメーター

*bTopToBottom*<br/>
DISPID_AMBIENT_TOPTOBOTTOM プロパティ。 テキストが表示されている場合に TRUE に設定上から順に、FALSE の場合は表示される下部にあるページのトップへ。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="getambientuidead"></a>  CComControlBase::GetAmbientUIDead

DISPID_AMBIENT_UIDEAD、コンテナーに、コントロール ユーザー インターフェイスの操作に応答するかどうかを示すフラグを取得します。

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>パラメーター

*bUIDead*<br/>
DISPID_AMBIENT_UIDEAD プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

TRUE の場合、コントロールが応答しない必要があります。 このフラグは、DISPID_AMBIENT_USERMODE フラグに関係なく適用されます。 参照してください[CComControlBase::GetAmbientUserMode](#getambientusermode)します。

##  <a name="getambientusermode"></a>  CComControlBase::GetAmbientUserMode

DISPID_AMBIENT_USERMODE、コンテナーが実行モード (TRUE)、またはデザイン モード (FALSE) かどうかを示すフラグを取得します。

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>パラメーター

*bUserMode*<br/>
DISPID_AMBIENT_USERMODE プロパティ。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="getdirty"></a>  CComControlBase::GetDirty

データ メンバーの値を返します`m_bRequiresSave`します。

```
BOOL GetDirty();
```

### <a name="return-value"></a>戻り値

データ メンバーの値を返します[m_bRequiresSave](#m_brequiressave)します。

### <a name="remarks"></a>Remarks

使用してこの値を設定[CComControlBase::SetDirty](#setdirty)します。

##  <a name="getzoominfo"></a>  CComControlBase::GetZoomInfo

X と y を取得します。 値の分子と分母ズームの倍率の有効なコントロールのインプレース編集します。

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>パラメーター

*di*<br/>
倍率の分子と分母を格納する構造体。 詳細については、次を参照してください。 [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)します。

### <a name="remarks"></a>Remarks

ズームの倍率は、コントロールの現在の大きさの自然なサイズの割合を占めています。

##  <a name="inplaceactivate"></a>  CComControlBase::InPlaceActivate

により、動詞の状態を非アクティブ状態からに移行コントロール*iVerb*を示します。

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>パラメーター

*iVerb*<br/>
によって実行されるアクションを示す値[IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb)します。

*prcPosRect*<br/>
インプレース コントロールの位置を指すポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

このメソッドは、アクティブ化する前に、コントロールにクライアントのサイトを持つし、コントロールの量が表示されてがチェックし、親ウィンドウ内のコントロールの位置を取得するを確認します。 コントロールがアクティブにした後、このメソッドはコントロールのユーザー インターフェイスをアクティブにし、コントロールを表示するコンテナーを示します。

このメソッドも取得、 `IOleInPlaceSite`、 `IOleInPlaceSiteEx`、または`IOleInPlaceSiteWindowless`コントロールのインターフェイス ポインター、コントロール クラスのデータ メンバーに格納[は](#m_spinplacesite)します。 コントロール クラスのデータ メンバー [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)、 [CComControlBase::m_bWndLess](#m_bwndless)、 [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)、および[各](#m_bnegotiatedwnd)に応じて true に設定されます。

##  <a name="internalgetsite"></a>  CComControlBase::InternalGetSite

識別されたインターフェイスへのポインターのコントロールのサイトを照会するには、このメソッドを呼び出します。

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
返されるインターフェイス ポインターの IID *ppUnkSite*します。

*ppUnkSite*<br/>
要求されたインターフェイス ポインターを受け取るポインター変数のアドレス*riid*します。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

サイトで要求されたインターフェイスをサポートしている場合*riid*、によって返されるポインター *ppUnkSite*します。 それ以外の場合、 *ppUnkSite* NULL に設定されます。

##  <a name="m_bautosize"></a>  CComControlBase::m_bAutoSize

コントロールが他の任意のサイズを示すフラグします。

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Remarks

このフラグをチェックして`IOleObjectImpl::SetExtent`し、TRUE の場合、関数は E_FAIL を返します。

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

追加する場合、**自動サイズ**オプション、[ストック プロパティ](../../atl/reference/stock-properties-atl-control-wizard.md)ATL コントロール ウィザード、ウィザードのタブに自動的に、コントロール クラスでこのデータ メンバーを作成します、put を作成およびプロパティのメソッドを取得をサポートしていると[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)プロパティが変更されたときに、コンテナーを自動的に通知します。

##  <a name="m_bdrawfromnatural"></a>  CComControlBase::m_bDrawFromNatural

示すフラグ`IDataObjectImpl::GetData`と`CComControlBase::GetZoomInfo`からコントロールのサイズを設定する必要があります`m_sizeNatural`からではなく`m_sizeExtent`します。

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_bdrawgetdatainhimetric"></a>  CComControlBase::m_bDrawGetDataInHimetric

示すフラグ`IDataObjectImpl::GetData`描画するときに HIMETRIC ユニットと単位を使用する必要があります。

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Remarks

それぞれの論理 HIMETRIC 単位は 0.01 ミリメートルです。

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_binplaceactive"></a>  CComControlBase::m_bInPlaceActive

コントロールがアクティブであることを示すフラグです。

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Remarks

つまり、コントロールが表示されると、そのウィンドウがある場合、表示ですがメニューやツールバーをアクティブなできない可能性があります。 `m_bUIActive`フラグは、メニューなどのコントロールのユーザー インターフェイスがアクティブでもを示します。

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_binplacesiteex"></a>  CComControlBase::m_bInPlaceSiteEx

コンテナー サポートを示すフラグ、`IOleInPlaceSiteEx`インターフェイスと OCX96 およびちらつきなしのコントロールなどの機能を制御します。

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

データ メンバー`m_spInPlaceSite`を指す、[ビュー](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)、[この](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)、または[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)の値に応じて、インターフェイス、`m_bWndLess`と`m_bInPlaceSiteEx`フラグ。 (データ メンバー `m_bNegotiatedWnd` TRUE である必要がありますの`m_spInPlaceSite`を有効にするポインター)。

場合`m_bWndLess`false と`m_bInPlaceSiteEx`が true の場合、`m_spInPlaceSite`は、`IOleInPlaceSiteEx`インターフェイス ポインター。 参照してください[は、「](#m_spinplacesite)これら 3 つのデータ メンバーの関係を示すしますテーブル。

##  <a name="m_bnegotiatedwnd"></a>  CComControlBase::m_bNegotiatedWnd

(ちらつきのないとウィンドウなしコントロールなど)、OCX96 コントロールの機能のサポートのコンテナーとコントロールがネゴシエートするかどうかと、コントロールは、ウィンドウまたはウィンドウなしかどうかを示すフラグします。

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

`m_bNegotiatedWnd`フラグが TRUE にする必要がありますの`m_spInPlaceSite`を有効にするポインター。

##  <a name="m_brecomposeonresize"></a>  CComControlBase::m_bRecomposeOnResize

コンテナー コントロールの表示サイズが変更されたときに、プレゼンテーションを再構成するために、コントロールを示すフラグします。

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

このフラグをチェックして[IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent)と TRUE の場合、`SetExtent`の変更の表示のコンテナーに通知します。 このフラグが設定されている場合に、OLEMISC_RECOMPOSEONRESIZE ビット、[入ります](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc)列挙体も設定する必要があります。

##  <a name="m_brequiressave"></a>  CComControlBase::m_bRequiresSave

最後に保存された後、コントロールが変更を示すフラグします。

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Remarks

値`m_bRequiresSave`で設定できる[CComControlBase::SetDirty](#setdirty)で取得および[CComControlBase::GetDirty](#getdirty)します。

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_bresizenatural"></a>  CComControlBase::m_bResizeNatural

コントロールでは、自然なエクステント (スケーリングされていない物理サイズ) のサイズを変更することを示すフラグ、コンテナーにコントロールの表示サイズが変更されたとき。

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Remarks

このフラグをチェックして`IOleObjectImpl::SetExtent`に TRUE の場合、サイズが渡されると、`SetExtent`に割り当てられている`m_sizeNatural`します。

渡されるサイズ`SetExtent`に常に割り当てられている`m_sizeExtent`の値に関係なく、`m_bResizeNatural`します。

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_buiactive"></a>  CComControlBase::m_bUIActive

メニューやツールバーなどのコントロールのユーザー インターフェイスを示すフラグはアクティブです。

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Remarks

`m_bInPlaceActive`フラグは、コントロールがアクティブでは、それがあることを示します、ユーザー インターフェイスがアクティブです。

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_busingwindowrgn"></a>  CComControlBase::m_bUsingWindowRgn

コンテナーが指定したウィンドウ領域を使用して、コントロールを示すフラグします。

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_bwasoncewindowless"></a>  CComControlBase::m_bWasOnceWindowless

ウィンドウなし、されましたが、可能性があります、またはできない可能性がありますウィンドウなしようになりましたコントロールを示すフラグです。

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_bwindowonly"></a>  CComControlBase::m_bWindowOnly

コンテナー ウィンドウなしのコントロールをサポートしている場合でも、ウィンドウ表示するコントロールを示すフラグです。

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_bwndless"></a>  CComControlBase::m_bWndLess

コントロールがウィンドウなしを示すフラグします。

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

データ メンバー`m_spInPlaceSite`を指す、[ビュー](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)、[この](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)、または[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)の値に応じて、インターフェイス、`m_bWndLess`と[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)フラグ。 (データ メンバー[各](#m_bnegotiatedwnd)TRUE である必要がありますの[は](#m_spinplacesite)を有効にするポインター)。

場合`m_bWndLess`が true の場合、`m_spInPlaceSite`は、`IOleInPlaceSiteWindowless`インターフェイス ポインター。 参照してください[は](#m_spinplacesite)これらのデータ メンバーの完全な関係を示すテーブル。

##  <a name="m_hwndcd"></a>  CComControlBase::m_hWndCD

コントロールに関連付けられているウィンドウ ハンドルへの参照が含まれています。

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_nfreezeevents"></a>  CComControlBase::m_nFreezeEvents

回数の合計数、コンテナーは、イベント (イベントの受け入れ) の間の凍結解除せずイベント (イベントを拒否しました) をフリーズがします。

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_rcpos"></a>  CComControlBase::m_rcPos

コンテナーの座標で表された、コントロールの位置を (ピクセル単位)。

```
RECT m_rcPos;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_sizeextent"></a>  この

特定のディスプレイの HIMETRIC 単位 (各単位は 0.01 ミリメートル) 内のコントロールの範囲。

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

このサイズはスケールが表示されます。 コントロールの物理サイズで指定する、`m_sizeNatural`データ メンバーは固定されているとします。

グローバル関数でピクセルにサイズを変換する[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)します。

##  <a name="m_sizenatural"></a>  CComControlBase::m_sizeNatural

HIMETRIC 単位 (各単位は 0.01 ミリメートル) コントロールの物理サイズ。

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

サイズの中に、このサイズは固定`m_sizeExtent`表示でスケーリングします。

グローバル関数でピクセルにサイズを変換する[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)します。

##  <a name="m_spadvisesink"></a>  CComControlBase::m_spAdviseSink

コンテナーのアドバイザリ コネクションを直接ポインター (コンテナーの[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink))。

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_spambientdispatch"></a>  CComControlBase::m_spAmbientDispatch

A`CComDispatchDriver`オブジェクトを取得し、オブジェクトのプロパティを設定することができます、`IDispatch`ポインター。

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_spclientsite"></a>  CComControlBase::m_spClientSite

コンテナー内のコントロールのクライアントのサイトへのポインター。

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

##  <a name="m_spdataadviseholder"></a>  CComControlBase::m_spDataAdviseHolder

標準的なデータ オブジェクト間のアドバイザリ コネクションをアドバイズ シンクすることを意味を提供します。

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

データ オブジェクトがデータを転送して、実装するコントロール[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)メソッドを持つが、データの形式と転送メディアを指定します。

インターフェイス`m_spDataAdviseHolder`実装、 [IDataObject::DAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dadvise)と[IDataObject::DUnadvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dunadvise)メソッドを確立し、コンテナーへのアドバイザリ コネクションを削除します。 コントロールのコンテナーがサポートすることによって、アドバイズ シンクを実装する必要があります、 [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)インターフェイス。

##  <a name="m_spinplacesite"></a>  は

コンテナーへのポインター[ビュー](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)、[この](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)、または[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)インターフェイス ポインター。

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

`m_spInPlaceSite`ポインターが有効な場合にのみ、 [m_bNegotiatedWnd](#m_bnegotiatedwnd)フラグは TRUE になります。

次の表は、どのように`m_spInPlaceSite`ポインターの種類によって異なります、 [m_bWndLess](#m_bwndless)と[m_bInPlaceSiteEx](#m_binplacesiteex)データ メンバーのフラグ。

|型は、「|m_bWndLess 値|m_bInPlaceSiteEx 値|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|true|TRUE または FALSE|
|`IOleInPlaceSiteEx`|false|true|
|`IOleInPlaceSite`|false|false|

##  <a name="m_spoleadviseholder"></a>  CComControlBase::m_spOleAdviseHolder

アドバイザリ コネクションを保持するための標準的な実装を提供します。

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロール クラス内でこのデータ メンバーを使用するには、必要がありますとして宣言するデータ メンバーをコントロール クラス。 基本クラスの共用体で宣言されているために、コントロール クラスは、基本クラスからこのデータ メンバーを継承しません。

インターフェイス`m_spOleAdviseHolder`実装、 [IOleObject::Advise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-advise)と[IOleObject::Unadvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-unadvise)メソッドを確立し、コンテナーへのアドバイザリ コネクションを削除します。 コントロールのコンテナーがサポートすることによって、アドバイズ シンクを実装する必要があります、 [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)インターフェイス。

##  <a name="ondraw"></a>  CComControlBase::OnDraw

コントロールを描画するには、このメソッドをオーバーライドします。

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>パラメーター

*di*<br/>
参照、 [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)描画特性、コントロールの境界などの描画情報を含む構造体かどうかに描画を最適化するかどうかとします。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

既定の`OnDraw`を削除またはデバイス コンテキストを復元または nothing 設定されているフラグによっては[CComControlBase::OnDrawAdvanced](#ondrawadvanced)します。

`OnDraw`メソッドは、ATL コントロール ウィザードを使用して、コントロールを作成するときに、自動的に、コントロール クラスに追加します。 ウィザードの既定`OnDraw`"ATL 8.0"というラベルの付いた四角形を描画します。

### <a name="example"></a>例

例をご覧ください[CComControlBase::GetAmbientAppearance](#getambientappearance)します。

##  <a name="ondrawadvanced"></a>  CComControlBase::OnDrawAdvanced

既定の`OnDrawAdvanced`描画、正規化されたデバイス コンテキストを準備し、コントロール クラスの`OnDraw`メソッド。

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>パラメーター

*di*<br/>
参照、 [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)描画特性、コントロールの境界などの描画情報を含む構造体かどうかに描画を最適化するかどうかとします。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

標準化なしに、コンテナーによって渡されるデバイス コンテキストをそのまま使用する場合は、このメソッドをオーバーライドします。

参照してください[CComControlBase::OnDraw](#ondraw)の詳細。

##  <a name="onkillfocus"></a>  CComControlBase::OnKillFocus

コントロールは、インプレース アクティブと有効なコントロール サイトを持つそのコンテナーにコントロールがフォーカスを失ったことを通知を確認します。

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>パラメーター

*nMsg*<br/>
予約済み。

*wParam*<br/>
予約済み。

*lParam*<br/>
予約済み。

*bHandled*<br/>
ウィンドウのメッセージが正常に処理されたかどうかを示すフラグ。 既定では FALSE です。

### <a name="return-value"></a>戻り値

常に 1 を返します。

##  <a name="onmouseactivate"></a>  CComControlBase::OnMouseActivate

UI がユーザー モードでは、し、コントロールをアクティブにすることを確認します。

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>パラメーター

*nMsg*<br/>
予約済み。

*wParam*<br/>
予約済み。

*lParam*<br/>
予約済み。

*bHandled*<br/>
ウィンドウのメッセージが正常に処理されたかどうかを示すフラグ。 既定では FALSE です。

### <a name="return-value"></a>戻り値

常に 1 を返します。

##  <a name="onpaint"></a>  CComControlBase::OnPaint

描画するため、コンテナーを準備し、コントロールのクライアント領域を取得、コントロール クラスの`OnDrawAdvanced`メソッド。

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>パラメーター

*nMsg*<br/>
予約済み。

*wParam*<br/>
既存の HDC にします。

*lParam*<br/>
予約済み。

*lResult*<br/>
予約済み。

### <a name="return-value"></a>戻り値

常に 0 を返します。

### <a name="remarks"></a>Remarks

場合*wParam*が NULL でない`OnPaint`有効 HDC を格納しの代わりに使用を前提としています[CComControlBase::m_hWndCD](#m_hwndcd)します。

##  <a name="onsetfocus"></a>  CComControlBase::OnSetFocus

コントロールは、インプレース アクティブと有効なコントロール サイトを持つそのコンテナー コントロールに通知の確認がフォーカスを取得します。

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>パラメーター

*nMsg*<br/>
予約済み。

*wParam*<br/>
予約済み。

*lParam*<br/>
予約済み。

*bHandled*<br/>
ウィンドウのメッセージが正常に処理されたかどうかを示すフラグ。 既定では FALSE です。

### <a name="return-value"></a>戻り値

常に 1 を返します。

### <a name="remarks"></a>Remarks

コントロールがフォーカスを受け取りましたが、コンテナーへの通知を送信します。

##  <a name="pretranslateaccelerator"></a>  CComControlBase::PreTranslateAccelerator

独自のキーボード アクセラレータのハンドラーを提供するには、このメソッドをオーバーライドします。

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>パラメーター

*pMsg*<br/>
予約済み。

*hRet*<br/>
予約済み。

### <a name="return-value"></a>戻り値

既定では、FALSE を返します。

##  <a name="sendonclose"></a>  CComControlBase::SendOnClose

コントロールが閉じられているアドバイズ ホルダーに登録されているすべてのアドバイズ シンクに通知します。

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

コントロールがそのアドバイズ シンクを閉じている通知を送信します。

##  <a name="sendondatachange"></a>  CComControlBase::SendOnDataChange

コントロールのデータが変更されたアドバイズ ホルダーに登録されているすべてのアドバイズ シンクに通知します。

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>パラメーター

*advf*<br/>
フラグを指定することをお勧めする方法への呼び出し[IAdviseSink::OnDataChange](/windows/desktop/api/objidl/nf-objidl-iadvisesink-ondatachange)されます。 値は、 [ADVF](/windows/desktop/api/objidl/ne-objidl-tagadvf)列挙体。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="sendonrename"></a>  CComControlBase::SendOnRename

コントロールに、新しいモニカーがあること、advise 所有者に登録されているすべてのアドバイズ シンクに通知します。

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>パラメーター

*pmk*<br/>
コントロールの新しいモニカーへのポインター。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

コントロールのモニカーが変更されたことを示す通知を送信します。

##  <a name="sendonsave"></a>  CComControlBase::SendOnSave

コントロールが保存されているアドバイズ ホルダーに登録されているすべてのアドバイズ シンクに通知します。

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

コントロールがデータを保存したことの通知を送信します。

##  <a name="sendonviewchange"></a>  CComControlBase::SendOnViewChange

登録されているすべてのコントロールのビューが変更されたアドバイズ シンクに通知します。

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>パラメーター

*dwAspect*<br/>
特性またはコントロールのビュー。

*lindex*<br/>
ビューの変更の部分。 -1 だけが無効です。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

`SendOnViewChange` 呼び出し[IAdviseSink::OnViewChange](/windows/desktop/api/objidl/nf-objidl-iadvisesink-onviewchange)します。 値だけ*lindex* -1 で、関心のある全体のビューがあることを示しますが、現在サポートされています。

##  <a name="setcontrolfocus"></a>  CComControlBase::SetControlFocus

設定またはコントロールとの間にキーボード フォーカスを削除します。

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>パラメーター

*bGrab*<br/>
TRUE の場合は、呼び出し元のコントロールにキーボード フォーカスを設定します。 FALSE の場合は、キーボード フォーカスをフォーカスが呼び出し元のコントロールから削除します。

### <a name="return-value"></a>戻り値

コントロールがフォーカスを正常に受信するかどうかは TRUE を返しますそれ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

ウィンドウを持つコントロール、Windows API 関数の[SetFocus](/windows/desktop/api/winuser/nf-winuser-setfocus)が呼び出されます。 ウィンドウなしのコントロールの[IOleInPlaceSiteWindowless::SetFocus](/windows/desktop/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus)が呼び出されます。 この呼び出しでは、ウィンドウなしのコントロールがキーボード フォーカスを取得やウィンドウのメッセージに応答できます。

##  <a name="setdirty"></a>  CComControlBase::SetDirty

データ メンバーを設定`m_bRequiresSave`の値に*bDirty*します。

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>パラメーター

*bDirty*<br/>
データ メンバーの値[CComControlBase::m_bRequiresSave](#m_brequiressave)します。

### <a name="remarks"></a>Remarks

`SetDirty(TRUE)` 最後に保存してから、コントロールが変更されたことをフラグに呼び出す必要があります。 値`m_bRequiresSave`で取得[CComControlBase::GetDirty](#getdirty)します。

## <a name="see-also"></a>関連項目

[CComControl クラス](../../atl/reference/ccomcontrol-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
